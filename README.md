# SpacetimeDB Free Tier Gets You 2,500 TeV/Month: No Server, No Docker, No $500 AWS Bills

So here's the situation. You have an idea for a multiplayer game — or maybe a real-time collaborative app. You know the drill: Docker Compose files, Kubernetes configs, a WebSocket server you'll write from scratch, and an AWS bill that shows up before you've shipped anything. SpacetimeDB keeps coming up in developer communities as the escape hatch from all of that. It hit 24,000+ GitHub stars, just dropped version 2.0 in February 2026, and the pricing got a serious overhaul. Let's dig in.

<img width="2703" height="1475" alt="image" src="https://github.com/user-attachments/assets/3e2866c6-b94c-4a78-81ea-ae5c1b7c6b7c" />

---

## What Even Is SpacetimeDB?

Shortest version: your database and your server, collapsed into one thing.

Normal backend flow goes: client → server → database → server → client. SpacetimeDB cuts out the middleman entirely. Your application logic (called "reducers") runs *inside* the database, compiled to WebAssembly. Clients connect directly. When state changes, updates push to subscribed clients automatically. No polling, no refetching, no WebSocket boilerplate you had to write yourself.

You write your schema and business logic as a module in Rust, C#, TypeScript, or C++. SpacetimeDB compiles it, runs it inside the database, and automatically synchronizes state to connected clients in real time. The whole thing is written in Rust, so memory safety and performance come baked in.

The proof-of-concept that makes people take this seriously: the entire backend of BitCraft Online, a full-scale MMORPG, runs as a single SpacetimeDB module — chat, items, terrain, player positions, everything, synchronized to thousands of players in real time. Seven engineers built that. That's wild.

One developer described it as: *"Think of it as Supabase but for building games."*

