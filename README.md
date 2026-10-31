# ISA Context

A JSON-LD context for ISA (Investigation / Study / Assay) metadata in RO-Crates, served via GitHub Pages
so that it is delivered as `application/ld+json`.

## Usage

Add the context URL to the `@context` of an `ro-crate-metadata.json`, next to the RO-Crate context:

```json
{
  "@context": [
    "https://w3id.org/ro/crate/1.1/context",
    "https://thejacksonlaboratory.github.io/isa-context/isa_context_1_0.jsonld"
  ]
}
```

With [python rocrate](https://pypi.org/project/rocrate/):

```python
crate.metadata.extra_terms = "https://thejacksonlaboratory.github.io/isa-context/isa_context_1_0.jsonld"
```

## Serving

A GitHub Actions workflow (`.github/workflows/pages.yml`) validates the `*.jsonld` files and deploys them to
GitHub Pages on every push to `main`. In the repository settings, Pages > Source must be set to **GitHub Actions**.
Verify headers with:

```
curl -I https://thejacksonlaboratory.github.io/isa-context/isa_context_1_0.jsonld
```

Expect `Content-Type: application/ld+json` and `Access-Control-Allow-Origin: *`.

## Background

Migrated from [ro-crate-isa-context](https://github.com/TheJacksonLaboratory/ro-crate-isa-context), which served the
context from raw.githubusercontent.com as `text/plain`. Term mappings are unchanged from that repo's
`isa_context_1_0.json`.
