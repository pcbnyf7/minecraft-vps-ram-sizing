# Minecraft VPS Hosting: How Much RAM You Need, Why "$7/Month" Rarely Is, and Which Plan Fits Your Player Count (Full Plan Table + Setup Steps)

A vanilla Minecraft server for a handful of friends runs fine on 2 GB of RAM. Add a modpack and 4 GB becomes the practical floor, with 8 GB once a heavy pack or a long player list is in play. Minecraft also leans hard on a single CPU thread, so clock speed buys you more smooth ticks than a pile of idle cores.

The other thing worth knowing before you compare prices: most "$7/month" Minecraft VPS offers are either a 24-month prepayment or a discounted first term. RackNerd sells its KVM plans on 12-month terms instead, and the cheapest one works out to **$21.99 for a full year**. Below are the sizing rules, the complete plan table with per-year prices, the first-term-versus-renewal math that listing pages tend to skip, and the setup steps plus the three places people get stuck.

> **Quick pick:** For a vanilla world with up to about eight friends, the **2 GB KVM plan at $35.99/year** (roughly $3.00/month) is the sensible buy. Running Paper with plugins or a light modpack, or expecting 10–20 players? Take the **4 GB plan at $59.99/year**. Both are one payment covering 12 months, with full root access and a 1 Gbps port.
> 👉 [Check the 2 GB plan's current annual price](https://bit.ly/RacKnerd)

## RackNerd's full KVM lineup, priced per year

Every plan below is KVM virtualization on SSD storage, with full root access and one IPv4 address. There's no per-player or per-slot charge, so the bill stays the same whether four people log in or forty.

| Plan | vCPU | RAM | SSD storage | Price (12-month term) | Order |
| --- | --- | --- | --- | --- | --- |
| 1 GB KVM | 1 vCore | 1 GB | 20 GB | **$21.99/year** (~$1.83/mo) | [Order the 1 GB plan](https://bit.ly/RacKnerd) |
| 2 GB KVM | 2 vCore | 2 GB | 35 GB | **$35.99/year** (~$3.00/mo) | [Order the 2 GB plan](https://bit.ly/RacKnerd) |
| 4 GB KVM | 2 vCore | 4 GB | 60 GB | **$59.99/year** (~$5.00/mo) | [Order the 4 GB plan](https://bit.ly/RacKnerd) |
| 6 GB KVM | 6 vCore | 6 GB | 100 GB | **$89.99/year** (~$7.50/mo) | [Order the 6 GB plan](https://bit.ly/RacKnerd) |
| 8 GB KVM | 7 vCore | 8 GB | 150 GB | **$119.99/year** (~$10.00/mo) | [Order the 8 GB plan](https://bit.ly/RacKnerd) |

The monthly figures in brackets are just the annual price divided by twelve. You are not billed monthly; the full amount is charged once per year.

There are also Windows tiers (2.5 GB at $69/year, 4 GB at $115/year, 12 GB at $289/year). They cost more because of the licence, and a Java server on Linux is the cheaper route for Minecraft either way.

| Plan | Monthly transfer | Where it fits |
| --- | --- | --- |
| 1 GB | 3 TB | 1–3 friends, vanilla, short render distance |
| 2 GB | 5 TB | Up to ~8 players vanilla, or a few plugins |
| 4 GB | 7 TB | Paper plus plugins, 10–20 players, light modpacks |
| 6 GB | 12 TB | Heavy modpacks (FTB, ATM, Create) with a group |
| 8 GB | 20 TB | Public server, or a BungeeCord/Velocity network split across boxes |

What you get on top of the specs: a 1 Gbps port, choice of Debian, Ubuntu, Rocky Linux, AlmaLinux, CentOS or Fedora at install time (a custom ISO is available through a support ticket), and the ctrl control panel for reboots, OS reinstalls, an HTML5 VNC console, root password resets, an inbound firewall, and plan upgrades. These are unmanaged servers, so nobody is going to configure your `server.properties` for you. The one-click app list leans toward self-hosting and AI workloads (Docker with Portainer, Ollama, n8n, Coolify, WordPress stacks), so plan on installing Java over SSH rather than expecting a Minecraft image.

## How much server does a Minecraft world actually need?

Pick RAM by mods and player count, then ignore the vCPU count. The vCPU column matters far less than people assume, and Cloudzy's own documentation says it plainly: Minecraft is single-thread heavy, so single-thread performance matters more than core count. A 3.5 GHz core will hold TPS better than four slower cores. RackNerd doesn't publish clock speeds per plan, so if your pack is CPU-bound, check the processor listed on the order page before you commit.

Sizing rules that hold up across providers:

- **1–3 players, vanilla, render distance 8–10:** 1 GB runs, 2 GB gives breathing room.
- **Up to ~8 players vanilla, or a handful of plugins:** 2 GB. This is where most private worlds land.
- **10–20 players, Spigot/Paper with a plugin stack:** 4 GB. Liquid Web's stated minimum for a smooth server is a dual-core 3.0 GHz chip, 4 GB of RAM and 10–20 GB of SSD.
- **FTB, ATM, Create-heavy packs:** 4–8 GB, depending on pack size and how many chunks stay loaded.
- **Public server or a multi-server network:** 8 GB and up, or split across two VPS with BungeeCord or Velocity in front.

One rule that saves an evening: leave 512 MB to 1 GB for the operating system. A 2 GB VPS running a JVM with `-Xmx2G` will get OOM-killed within an hour. On the 2 GB plan, set `-Xmx1536M` and leave the rest alone.

What about cores? A modpack that generates chunks fast or a server with a hundred redstone clocks will use a second thread, but four vCPU won't rescue you if the heap is too small. Buy RAM first.

👉 [See the 4 GB plan if you're running a modpack or a plugin stack](https://bit.ly/RacKnerd)

## First-term price, renewal price, and what a year actually costs

RackNerd's structure is easy to reason about: one payment covers twelve months at the rate in the table above, and there's no monthly invoice to track. That's a different shape from what most of this market advertises.

Take Hostinger, whose game VPS page lists Game Panel 1 at $6.99/mo. That rate requires paying **$167.76 upfront for 24 months**, and it renews at $11.99/mo for the following term. The second 24 months costs $287.76. The headline again: Cloudzy's 2 GB plan shows $7.48/mo, which is a 50% discount off a $14.95 list price, and LightNode's up-to-$15 first top-up credit is a one-time offset, not a recurring discount.

| Provider | Plan | RAM | Price as displayed | Billing notes |
| --- | --- | --- | --- | --- |
| RackNerd | 2 GB KVM | 2 GB | $35.99 | Per year, one payment |
| Hostinger | Game Panel 1 | 4 GB | $6.99/mo | $167.76 for 24 months; renews at $11.99/mo |
| Cloudzy | 2 GB tier | 2 GB | $7.48/mo | 50% off $14.95; 14-day money-back |
| LightNode | Start | 2 GB | $7.71/mo | Hourly billing available |
| Liquid Web | Iron | 4 GB | $17/mo | Page dated November 2024; term not stated |

Every price in that table is what the provider's page displayed when it was checked, and most carry a discount tag that can change without notice. Three questions settle the real cost of any of them: how many months does this rate lock in, what does it renew at, and can I pay monthly first to test. RackNerd answers the first one on the order form; get the other two in writing wherever you buy.

👉 [Compare RackNerd's annual plans before you commit to a term](https://bit.ly/RacKnerd)

## Setup: ten steps and three places people get stuck

Ubuntu or Debian, root over SSH, about twenty minutes.

1. `ssh root@your-ip`
2. `apt update && apt upgrade`
3. Install Java 17 or newer: `apt install openjdk-17-jre`, or `openjdk-21-jre-headless` if you want 21.
4. `mkdir minecraft && cd minecraft`
5. Upload the server `.jar` (Paper, Purpur, Fabric, Forge, whatever you're running) with `scp` or SFTP.
6. Run it once: `java -Xmx1536M -Xms1536M -jar server.jar nogui`. It will exit and write `eula.txt`.
7. Edit `eula.txt` and set `eula=true`.
8. Edit `server.properties` for motd, view-distance, online-mode and difficulty.
9. Open the port: Java uses **25565 TCP**, Bedrock uses **19132 UDP**. Open it in `ufw` and in the ctrl panel's network firewall, because both can block you.
10. Restart inside a persistent session: `screen -S mc java -Xmx1536M -Xms1536M -jar server.jar nogui`, then `Ctrl+A` `D` to detach. Schedule backups before you invite anyone.

The three recurring failures: forgetting `eula=true` (the server exits silently), setting `-Xmx` equal to total RAM (OOM kill), and opening the port in only one of the two firewalls (connection timed out, server looks dead from outside).

## Who this isn't for

RackNerd's plans are unmanaged KVM boxes. That's the right shape if you're comfortable in a terminal and want root, but it's the wrong purchase in a few cases:

- **You want a control panel with one-click modpack switching.** Hostinger's game panel advertises 2,000+ modpacks you can swap from a dashboard. That convenience is what you'd be paying for.
- **You need hourly billing for a weekend test.** Cloudzy and LightNode both bill hourly; RackNerd's plans are annual.
- **You want a published refund window as a safety net.** Cloudzy publishes a 14-day money-back guarantee. Hostinger only promises "cancel anytime." If a refund window is a deciding factor, ask before you order rather than assuming.
- **You need a specific DDoS filtering tier in writing.** Get the terms confirmed by support first, whichever provider you pick.

## FAQ

**Can my friends on Switch, Xbox or phones join a Java server?**
Not directly. Java listens on 25565 TCP; Bedrock Dedicated Server listens on 19132 UDP. Either run a Bedrock server for those players, or install GeyserMC so Bedrock clients can connect to your Java world.

**How many players can 2 GB hold?**
Five to eight on vanilla with a modest render distance. Add a plugin stack or a large farm-loaded spawn and you'll want 4 GB.

**Do modpacks really need 8 GB?**
A small pack runs on 4 GB. Eight GB is for heavy packs (ATM, Create-heavy builds) or a dozen players generating chunks at once. Over-allocating RAM won't fix a slow single thread either.

**If I move to a different region later, does my IP change?**
Yes. You'd copy the world files to the new server, test it, then tell everyone the new address. Budget an evening for that, and keep the old box alive until the migration is confirmed.

**Is a $21.99/year server usable for Minecraft?**
For one to three players on vanilla with render distance turned down, yes. It is not a modpack box, and it will not survive a public player list.

## Picking your plan

Match the plan to the world, not to a vague idea of "more power later."

- **One to three friends, vanilla:** the 1 GB plan if you'll keep render distance low, the 2 GB if you want headroom for a future plugin or two.
- **A private SMP with plugins or a light pack:** 4 GB at $59.99/year.
- **Heavy modpack or 15+ players:** 6 GB, or 8 GB if you're also running a proxy in front.
- **Bedrock-first group:** confirm the port situation and your plan for cross-play before you pay for anything, on any provider.

Two things to verify on the order form before you finish: the term length you're agreeing to, and the renewal rate for the following year. Both cost nothing to check and are the two numbers that decide whether a cheap server stays cheap.

👉 [Start with the 2 GB KVM plan and have Java running tonight](https://bit.ly/RacKnerd)
