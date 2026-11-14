# Traffic readiness — why vibe-coded apps fail under real traffic

**Category:** Performance, scalability and launch readiness  
**Use when:** Building a web app/API, reviewing a generated app, preparing a launch, or investigating slowdowns under load.  
**Original post:** https://www.instagram.com/p/DfHhUHxjT-I/  
**Reviewed:** 2026-11-14  
**Source evidence:** User-supplied cover and five numbered slide screenshots. The post's full caption and any additional slides were not reviewed.

## What is what?

- **Post statement / suggested fix:** Paraphrases of the supplied slides.
- **AI implementation instructions:** Our engineering guidance for turning those suggestions into appropriate project changes.
- **Verification:** Evidence needed before claiming a fix works.
- These five checks are a starting point, not a guarantee of unlimited capacity. Choose solutions for the actual stack, workload and budget.

## 01 — Unoptimised database queries

**Post statement:** Queries that feel fine on tiny test datasets may become slow as real data grows.

**Post's suggested fix:** Add indexes to columns used in filters and searches.

**AI implementation instructions:**
- Inspect frequently executed and slow queries, schema, existing indexes and representative data volumes.
- Use query plans (for example EXPLAIN) to identify expensive scans, joins and sorts.
- Choose indexes based on actual query patterns, selectivity and column order. Consider composite indexes where appropriate.
- Fix N+1 queries, unnecessary columns and unbounded result sets; use suitable pagination.
- Do not blindly index every searchable column: indexes consume storage and add write overhead. Document migrations and rollback.

**Verification:** Compare query plans and timings before/after on representative data. Check write performance and result correctness. Do not promise a particular speedup merely because an index was added.

**Ask the AI:**
> Audit my database queries for realistic data volumes. Identify the slowest paths and N+1 queries, propose justified indexes and pagination, implement appropriate fixes, and show before/after evidence.

## 02 — No caching

**Post statement:** Repeated requests may fetch unchanged data from the database again and again.

**Post's suggested fix:** Cache infrequently changing data; Upstash Redis is mentioned as an option.

**AI implementation instructions:**
- Identify repeated reads and the freshness each response requires.
- Choose the simplest suitable layer: browser/CDN, application cache or a shared cache such as Redis.
- Define cache keys, expiry, invalidation after writes, memory bounds and fallback behaviour.
- Isolate user/tenant-specific data and permissions in cache keys; do not put private responses in public shared caches.
- Avoid many concurrent cache misses triggering identical expensive work. Account for multiple application instances.

**Verification:** Check warm/cold behaviour, cache hit rate, database request reduction, updates/invalidation, cross-user isolation and cache outage behaviour.

**Ask the AI:**
> Identify safe caching opportunities, choose an appropriate cache layer, define expiry and invalidation, implement it, and test freshness, user isolation and failure behaviour.

## 03 — Images not optimised

**Post statement:** Serving full-size images can make pages slow, especially on mobile connections.

**Post's suggested fix:** Use Vercel image optimisation or Cloudflare to deliver smaller images.

**AI implementation instructions:**
- Audit image dimensions, transfer sizes and usage; serve sizes appropriate to the rendered viewport.
- Use responsive variants and suitable compressed formats, with fallbacks where needed.
- Prefer the existing framework's image pipeline or a suitable CDN; a vendor subscription is not mandatory.
- Reserve layout space, lazy-load offscreen images and avoid delaying the key above-the-fold image.
- Configure caching and safe source restrictions for remote image optimisation.

**Verification:** Inspect actual network payloads and selected image variants at mobile/desktop sizes. Check visual quality, layout shifts and loading under a slower connection.

**Ask the AI:**
> Audit image delivery, implement responsive sizing and compression using our stack, and verify transfer sizes, mobile loading and visual quality.

## 04 — No load testing before launch

**Post statement:** A single-user laptop test does not establish that the app can handle concurrent traffic.

**Post's suggested fix:** Use k6 or Artillery to simulate multiple users before launch.

