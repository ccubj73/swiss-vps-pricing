# Swiss VPS: how much should you actually pay, which plan is enough, and what the plan tables hide (Evoxt tiers vs Swiss-located hosts)

Swiss-located VPS plans that can be verified price a 1–2 GB machine somewhere between €8 and about $20 a month, and almost all of that spread comes down to RAM, transfer allowance and whether backup is included. Evoxt's published ladder sits at the low end: **$2.99/month for 512 MB, $5.99/month for 2 GB**, weekly offsite backup listed on every tier, and 11 plans running up to 32 GB of RAM.

Below is the full Evoxt price table, the per-gigabyte arithmetic that shows which upgrades are worth paying for, and verified Swiss-located plans from other providers for a like-for-like check. There is also a section on three provider pages whose spec tables contradict their own headlines, because reading the row instead of the banner is what keeps you from paying for the wrong tier.

> **Quick read**
> - Small site, VPN endpoint, DNS secondary, monitoring agent: **VM-1 at $5.99/month** (1 core, 2 GB RAM, 20 GB storage, 500 GB transfer). VM-0.5 at $2.99 is a $3 saving that costs you 1.5 GB of RAM and half the transfer.
> - Need a second core without more memory: **VM-1.5 at $6.95/month**.
> - Every Evoxt plan lists weekly offsite backup at no extra cost. Several Swiss hosts sell backup as a paid add-on.
> - 👉 [Check the live plan list and deploy a Swiss VM](https://console.evoxt.com/deploy.php?aff=1168)

## Evoxt's full plan list and prices

Prices below are Evoxt's published USD list prices. The Switzerland page on Evoxt's site uses the same ladder and the same numbers as the main plan table, so there is no separate Swiss price column to budget for in the published figures.

| Plan | vCPU / RAM | Storage | Monthly transfer | Price (USD/mo) | Order |
| --- | --- | --- | --- | --- | --- |
| VM-0.5 | 1 core / 512 MB | 5 GB | 250 GB | $2.99 | [Deploy VM-0.5](https://console.evoxt.com/deploy.php?aff=1168) |
| VM-0.75 | 1 core / 1 GB | 10 GB | 250 GB | $4.99 | [Deploy VM-0.75](https://console.evoxt.com/deploy.php?aff=1168) |
| VM-1 | 1 core / 2 GB | 20 GB | 500 GB | $5.99 | [Deploy VM-1](https://console.evoxt.com/deploy.php?aff=1168) |
| VM-1.5 | 2 cores / 2 GB | 20 GB | 500 GB | $6.95 | [Deploy VM-1.5](https://console.evoxt.com/deploy.php?aff=1168) |
| VM-2 | 2 cores / 4 GB | 30 GB | 1,000 GB | $11.99 | [Deploy VM-2](https://console.evoxt.com/deploy.php?aff=1168) |
| VM-3 | 4 cores / 4 GB | 30 GB | 1,000 GB | $14.99 | [Deploy VM-3](https://console.evoxt.com/deploy.php?aff=1168) |
| VM-4 | 4 cores / 8 GB | 60 GB | 2,000 GB | $23.99 | [Deploy VM-4](https://console.evoxt.com/deploy.php?aff=1168) |
| VM-6 | 8 cores / 8 GB | 60 GB | 2,000 GB | $29.99 | [Deploy VM-6](https://console.evoxt.com/deploy.php?aff=1168) |
| VM-8 | 8 cores / 16 GB | 80 GB | 3,000 GB | $47.99 | [Deploy VM-8](https://console.evoxt.com/deploy.php?aff=1168) |
| VM-12 | 16 cores / 16 GB | 80 GB | 3,000 GB | $60.95 | [Deploy VM-12](https://console.evoxt.com/deploy.php?aff=1168) |
| VM-16 | 16 cores / 32 GB | 100 GB | 5,000 GB | $95.99 | [Deploy VM-16](https://console.evoxt.com/deploy.php?aff=1168) |

Everything in the table shares the same inclusions: weekly offsite backup, the control panel tools (monitoring, IP reassignment and floating IPs, firewall rules set from outside the VM, cloning, VNC console, sub-accounts for staff), and a CPU model Evoxt advertises at up to 6.0 GHz. Extra IPv4 addresses are $3/month each. Billing runs from monthly up to a three-year prepay, and payment covers credit and debit cards, PayPal, Bitcoin and USDt on Tron.

## The ladder is linear, so buy RAM rather than a "bigger plan"

Take the five RAM-doubling steps and divide the price by memory: VM-1, VM-2, VM-4, VM-8 and VM-16 all land on exactly **$3.00 per GB of RAM**. Storage and transfer scale alongside. There is no bulk discount for going bigger, and no penalty either, which means the tier you pick should be decided by the memory your workload actually needs, not by a vague sense that the larger plan is better value.

The two sub-1 GB tiers are the exception. VM-0.5 works out at $5.98 per GB and VM-0.75 at $4.99 per GB, so you pay a premium for going small. That is reasonable for a VPN endpoint or a monitoring agent and a poor deal for anything running a database.

Where the money genuinely changes shape is the core-doubling variants:

| Upgrade | Extra cost | What changes |
| --- | --- | --- |
| VM-1 → VM-2 | +$6.00/mo | +2 GB RAM, +10 GB storage, +500 GB transfer |
| VM-2 → VM-3 | +$3.00/mo | +2 cores only (4 GB RAM, 30 GB storage, 1 TB transfer unchanged) |
| VM-4 → VM-6 | +$6.00/mo | +4 cores only (8 GB RAM, 60 GB storage, 2 TB transfer unchanged) |
| VM-8 → VM-12 | +$12.95/mo | +8 cores only (16 GB RAM, 80 GB storage, 3 TB transfer unchanged) |

$3.00 for two extra cores (VM-2 to VM-3) is the cheapest CPU upgrade in the list, and it is the right move if you are compiling, running CI jobs or hosting a game server that is core-bound rather than memory-bound.

## Where the Swiss location actually matters

Two things change when the box sits in Switzerland: the network path to Swiss visitors, and which jurisdiction holds the disk.

OVHcloud runs Local Zones in Zurich and Geneva and says workloads stay in Switzerland, aligned with Swiss data protection rules and GDPR. The company markets those zones specifically as a way to cut response times for Swiss users compared with routing everything through Frankfurt. Exoscale states that it is a Swiss company, that its services are located and operated only from Switzerland, and that it has no US affiliate or subsidiary, which it argues keeps it outside the Patriot Act. Both are the providers' own claims, and both are the kind of claim you can only check by reading the contract terms attached to the plan you buy.

Exoscale also illustrates why metered cloud pricing needs attention. The same page describes billing as "by the minute" in the intro, "billed by the second" in the comparison table, and "per 5 minutes" in the footnote. That is three different meters on one page. The invoice line, not the marketing copy, is the thing to read.

For Evoxt specifically, the practical check is short: open the deploy screen and confirm Switzerland appears in the region list, and confirm whether that region carries a network surcharge before you enter payment details. Latency claims are easy to publish and easy to test. A ping from Zurich or Geneva to your instance after deployment settles in ten seconds what a marketing map cannot.

## Three plan tables that contradict their own headlines

Provider pages are unreliable at the banner level, and the pattern repeats across the Swiss market:

- **Colonelserver** titles its Swiss page "NVMe High Performance" and then lists SSD storage in every plan row, 40 GB at €8/month up to 250 GB at €75/month.
- **SwissNode** invites you to "choose from four levels" and then displays seven plans, with HDD storage from 20 GB to 200 GB and 100 Mbit/s of internet access per VPS.
- **SwissLayer** writes about "terabytes of NVMe SSD storage" in the body copy, while the plan cards show 30 GB and 50 GB SSD with a 5 TB monthly cap.

None of those are necessarily bad products. They are just pages where the prose was written separately from the price table, and the price table is the part that bills you.

The same discipline applies to Evoxt. The tightest number on VM-0.5 and VM-0.75 is not the 512 MB of RAM, it is the **250 GB monthly transfer**. A site with any real traffic, image-heavy pages or a video component will hit that ceiling long before it runs out of memory. Move to VM-1 for 500 GB, and to VM-2 or VM-3 for 1 TB.

## What Swiss-located plans cost elsewhere

These are verified figures from providers' own pages, listed for comparison. Nothing here is a recommendation and no links are provided.

| Provider | Location as stated | Entry configuration | Price as listed | Notes |
| --- | --- | --- | --- | --- |
| Colonelserver | Switzerland, central Europe | 1 vCPU, 1 GB RAM, 40 GB SSD | €8/mo | Unlimited transfer, 1 Gbps port, IPv4 + IPv6, unmanaged |
| SwissNode | Switzerland | 512 MB, 1 core, 20 GB HDD, 100 GB traffic | €8.80/mo | 100 Mbit/s per VPS; the 2 GB tier is €26.40/mo |
| SwissLayer | Switzerland | 2 cores, 2 GB RAM, 30 GB SSD, 5 TB | $19.95/mo | 1 IPv4 plus 100 IPv6; the 8 GB tier is $42.95/mo |
| OVHcloud | Zurich and Geneva | Plans not priced on the page reviewed | Not listed | KVM, NVMe, IPv4/IPv6, unlimited traffic, DDoS protection, backup, managed or unmanaged |
| Exoscale | Zurich (CH-ZH-1) | 2 cores, 4 GB RAM, 10 GB SSD | 24.01 CHF/mo | Metered billing, S3-compatible object storage with three copies |

Put Evoxt's VM-2 next to that table: 2 cores, 4 GB RAM, 30 GB storage and 1 TB transfer for $11.99/month, with backup included. On the listed numbers, before any currency conversion, that is less than half of SwissLayer's 2 GB plan and roughly half of Exoscale's 4 GB comparison row, with triple the disk of the latter. The differences that survive the comparison are the ones worth weighing: Colonelserver offers a 1 Gbps port with unlimited transfer, OVHcloud sells a managed option, Exoscale bills by the unit of time with no commitment, and Evoxt runs a flat monthly price with a fixed transfer allowance.

## Who should not buy the cheap tiers

VM-0.5 and VM-0.75 are honest plans for a WireGuard or Tailscale coordination node, a secondary DNS server, an uptime monitor, an IRC bouncer or a small bot. They are the wrong purchase for:

- **A WordPress site with a database and a media library.** 5–10 GB of disk fills quickly once plugins, backups and uploads accumulate. Start at VM-1.
- **Docker with more than one or two images.** A base image plus a database container plus logs will eat 10 GB before you have configured anything.
- **Anyone installing cPanel or Plesk.** The control panel licence is an added cost on most hosts, and the panel itself wants 2 GB of RAM minimum. VM-2 is the realistic floor.
- **Windows RDP.** Windows plus a browser is a 4 GB workload. VM-2 or VM-4.
- **Anyone who wants managed support.** Evoxt's plans are self-managed. Colonelserver advertises managed VPS options and OVHcloud sells a managed tier; if you need someone else to patch the box, buy that instead of a cheaper unmanaged plan plus a support ticket queue.

## What buyers actually report

Two public sources are worth reading before payment, and neither is uniformly positive.

A LowEndTalk review from June 2026 describes a VPS bought for a Tailscale coordination server where the IPv4 address showed 100% packet loss from mainland China, apparently already blocked before delivery. The refund request was denied under a policy covering GFW-blocked addresses, and the reviewer also reports that a destroyed instance was reactivated by support without consent. The takeaway is narrow but useful: if a meaningful share of your traffic originates in mainland China, test the assigned IP before you build anything on it.

Trustpilot reviews for Evoxt are mixed. One 2025 reviewer reports a smooth, fast refund after a support conversation. Others report account credits being non-refundable, a suspension triggered by bandwidth overage where a purchased add-on took two days to activate, and an affiliate complaint about withheld commissions. The operational lesson is to keep account top-ups small and to watch the transfer meter rather than prepaying a large credit balance.

👉 [Deploy a Swiss VM and check the region list before paying](https://console.evoxt.com/deploy.php?aff=1168)

## Pick by workload

- **VPN endpoint, DNS secondary, monitoring agent** → VM-0.5 at $2.99, or VM-0.75 at $4.99 if you want a full 1 GB.
- **One small site, static or lightly plugin'd WordPress** → VM-1 at $5.99. The 2 GB of RAM matters more than the core count here.
- **Several small sites, or Docker with a handful of containers** → VM-1.5 at $6.95 if CPU is the bottleneck, VM-2 at $11.99 if memory is.
- **Compiling, CI runners, game servers, application plus database on one box** → VM-3 at $14.99 for cores, VM-4 at $23.99 when you need both cores and 8 GB.
- **Multi-tenant hosting, heavy database, many containers** → VM-6 at $29.99 upward. The $3/GB RAM rate holds all the way to VM-16, so there is no cheaper-per-gigabyte reason to stop at 8 GB.

## Before you pay

Four things to confirm on the order screen, in this order: that **Switzerland appears in the region list** (the Swiss page and the main plan table share prices, but regional availability is what the console enforces); the **transfer allowance** on the tier you picked, since 250 GB is the real limit on the two cheapest plans; the **billing term**, because Evoxt allows anything from monthly to a three-year prepay and the longer terms lock up more capital with a provider whose credit policy reviewers describe as non-refundable; and the **refund terms in force at the moment of purchase**, given that at least one buyer reports being declined on grounds that were not obvious from the plan page.

Start monthly. A $5.99 VM-1 on a monthly term costs you nothing extra to leave, and one month is enough to test latency from your actual users and confirm the transfer meter behaves the way you expect.

👉 [See Evoxt's current plan prices and start with a monthly term](https://console.evoxt.com/deploy.php?aff=1168)
