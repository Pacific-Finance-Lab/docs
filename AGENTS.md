# AGENTS.md

Rules for anyone, human or AI, writing in this repository. Read this before editing any `.mdx` file.

The full internal style document (`PAFI_Docs_STYLE.md`) is the parent of this file. Where the two conflict, the internal document wins.

## Source of truth

In this order, later overrides earlier.

1. `Final Whitepaper (2026-07-31)`
2. `Decisions, Constraints, and Handoff Rules`
3. `PAFI Integration Guide for Issuers`, English edition
4. Engineering documents. `AI Assistant / Overview` is the only basis for the PAFI Agent page

Do not invent a fact the whitepaper does not carry. Where the whitepaper is silent, mark the value `Not yet set` or `To confirm` and link the page that will hold it.

## What these docs are for

The whitepaper argues. These docs instruct.

Why points are represented the way they are, why a cycle has declared terms, why coverage is sized as it is: all whitepaper. Do not restate those arguments here. Resources links the whitepaper, that is the whole relationship.

## Writing rules

**Delete first.** Keep a sentence only if removing it stops the reader doing something. This is the rule most often broken.

**Do not argue.** A heading starting with `Why` is almost always an argument. Delete it or reduce it to one factual sentence. Two exceptions: troubleshooting sections (`Why a conversion can fail`) are fact lists, and risk pages are the place to say what is risky and why.

**Capability before guardrails.** On a feature page, write what the reader can do, then a real example, then how to use it, then what bounds it. Guardrails go last, not first.

**Third person for authority and mechanism.** No `we`. Second person `you` only on task pages and issuer procedure pages.

**No marketing adjectives.** State uncomfortable facts plainly.

**End paragraphs with the conclusion.** Do not stop at a list of facts.

## Tables

Too many tables makes a document read as machine written. Use a table only when all three hold.

1. Three or more items
2. Two or more attributes per item, and the attributes differ across items
3. The reader compares across rows

If any one fails, write prose or a list. Two column name and description lists are almost always better as prose.

Check: rows times 6, divided by body word count. Over 15 percent, cut.

## Hyphens

Do not create new hyphenated compounds. The allowed list, all of which exist in the whitepaper:

`on-chain`, `off-chain`, `self-custodial`, `non-custodial`, `third-party`, `issuer-gated`, `issuer-defined`, `price-referenced`, `contract-level`, `stable-value`, `two-hop`, `real-world`, `governance-set`, `liquidity-routing`, `protocol-wide`, `load-bearing`, `per-token`, `lock-up`, `Zero-Barrier`

No em dashes. No middle dots. No coinages that do not appear in the whitepaper or the integration guide. The one kept exception is `Zero-Barrier DeFi Experience`, which must always carry the phrase "PAFI refers to this capability as".

## Banned vocabulary

These are elements of regulatory definitions. Introducing the word is the risk, so do not use them even in a denial.

| Banned | Basis |
|---|---|
| `on behalf of` | MiCA Art 3(1)(17), 3(1)(26) |
| `means of access` | MiCA Art 3(1)(17) |
| `provide`, `provider` with PAFI as subject | MiCA CASP, FATF VASP |
| `manage`, `administer`, `custody`, `safekeep`, `control` with PAFI as subject | FATF 2021 para 73 |
| `share`, `shared wallet` | Implies the account is the operator's property |
| `discretionary` | Exactly one occurrence site-wide, in `learn/who-operates-what.mdx` |
| `protect`, `protection`, `safeguard` | Zero site-wide |
| `insurance` | Zero site-wide |

`liquidity provider` and `liquidity provided by` are fine. The whitepaper uses them and PAFI is not the subject.

## Terminology

Use the left column.

| Use | Not |
|---|---|
| account | wallet. Keep `wallet` only in SDK field names and integration guide code |
| integrated venue | partner, partner venue |
| committed stablecoin | collateral |
| issuance budget | issuance cap |
| holder exit window | exit pot, redemption window |
| Deficit Reserve | Protocol Risk Reserve |
| PAFI Agent | AI Agent, AI Chatbot, chatbot, agent interface |
| issuer | authorized point issuer |
| listing proposal | application, onboarding |
| governance vote | protocol discretion, at PAFI's discretion |
| USD stablecoin | USDT, USDC |
| routing layer | bridge |

The PAFI token has **four** functions: governance, issuer staking, fee benefits, ecosystem incentives.

`L` is the **issuer inventory allocation**. Once it enters the pool it is **liquidity**, not inventory. Connect both in one sentence for readers coming from either side.

### Statements that are wrong

- One issuer, one token. An issuer can list more than one point token.
- A point token is minted to an issuer designated address. It is issued to the user's account.
- Staking unlocks issuer status. Staking is a precondition for submitting a proposal.
- PAFI Oracle. There are four components and none of them is an oracle.

## Abstraction level

| Item | These docs |
|---|---|
| Standard numbers (ERC-20, EIP-7702) | Use |
| Chain names, vendor names | `developers/` and `issuers/` only. Never in a concept page |
| Internal module names (PointToken, Connector) | Use |
| Product versions (PAFISwap V3) | Drop the version. `PAFISwap` |
| Phase notation (Phase 1, beta, coming soon) | Never, anywhere |
| Integrated venue names | Use |
| Issuer names | Never |