👉 [Claim your free 2,500 TeV/month credit and start building](https://spacetimedb.com/?referral=hm5483188)

---

## The 2.0 Benchmarks (And the Honest Take)

SpacetimeDB 2.0, released in February 2026, posted some attention-grabbing benchmarks — over 150,000 transactions per second for Rust modules, and over 100,000 for TypeScript modules. For comparison, Node.js with PostgreSQL handled around 1,500 in the same test — roughly a 100x gap.

The architecture explains why those numbers are possible. When your logic runs inside the database, you eliminate network hops, serialization overhead, and context switching. All state lives in memory, right where your code needs it.

That said, be honest with yourself about what these benchmarks measure. SpacetimeDB is an all-in-one database and application server where you deploy a database instance and your application's code runs inside the database itself — which is a very different offering than the distributed databases it benchmarks against. For real-time multiplayer workloads, the performance wins are very real. For multi-region, highly available distributed systems, it's a different conversation.

---

## Pricing: The Free Tier Is Actually Real

SpacetimeDB uses an energy-based credit system measured in TeV (Tera-electron-Volts — yes, they leaned into the particle accelerator branding). You consume energy when your modules execute operations, send data to clients, or store data.

Here's what the plans look like:

| Plan | Monthly Price | Free Energy Credit | Approx. Equivalent | Key Features |
|---|---|---|---|---|
| **Maincloud Free** | $0 | 2,500 TeV/mo | ~3M function calls, ~12.5 GB egress, ~1 GB storage | Unlimited MAUs, 5 collaborators/DB, community support |  [Start Free](https://spacetimedb.com/login?referral=hm5483188) |
| **Maincloud Pro** | $25/mo | 100,000 TeV/mo | ~120M function calls, ~500 GB egress, ~40 GB storage | Auto backups, pay-as-you-go overage, email support, SLA |  [Go Pro](https://spacetimedb.com/login?from=/settings/billing&referral=hm5483188) |
| **Maincloud Team** | $250/mo | 250,000 TeV/mo | ~300M function calls, ~1,250 GB egress, ~100 GB storage | Named org, dedicated nodes, unlimited collaborators, priority support |  [Build a Team](https://spacetimedb.com/login?from=/settings/billing/organization&referral=hm5483188) |
| **Enterprise** | Custom | Custom | Custom | Custom deployment, BYO Cloud, 24/7 support, dedicated onboarding |  [Talk to a Founder](https://spacetimedb.com/contact-a-founder) |

The overage rate for Pro and Team is 2,592 TeV per dollar once you exceed the included credit. Storage pricing dropped significantly in late 2025, going from $10/GB/month down to $1/GB/month while maintaining the same in-memory performance.

Three million reducer calls a month on the Free tier is not a toy demo limit. That's enough to run actual applications and see if this thing fits how you build.

---

## The Space Race Referral Program: Free Credits That Stack

This is the interesting part. SpacetimeDB runs a referral program called Space Race, and it's structured unusually well.

When you sign up through a referral link, both you *and* the person who referred you permanently get +2,500 TeV/month added to your monthly credit. Not a one-time bonus — every month, forever.

If the referred user upgrades to Pro, the referrer gets an additional 22,500 TeV/month bonus on top of that. Free tier users can stack referrals up to 100,000 TeV/month — the same credit as the paid Pro plan, but free. Pro tier users can stack up to 1,000,000 TeV/month.

So if you're on the Free plan and you refer enough developers, you can hit Pro-equivalent compute for $0 a month. Permanently. That's not a typo and it's not a limited-time thing — the rewards are a permanent change to your account.

👉 [Sign up with a referral link and grab your free bonus TeV right now](https://spacetimedb.com/?referral=hm5483188)

---

## Who Should Actually Use This?

**Indie game developers.** This is what SpacetimeDB was literally designed for. Real-time state sync, subscription queries, scheduled reducers for NPC behavior and respawns — it handles the hard parts of multiplayer game backends. If you're building in Unity (C#), Unreal (C++), or just targeting web (TypeScript), the client SDK generates matching types automatically.

**Solo devs and small teams.** No Kubernetes. No Docker. No separate server to maintain. One deploy command. One developer shipped their app to the App Store in three months and said 95% of that time went to the frontend — the backend was, in their words, "completely plug-and-play."

**Real-time web app builders.** SpacetimeDB has TypeScript support and React hooks. One developer used it to build a full Discord clone with channels, threads, and real-time messaging in a single AI-assisted session. If your app needs live data that multiple users see simultaneously — collaborative tools, live dashboards — this architecture fits naturally.

**AI-assisted development.** Because the entire backend lives in one coherent place, LLMs work significantly better with it. Less context to juggle means better results from AI coding tools.

---

## What Developers Are Actually Saying

One developer who's been building with SpacetimeDB noted: "I haven't come across any obvious limitations for the kind of project I'm building. It feels robust, the developer experience is smooth, and the performance is great."

Another developer who spent three months putting it through its paces called it a "paradigm shift" — a developer experience so streamlined it felt like cheating. They highlighted how Rust's compile-time type checking drastically reduced runtime errors in data manipulation.

The critical takes exist too. Some reviewers note that the benchmark setup is comparing apples to particle accelerators — your application logic running inside the database will naturally outperform a separate app server making network calls. Fair point. For use cases where multi-region replication or fine-grained distributed guarantees matter, SpacetimeDB is not the right tool. But for the real-time, low-latency workloads it targets, the speed is genuine.

---

## The Bottom Line

SpacetimeDB is a genuinely different idea — not just another database with a splash page. The architecture has real performance implications for the workloads it's designed for, and the fact that it powers an actual production MMORPG is probably the best validation. MMOs are notoriously difficult from an infrastructure perspective, and if SpacetimeDB can handle that with a small team, it can probably handle your real-time app.

The Free tier gives you enough runway to actually build something and find out. The Space Race referral bonus means signing up through a referral is just leaving free credits on the table if you don't.

👉 [Sign up now, claim your 2,500 TeV/month bonus, and see what building without a server actually feels like](https://spacetimedb.com/?referral=hm5483188)
