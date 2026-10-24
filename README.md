# zenrows pricing: every plan and credit cost explained, plus the alternative worth opening in a second tab

ZenRows' current plans start at $0 (5,000 credits a month, no card) and run $16/mo for Build, $58/mo for Launch, $166/mo for Growth, and $458/mo for Scale, with Enterprise priced on request. Those headline numbers look simple, but what a plan actually costs you depends on the credit weights: 1 credit for a plain page, 5 with JavaScript rendering, 10 with premium proxies, and 25 for protected sites — so 250,000 Launch credits is either 250,000 plain pages or just 10,000 protected ones.

That gap between the sticker price and the real cost is where most pricing write-ups stop. This one doesn't. Below you'll find the full current plan list, the credit math most articles skip (response size caps, rollover rules, how overages actually get billed), and — since nobody shops a scraping API in a vacuum — a side-by-side with ScraperAPI, whose pricing works differently in a few ways that matter depending on what you're scraping.

> **Quick take:** If your workload is mostly standard pages and you want predictable overage handling, ScraperAPI's Scaling plan at $475/mo (5,000,000 credits, pay-as-you-go overage, 10% off with annual billing) is the safer bet — 👉 [check ScraperAPI's current plans and the 7-day trial](https://www.scraperapi.com/?fp_ref=coupons). If you're JS-rendering-heavy and stay under your quota, ZenRows' 5-credit rendering is the better rate. Both have free entry points, so there's no reason to decide blind.

## ZenRows pricing right now

ZenRows sells five self-serve tiers plus a custom Enterprise plan, all billed monthly in USD. These are the prices currently shown on its pricing page (verify against the live page before subscribing — its developer docs were still listing higher tier prices as of September, which suggests a recent revision):

| Plan | Monthly price | Credits/mo | Concurrent requests | Support |
| --- | --- | --- | --- | --- |
| Free | $0 | 5,000 | 5 | Community |
| Build | $16 | 45,000 | 20 | Email |
| Launch | $58 | 250,000 | 50 | Chat |
| Growth | $166 | 1,200,000 | 100 | Priority |
| Scale | $458 | 5,000,000 | 200–400 | Priority |
| Enterprise | Custom | Unlimited | 500–1,000+ | Dedicated manager + SLA |

Every plan unlocks the full feature set — Fetch, Extract, Crawl, Batch, and Browser Sessions, across API, SDK, CLI, and MCP — with the single exception that the Free plan can't use standalone Residential Proxies. The tiers differ only in credit volume, concurrency, and support level. Enterprise adds an SLA, SOC 2, ISO 27001, and a DPA, which matters if you're procurement at a company that cares about those checkboxes.

One wrinkle worth knowing: ZenRows' own developer documentation (from September) still lists a finer ladder inside each tier — Build starting at $19, Launch at $69, Growth at $199, Scale at $549, with multiple rungs per tier. The public pricing page has since moved to the lower single prices shown above, so treat the pricing page as the source of truth and don't be surprised if older articles quote the higher numbers.

## What a credit actually buys — and where the hidden limits live

The credit weights are fixed and identical on every plan: a standard page costs 1 credit, JavaScript rendering costs 5, premium proxies cost 10, and JavaScript plus premium proxies (the "protected site" tier) costs 25. There's no per-plan stealth pool or surcharge menu; when you move up a tier, you're only buying more credits.

Three things rarely make it into the comparison tables but will affect your bill:

**Failed requests are free; 404 and 410 are not failures.** ZenRows only charges for successful requests, and it treats a 404 or 410 as a real answer, so those get billed like any other result. If your scraper hammers dead URLs expecting not to pay, this is the line item to watch.

**Response size is capped per plan.** Free and Build responses max out at 5 MB, Launch and Growth at 10 MB, Scale at 20 MB (decimal MB, so 1 MB = 1,000,000 bytes). An oversized response comes back as HTTP 413 and isn't delivered — you're not charged for it, but your job doesn't finish either. If you're scraping page types with fat HTML bodies, check this before committing to a lower tier.

**Standalone residential proxies and browser sessions bill differently.** Residential bandwidth draws 25,000 credits per GB, and Browser Sessions cost 5 credits per minute on top of bandwidth. At those rates, your entire Launch allowance converts to about 10 GB of residential traffic — fine if that's the plan, surprising if you thought credits meant pages.

And the rollover rules: unused plan credits expire at each renewal, full stop. Top-up packs are the pressure valve — for example, the Launch tier's pack is 70,000 credits for $19.50, and unused top-up credits roll into the next billing period once, then expire. The pack pricing is deliberately sized so one pack covers a shortfall but two packs approach the cost of the next tier up; at that point upgrading is the better deal. The Free plan has no top-ups at all — when its 5,000 credits run dry, you wait for the monthly refresh or upgrade.

What ZenRows doesn't have at all is pay-as-you-go overage. When your credits hit zero, you either buy a top-up pack or upgrade; there's no metered continuation at a fixed per-credit rate. That's a real difference from ScraperAPI, which we'll get to in a second.

The free tier deserves a mention because it's unusually usable: 5,000 credits every month, forever, every feature unlocked, no card required. At 1 credit per plain page, that's 5,000 pages a month for nothing — enough to properly prototype before you spend anything.

## ScraperAPI: the alternative with different overage math

ScraperAPI prices on the same credit model but with a different ladder and, crucially, different overage handling. Its current self-serve plans:

| Plan | Monthly | Annual (per mo) | Credits/mo | Threads | Get it |
| --- | --- | --- | --- | --- | --- |
| Hobby | $49 | $44.10 | 100,000 | 20 | [Start with Hobby](https://www.scraperapi.com/?fp_ref=coupons) |
| Startup | $149 | $134.10 | 1,000,000 | 50 | [See Startup plan details](https://www.scraperapi.com/?fp_ref=coupons) |
| Business | $299 | $269.10 | 3,000,000 | 100 | [Compare Business vs. Scaling](https://www.scraperapi.com/?fp_ref=coupons) |
| Scaling | $475 | $427.50 | 5,000,000 | 200 | [Check the Scaling plan](https://www.scraperapi.com/?fp_ref=coupons) |
| Professional | $975 | $877.50 | 10,500,000 | 300 | [View Professional pricing](https://www.scraperapi.com/?fp_ref=coupons) |
| Advanced | $1,975 | $1,777.50 | 21,500,000 | 500 | [View Advanced pricing](https://www.scraperapi.com/?fp_ref=coupons) |
| Enterprise | Custom | Custom | 22,000,000+ | 500+ | Custom quote |

Annual billing takes 10% off every paid plan. On Hobby that's $58.80 saved over a year ($44.10 vs. $49 per month); on Startup it's $178.80; on Scaling, $570. There's also a free plan (1,000 credits, 5 concurrent connections, shown in the FAQ rather than the plan grid) and a 7-day trial that ships 5,000 credits with no credit card — so testing costs nothing either way.

Where ScraperAPI diverges from ZenRows:

**Its credit weights are heavier on some operations.** JavaScript rendering or premium proxies cost 10 credits (vs. ZenRows' 5 and 10), premium-plus-render costs 25, and ultra-premium-plus-render costs 75 — the single most expensive request type on either platform. But it also has fixed pricing for hard targets: Amazon, Walmart, and eBay cost 5 credits, Google/Bing SERPs 25, LinkedIn 30, and sites behind Cloudflare, Datadome, or PerimeterX add 10 credits when the bypass kicks in. You can check any URL's exact cost with the Domain Cost Estimator in the dashboard and cap a single request with `max_cost`. If your workload is Google SERP-heavy, run both calculators before assuming either one is cheaper — the fixed domain rates can flip the comparison.

**Overage doesn't force an upgrade above Scaling.** On ScraperAPI, Hobby through Business pause or auto-upgrade when credits run out. Scaling, Professional, Advanced, and Enterprise can switch on pay-as-you-go and keep scraping at a fixed per-credit rate up to a monthly spending cap you set. ZenRows simply has no equivalent — its answer to running dry is a top-up pack. If your monthly volume swings unpredictably, PAYG is the mechanism that keeps a spike from turning into a plan upgrade you'll regret.

Two smaller details: requests that exceed your plan's concurrency limit come back as a 429 response and cost nothing (they're rejected, not queued), so throttling mistakes don't burn credits. And geography is tiered — Hobby and Startup only get US and EU targeting with 30 days of analytics history, while Business and above unlock country-level targeting and unlimited analytics.

## Side by side at common volumes

Here's the honest comparison for standard (plain) pages, which is the cheapest case for both:

| Monthly volume | ZenRows cheapest route | ScraperAPI cheapest route |
| --- | --- | --- |
| 10,000 pages | Build, $16/mo | Hobby, $49/mo |
| 100,000 pages | Launch, $58/mo (250K credits) | Hobby, $49/mo (100K credits, just fits) |
| 250,000 pages | Launch, $58/mo | Startup, $149/mo |
| 1,000,000 pages | Growth, $166/mo (1.2M credits) | Startup, $149/mo (1M credits) |

Read that table the right way. ZenRows wins comfortably at low and mid volumes — $16 for up to 45,000 plain pages is a very low floor, and nothing in ScraperAPI's ladder comes close below the 100K mark. At 1M standard pages the prices look close ($166 vs. $149), but remember ZenRows' Growth plan includes 200,000 extra credits, so the effective per-page gap narrows further than the sticker suggests. ScraperAPI's real edge at scale sits elsewhere: its per-credit price drops faster through the upper tiers, and PAYG smooths out the spikes.

The picture shifts for JavaScript-heavy work: ZenRows charges 5 credits per rendered page against ScraperAPI's 10, so a rendering-dominated workload roughly halves ZenRows' effective price relative to the table above. If 80% of your requests carry `render=true`, do that math before anything else — it can outweigh every other difference on this page.

## Which one fits your workload

- **Under ~40,000 plain pages a month, mostly static content:** ZenRows Build at $16. At this volume ScraperAPI's cheapest entry is triple the price.
- **Prototype or hobby project:** ZenRows Free (5,000 credits/mo, no card) or ScraperAPI's 7-day trial with 5,000 credits plus the permanent 1,000-credit free plan. Use both free tiers, actually — they cover different feature sets, and neither costs a cent.
- **Rendering-heavy pipelines:** ZenRows, on credit weights alone (5 vs. 10 per rendered page).
- **Google SERP or e-commerce data at volume:** run the numbers both ways. ScraperAPI prices Amazon at 5 credits and SERPs at 25 flat; ZenRows bills those under its protected tier at 25 per page. It also acquired Traject Data in April, folding dedicated SERP and e-commerce APIs (the Rainforest API and SerpWow lines) into the same credit system — worth a look if structured marketplace data is the actual goal.
- **Unpredictable volume above 5M credits:** ScraperAPI Scaling or higher, because pay-as-you-go exists there and doesn't anywhere on ZenRows.
- **Enterprise with SLA and compliance requirements:** both offer custom plans with SLAs and security certifications; you'll be talking to sales either way.

## FAQ

**Does ZenRows have annual billing or a yearly discount?** Its pricing page currently shows monthly prices only, with no annual option displayed. ScraperAPI, by contrast, publishes an explicit 10% annual discount on every paid plan. If annual invoicing matters to your budgeting, that asymmetry is a decision factor in itself.

**Is there a refund window on ZenRows?** Third-party roundups describe a 14-day withdrawal right for consumers, with refunds limited when usage exceeds roughly 15% of the subscription. That's not something the pricing page itself advertises, so confirm the terms in checkout before relying on it. ScraperAPI's cost-free entry points (7-day trial, free plan) are the more straightforward way to evaluate it without payment risk.

**What happens when I hit my credit limit on ZenRows?** Your plan credits expire monthly with no rollover, and there's no metered overage — you buy a top-up pack (unused top-up credits roll over one period, then expire) or upgrade. On Free there are no top-ups at all; you wait for the monthly refresh or upgrade.

**Can I cap what a single request costs?** On ScraperAPI, yes — the dashboard's Domain Cost Estimator shows any URL's credit cost, and `max_cost` caps each request. On ZenRows, `max_pages` caps how many pages a Crawl opens, which serves the same budget-control purpose for crawls.

## Before you subscribe

Two checks that take five minutes and prevent the most common regrets. First, pull your last month of scraping logs and count how many requests actually need rendering or premium proxies — that ratio, more than any review, tells you which credit ladder is cheaper for you specifically. Second, size your burst months: if one week a month runs 3x your average, ZenRows' top-up-plus-upgrade model will sting more than ScraperAPI's PAYG.

Concretely: under 45K plain pages with steady volume, ZenRows Build at $16 is hard to beat. Between 250K and 1M standard pages, or anything with spiky demand, ScraperAPI's Startup and Scaling plans with the 10% annual discount come out ahead on both price and overage mechanics — 👉 [compare ScraperAPI's full plan ladder and start the 7-day trial with 5,000 free credits](https://www.scraperapi.com/?fp_ref=coupons), then use the 1,000-credit free plan as a no-card fallback if you want to test longer before paying.