**AI implementation instructions:**
- Define representative journeys, dataset size, request mix, arrival rate/concurrency and test duration.
- Establish measurable latency and error-rate targets before testing. State assumptions if traffic forecasts are unavailable.
- Start small, ramp to expected load, and include spikes or sustained runs where useful.
- Exercise reads, writes and authenticated flows, rather than only the homepage.
- Use an owned/authorised test environment with synthetic data; isolate real payments, email and other side effects.
- Observe application errors, database connections, CPU, memory and dependency saturation.

**Verification:** Save the test script, environment, workload, latency percentiles, throughput, errors and resource measurements. Distinguish expected rate-limit responses from unexpected failures. Fix bottlenecks and rerun the affected scenario. Passing establishes only the capacity tested.

**Ask the AI:**
> Create a realistic k6 or Artillery test for our key journeys, define pass/fail targets, run it in our test environment where available, and report bottlenecks with measured results.

## 05 — No rate limiting

**Post statement:** Unrestricted requests can overwhelm endpoints during bursts or abusive use.

**Post's suggested fix:** Add per-IP request limits to public endpoints; Upstash is mentioned as an implementation option.

**AI implementation instructions:**
- Inventory public routes and set policies by endpoint cost and sensitivity; prioritise authentication, search, uploads and expensive operations.
- Choose appropriate keys: authenticated user/API key, tenant and/or trusted client IP. Account for shared networks and proxy configuration.
- Enforce limits server-side or at a trusted gateway. Use shared/atomic counters for distributed deployments.
- Define burst allowance, sustained limits and behaviour if the limiter is unavailable.
- Return HTTP 429 for exceeded limits with useful retry guidance (such as Retry-After).
- Rate limiting complements authentication and capacity controls; it does not replace them.

**Verification:** Test below/above limits, concurrent requests across instances, reset/retry behaviour, identity isolation and limiter failure. Confirm valid users can still complete their journeys.

**Ask the AI:**
> Review public endpoints and implement appropriate server-side rate limits using our deployment architecture. Explain identity keys and thresholds, and test enforcement, retries and legitimate-user behaviour.

## Apply automatically — master instruction

> Review this project against all five traffic-readiness checks. Inspect the stack and existing protections first. For each check, state applicable, already covered or not applicable, with evidence. Propose the smallest suitable solution, implement authorised changes, and verify them on representative data and workloads. Reuse existing infrastructure where sensible. Report changed files, measurements, tradeoffs and remaining gaps. If execution is unavailable, provide runnable checks and clearly label them untested. Never claim production capacity from code inspection alone.

For a static site without a database or API, mark database/cache/API checks not applicable where justified. Do not add services solely to tick a box.

## Tool references

| Tool/reference | Purpose |
| --- | --- |
| [MySQL index guidance](https://dev.mysql.com/doc/refman/8.4/en/optimization-indexes.html) | Query-driven index decisions and tradeoffs |
| [Upstash Redis](https://upstash.com/docs/redis/overall/getstarted) | Optional managed Redis caching |
| [Next.js Image](https://nextjs.org/docs/app/api-reference/components/image) | Framework image optimisation |
| [Vercel image optimisation](https://vercel.com/docs/image-optimization) | Provider mentioned in the post |
| [Cloudflare Images](https://developers.cloudflare.com/images/) | Image delivery and transformations |
| [k6 thresholds](https://grafana.com/docs/k6/latest/using-k6/thresholds/) | Measurable test pass/fail criteria |
| [Artillery documentation](https://www.artillery.io/docs) | Load-test scenarios and tooling |
| [Upstash rate limiting](https://upstash.com/docs/redis/sdks/ratelimit-ts/overview) | Optional distributed rate limiter |
| [HTTP 429](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Status/429) | Standard response for exceeded limits |

The post includes free-tier and quick-setup claims. Treat pricing, limits and setup time as variable; check current provider documentation before choosing a service. Do not treat “index every column” or one universal IP limit as a mandatory implementation rule.
