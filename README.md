# lightlayer: What It Is, What the RTX 4090 Servers Cost, and Why GitHub Keeps Showing Up (Plan Tables and an Ordering Checklist)

Lightlayer (lightlayer.net) is a cloud hosting provider whose GPU line runs entirely on the NVIDIA RTX 4090. Its GPU pricing page lists three ready-made server configurations, the cheapest at **$1,109.99 per server** with eight cards inside; existing customers manage everything through **account.lightlayer.net**, a portal that shows nothing but “Registered Clients Only” until you sign in.

Three things trip people up when they search this name. The client portal is not a price list, so there is nothing to compare there. Lightlayer's public pages cover GPU and dedicated servers but publish no small cloud-host price list, so the $25-a-year VPS offers people remember aren't visible to check. And at least three unrelated software projects also call themselves lightlayer, which is why search results mix GPU hosting with an AI code-review tool and a jQuery popup plugin. The last section sorts those out so you don't buy the wrong thing.

> **Quick answer for buyers:** every GPU configuration on Lightlayer's official page carries eight RTX 4090 cards, so the real choice is which CPU, memory and network package you wrap around those eight cards. The $1,109.99 EPYC 75F3 build is the cheapest entry into that class; the other two cost more for CPU, RAM and ports, not for more GPU. If you need a single card for inference or rendering, ask sales directly instead of assuming a smaller slice exists.
>
> 👉 [See the current RTX 4090 server configurations and prices](https://lightlayer.net/pricing-pm?affid=74)

## The full plan list

Lightlayer splits its public pricing across two pages: one for GPU servers, one for standard dedicated servers. Both are reproduced in full below, with the specs exactly as the pages state them.

### RTX 4090 GPU servers

| Configuration | GPU | Memory / Storage | Network card | Price | Order |
| --- | --- | --- | --- | --- | --- |
| AMD EPYC 7542 ×2 | 8× RTX 4090 | 1,024 GB / 480 GB SATA SSD ×2 + 3.84 TB U.2 ×1 | 25G optical ×2 | $3,796.99 | [Order the 7542 build](https://lightlayer.net/pricing-pm?affid=74) |
| Intel Xeon P8136 ×2 | 8× RTX 4090 | 512 GB / 7.68 TB U.2 ×2 + 960 GB U.2 ×2 | 10G ×1 + 200G ×1 | $2,920.99 | [Order the P8136 build](https://lightlayer.net/pricing-pm?affid=74) |
| AMD EPYC 75F3 ×2 | 8× RTX 4090 | 512 GB / 1.92 TB M.2 ×1 + 7.68 TB U.2 ×2 | 10G ×2 + 40G/100G ×2 | $1,109.99 | [Order the 75F3 build](https://lightlayer.net/pricing-pm?affid=74) |

Lightlayer's own one-line descriptions map the builds to workloads: the $3,796.99 machine for “large-scale data processing and deep learning model training”, the Intel build for “large-scale database processing and online transaction processing”, and the $1,109.99 EPYC for “scientific computing and data analysis”. Those labels are marketing copy rather than benchmark results, but they do tell you the vendor's intended positioning.

### Standard dedicated servers (no GPU)

| Configuration | Cores / RAM | Storage | Network | Price | Order |
| --- | --- | --- | --- | --- | --- |
| AMD EPYC 7742 ×2 | 64 cores / 256 GB | 2×240 GB SSD + 2×4 TB NVMe | Standard, 10 Gbps port, unlimited data | $9,230/month | [Order the 7742 build](https://lightlayer.net/pricing-cs?affid=74) |
| Intel E5-2696V4 dual | 44 cores / 128 GB | 2 TB SSD | Standard, 10 Gbps port, unlimited data | $8,630/month | [Order the E5-2696V4 build](https://lightlayer.net/pricing-cs?affid=74) |
| AMD EPYC 7502 ×2 | 64 cores / 256 GB | 2×240 GB SSD + 2×4 TB NVMe | Premium, 100 Mbps port, unlimited data | $900/month | [Order the 7502 build](https://lightlayer.net/pricing-cs?affid=74) |
| Intel E5-2660 dual | 16 cores / 64 GB | 1 TB SSD | Premium, 50 Mbps port, unlimited data | $150/month | [Order the E5-2660 build](https://lightlayer.net/pricing-cs?affid=74) |

Every plan on this page includes 5 IPs, unlimited data and an upgrade path. Two details on the page are worth flagging before you treat any figure as final.

The first is the header banner, which advertises “Low price to $1/mo” and “No credit card required” while the cheapest actual plan listed is $150/month. The banner is site-wide marketing, not a plan price. The second is billing language: the standard server page says “per month” plainly, but each GPU price carries the line “Billed per agent”, which reads like a machine translation of per-machine billing and does not state a cycle. Get the billing unit and renewal price in writing before paying for an eight-card box.

👉 [Confirm GPU billing terms and the current configuration list](https://lightlayer.net/pricing-pm?affid=74)

## What Lightlayer actually sells

Three product families show up across the company's own pages.

**GPU servers.** The company announced RTX 4090 GPU servers as an expansion of its computing lineup, and the GPU pricing page is now the place where those machines are configured and priced. All three listed builds use eight cards.

**Dedicated servers.** The second pricing page covers conventional single-tenant machines from $150/month up to $9,230/month, with the main spread coming from port speed and network tier rather than core count.

**Cloud hosts (VPS).** A company news post from 2024 documents small annual-billed cloud hosts in Los Angeles, Taiwan and Manila, starting from $24.99/year for 1 core, 1 GB RAM and 50 GB storage. That promotion ended on August 31 of that year and the price should not be treated as current, but the post does explain something still relevant: Los Angeles offers three network tiers, Premium (CN2 plus mainland China BGP plus international BGP, aimed at the lowest latency from mainland China), Standard (mainland BGP plus international BGP) and Global (international BGP only). It also says Lightlayer sells both metered and unmetered bandwidth, which is a billing distinction worth asking about on any plan.

The account subdomain is the customer-facing side of all this. It runs the billing and service management system behind the “Light Cloud easy computing” branding, which is why it has no price list or product comparison on it.

## Where the money actually goes on the dedicated page

Port speed is the single biggest price driver, and it runs in the opposite direction from what most people expect. The $150/month Intel E5-2660 comes with a 50 Mbps Premium port. The $900/month EPYC 7502 gives you 100 Mbps on the same Premium network. The $8,630 and $9,230 machines jump to 10 Gbps ports on the Standard network, which suggests they are built for throughput-heavy workloads rather than low-latency access from mainland China.

So if your workload is a busy database that mostly serves users in Asia, the $900 plan's Premium network may serve you better than a faster port on the Standard tier. If you are pushing large volumes of data between regions, the 10 Gbps machines are the ones built for it, and the $8,630 Intel box buys 44 cores against 64 on the AMD at $9,230.

On the GPU side, the three builds share the same eight-card layout, so the $1,109.99 to $3,796.99 range is buying CPU cores, memory (512 GB versus 1,024 GB) and network cards (dual 10G up to dual 25G optical). None of it buys more GPU compute. If the eight cards are the point, the entry build is the rational default.

For anyone who only needs one card, there is a data point worth knowing but not trusting. A third-party server stock tracker lists a “VGPU-1*RTX4090” plan from Lightlayer at about **$365/month** with 16 vCPU, 32 GB RAM, 250 GB SSD, monthly billing and “multiple locations”, last checked in November 2026. That configuration does not appear on Lightlayer's official pricing pages, so treat the figure as an unconfirmed pointer and verify it with sales rather than budgeting around it.

## Why searching “lightlayer” pulls up GitHub, npm and Adobe docs

This is the part that costs people real time, because two of these lookalikes are developer tools that could plausibly belong to a hosting company.

| What you see in results | What it actually is | How to tell it apart |
| --- | --- | --- |
| lightlayer-dev/lightlayer on GitHub | An AI code review tool for GitHub pull requests. TypeScript, MIT licence, 6 stars. Splits large PRs into AI-generated sub-PRs; the CLI command is `lightlayer split -n 3`. Needs Docker, a GitHub App and an Anthropic API key. | It reviews pull requests. No servers, no GPU, no hosting. |
| lightlayer on npm (version 2.3.0) | A jQuery lightbox and dialog plugin by Martin Metodiev, MIT licensed, copyright 2017. Options include background colour, opacity and popup position. | It depends on jQuery and runs in a browser. |
| `LightLayer` in Adobe's After Effects UXP API | A layer object class in Adobe's scripting documentation, available from version 27.0, with methods like `duplicate`, `addGuide` and `applyPreset`. | It is an API reference page, not a product. |

The GitHub project and the npm package are entirely separate from the hosting business, and neither has any connection to `lightlayer.net`. The GitHub organisation behind the code-review tool also publishes agent-gateway and API-middleware projects under the same name, and its product site describes itself as being built by engineers from Nvidia and Meta. That claim belongs to that team, not to the hosting provider, and repeating it in a hosting context would be a straightforward error.

## What the public pages don't tell you

Five things decide whether an order works out, and none of them is answered on the pricing pages.

1. **GPU location.** The 2024 news post names Los Angeles, Taiwan and Manila for cloud hosts. The GPU page does not state where the eight-card machines sit. Ask before you plan latency-sensitive work.
2. **Billing cycle and renewal price.** The GPU page's “Billed per agent” line does not specify monthly or annual, and no renewal pricing is published. The 2024 promotion promised renewal at the same price, which is not a general policy statement.
3. **Refunds, trials and SLA.** No refund window, trial period or uptime commitment appears on either pricing page. Assume none exists until sales confirms otherwise in writing.
4. **Verification and payment methods.** Whether you need a company registration, and whether cards, PayPal or anything else is accepted, is not published.
5. **Scaling past one machine.** Multi-server deployments, private networking between GPU boxes and bandwidth overage charges are all undiscussed on the public pages, which matters if you plan to run training across more than eight cards.

👉 [Start from the Lightlayer account portal to check plan availability](https://account.lightlayer.net/?affid=74)

## FAQ

**Does Lightlayer offer a free trial or a refund period?**
No trial, refund window or money-back guarantee is stated on the GPU or dedicated-server pricing pages. If a trial matters to your decision, ask before paying rather than after.

**Can I order a single RTX 4090?**
Not from the official GPU page, which lists only eight-card configurations. A third-party tracker shows a single-card virtual GPU plan at roughly $365/month, but it is not on Lightlayer's own pages, so confirm it exists before you plan around it.

**Is Lightlayer the AI code review tool I saw on GitHub?**
No. The GitHub project is an unrelated open-source tool for splitting and reviewing pull requests. The hosting provider's site is lightlayer.net.

**Why does account.lightlayer.net show only “Registered Clients Only”?**
Because it is the client area for existing customers, not a marketing page. New orders and plan details sit on the main site's pricing pages.

**Which network tier should I pick?**
Premium is built for low latency from mainland China (CN2 plus mainland and international BGP), Standard keeps mainland BGP with more international capacity, and Global is international BGP only. That breakdown comes from Lightlayer's own 2024 announcement about its Los Angeles facility, and it still describes how the tiers are positioned.

## Picking a build

If the job is inference, rendering or a single research project that fits in eight cards, the **$1,109.99 EPYC 75F3** configuration is the sensible starting point. It has the same GPU count as the $3,796.99 machine, and the extra $2,687 buys memory and network capacity that a single-node workload will rarely saturate.

If you are feeding the GPUs from fast storage or moving large datasets between machines, the storage and network differences start to matter, and the **$2,920.99 Intel P8136** build's 200G port and 7.68 TB U.2 drives are the reason to look past the entry plan.

If GPUs aren't the point at all and you need a plain dedicated box, the decision comes down to one question: low latency from Asia (Premium network, $150 or $900 depending on how much CPU and port speed you need) or raw throughput (Standard network, 10 Gbps, $8,630 and up).

Whatever you pick, get two things confirmed in writing first: the billing cycle behind that “Billed per agent” line, and whether a refund or trial applies. Neither is on the page, and both change what the server actually costs you.

👉 [Open the Lightlayer portal and price the configuration you need](https://account.lightlayer.net/?affid=74)