A concept page tied to infrastructure detail goes stale when the infrastructure changes. `deployed on Arbitrum` belongs in `developers/contracts.mdx` and nowhere else.

**Learn is high level. Reader sections are concrete.** Symbols (`P0`, `I`, `U`, `L`, `CR_min`), relations, allocation limits, and parameter names do not appear in `learn/`. Link to the page that holds them instead of copying the value across. The single exception is `learn/glossary.mdx`, which is the site-wide lookup point for symbol definitions.

**Do not assert unconfirmed implementation.** Whether listing screening runs in contracts is not settled. Write the outcome, not the actor.

| Do not write | Write |
|---|---|
| The contracts check coverage, lock period, staking, and the template | The criteria are checked before any vote takes place |
| screened against contract-level criteria | checked against the listing criteria |

This is the only place these docs are less specific than the whitepaper. Reverse it once implementation is settled.

## Unresolved values

```mdx
<Info>
  **Not yet set.** `CR_min` is a governance-set value. See [Parameters](/developers/parameters).
</Info>
```

Never promise a date. No "will be published in Q3".

## Where disclaimers go

Not scattered through the body. Only these pages.

| Page | Carries |
|---|---|
| `learn/who-operates-what.mdx` | The five parties. The single permitted `discretionary` |
| `learn/liquidity-routing.mdx` | Licensing |
| `learn/risks.mdx` | Holder and general risk |
| `issuers/running/risks.mdx` | Issuer risk only |
| `resources/legal/` | Terms, Privacy, Disclaimers, Risk Disclosures |

Before adding a disclaimer sentence, check whether it is already on one of these pages.

Every risk page needs a non-exhaustiveness statement.

## Page length

No global cap. Bands by page type, measured against real reference docs.

| Type | Words |
|---|---|
| Router | 60 to 200 |
| Task | 200 to 400 |
| Concept | 300 to 800 |
| Mechanism | 800 to 2,000 |
| Risk sub-page | 600 to 1,500 |
| Reference | No limit |

A risk page is longer than the mechanism page it qualifies. Do not pad to reach a band. If a page ends short, leave it short.

## Diagrams and screenshots

Default is none. Add one only when the content is a sequence or a topology and prose would take more than 150 words.

Approved positions, and no others without a written reason:

| ID | Page | Content |
|---|---|---|
| `D1` | `learn/how-pafi-works.mdx` | Topology from issuer system through Gateway to integrated venue |
| `D2` | `learn/listing-cycles.mdx` | Cycle timeline |
| `D5` | `learn/life-of-a-point.mdx` | Five lifecycle states. High level, no figures or limits |
| `D3` | `issuers/integration/issue-point-tokens.mdx` | Issuance sequence. Exists in the integration guide, port it |
| `D4` | `issuers/integration/redeem-point-tokens.mdx` | Redemption sequence. Exists in the integration guide, port it |

Screenshots go only on the four Get Started task pages, after the UI is settled. Pending markers are written as a `<Note>` carrying `[D2]` or `[S1]`.

## Mintlify conventions used here

- Body headings start at `##`. The page title comes from frontmatter.
- Every page has `title` and `description` in frontmatter.
- Prev and next links are generated from `docs.json`. Do not hand write them.
- Callouts: `<Info>` for unresolved values and pending ports, `<Note>` for asides and pending diagrams, `<Warning>` for things that cost the reader money or access.
- `<Steps>` for procedures on task pages.
- Internal links are absolute paths without the extension, for example `/learn/risks`.

## Before you commit

1. Does every remaining sentence stop the reader doing something if removed
2. Any banned vocabulary
3. Any term off the dictionary
4. Any chain or vendor name in a concept page
5. Any disclaimer outside the five listed pages
6. Any new hyphenated compound
7. Any fact asserted that the whitepaper does not carry
8. Any date promised on an unresolved value
9. Word count calculated, not eyeballed
10. Any diagram outside the approved list

## Open items

| Item | Blocks |
|---|---|
| Point token standard | `To confirm` on `developers/contracts.mdx` |
| `CR_min`, minimum lock period, staking minimum, exit window length, grace period, timelock delay, fee rates | All of `developers/parameters.mdx`, which 14 callouts across the site point at |
| Audit reports | `security/audits.mdx` |
| Contract addresses | `developers/addresses.mdx` |
| Whether the staking requirement is per listing or aggregate | `To confirm` on `issuers/listing/terms-and-commitments.mdx` |
| Six integration pages | Port from the integration guide English edition |
| Legal disclaimers and consolidated risk disclosures | `resources/legal/` |
| `D1`, `D2`, `D5` | Learn pages, marked in place |

### When porting the integration guide

- `wallet` becomes `account` in prose. SDK field names keep `wallet`.
- Add the one account principle. Signing in from a second issuer app does not create a second account.
- Link limits to `/issuers/listing/terms-and-commitments` rather than restating them.
- Replace "may be treated as a breach of contract" with the slashing condition wording. There are two conditions and no authority outside them.
- Replace `provides` wherever PAFI is the subject.
- Remove the roadmap reference from Forward-Looking Statements. The whitepaper no longer carries a roadmap.
