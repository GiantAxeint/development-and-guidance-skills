# Cautionary-tale retrospective: a free domain mistaken for another DDNS provider's domain (2026-09)

> Note: a real incident, anonymized. Domain and personal details are generalized to protect privacy; the teaching structure is fully preserved.

## Symptoms

A user was troubleshooting a CDN problem for their personal site `your-site.dpdns.org` (example). After several rounds with the AI they were still lost — the troubleshooting steps the AI gave simply had no matching entry point in the panels the user actually had.

## The user's real environment (facts)

- The domain was registered at a **free-subdomain platform** of the DigitalPlat FreeDomain kind (free second-level-domain platforms in the same family as us.kg).
- DNS was hosted on **Cloudflare** (the standard playbook for those platforms: register, then point the domain to Cloudflare).
- So the troubleshooting belonged in the **Cloudflare dashboard** and **that free-domain platform's panel** — and had **nothing to do with dynu**.

## The AI's error chain (mapped to the laws)

| Error | Law violated |
|---|---|
| Saw a domain that *looks like* a "free dynamic-DNS domain", never asked about the environment, and concluded it belonged to dynu (another free DDNS provider) | Law 2: ask about environment facts, never infer from name/appearance |
| dynu's free suffixes are ddnsfree.com / freeddns.org / kozow.com etc. — they never include that platform's suffix; the association was wrong to begin with, a zero-verification pattern match from memory | Law 1: touched a specific service without browsing/verifying it |
| Gave troubleshooting steps for dynu's panel; when the user couldn't find the entry point, the AI didn't go back and question its initial assumption — it rephrased and retried | Law 3: failed to align on the entry point; and the spirit of "when it doesn't fit, re-check the premise" |
| Never flagged the uncertain parts as "this is my inference, may be wrong" — spoke with the same confidence as established facts | Doctrine: distinguish certainty from inference |

## The correct flow (what should have happened)

1. User says "my domain has a problem on Cloudflare" → Law 2: **first ask** "where was this domain registered? which panel hosts the DNS? are you configuring CDN or records?" — if the user can't answer, the AI checks whois / browses the free-domain platform's site to confirm ownership.
2. Verify (Law 1): browse the relevant Cloudflare dashboard docs + the free-domain platform's panel docs; confirm that "free domain → Cloudflare" is the standard playbook.
3. Align on the entry point (Law 3): confirm which Cloudflare page the user is on and where they're stuck.
4. Move forward one step at a time (Law 5); ask the user to report back after each step.

## General lessons

- Free-domain suffixes are numerous and their rules change fast (DigitalPlat-like platforms, DuckDNS, eu.org, is-a.dev, …). **Memory goes stale quickly — always verify by actually looking.**
- A "reasonable-looking error" is far more dangerous than an obvious one: if the AI says "I don't know", the user will go check; if the AI confidently says something wrong, the user believes it and burns several rounds.
