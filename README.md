# PAFI Docs

Source for the PAFI protocol documentation, built with Mintlify.

## Before writing

Read [`AGENTS.md`](./AGENTS.md) first. It carries the source of truth order, the banned vocabulary, the terminology dictionary, the hyphen allowlist, the page length bands, and the disclaimer placement rules. It applies to humans and to AI assistants equally.

## Structure

```
index.mdx            Welcome
get-started/         4 task pages
learn/               11 concept pages
issuers/             Overview, Listing, Integration, Running a listing
governance/          Governance, PAFI token, votes, rewards, Deficit Reserve
developers/          Integration API, Contracts, Addresses, Parameters, Events
security/            Audits, Official domains
resources/           Whitepaper, Brand kit, Legal
```

Navigation is declared in `docs.json`. A new page must be added there or it will not appear.

## Local preview

```
npm i -g mint
mint dev
```

Check links before opening a pull request.

```
mint broken-links
```

## Publishing

Changes deploy automatically after merging to the default branch.
