# B2B Compliance & UK Public Procurement MCP Servers

Hosted **Model Context Protocol (MCP)** servers and batch data extractors on Apify for regulatory product compliance (**NSF International / cGMP**) and UK government tendering (**UK Government Commercial Agency — GCA, formerly Crown Commercial Service / CCS**).

Both tools run remotely via Streamable HTTP (`mcp.apify.com`) with **zero local Docker/Python setup**, plus structured CSV/JSON exports on the Apify Store.

---

## Included Hosted MCP Servers

| Server | Source Registry | Direct Apify Store & Glama Connector |
| :--- | :--- | :--- |
| **[NSF Certified Products & cGMP Facilities](https://apify.com/sreelalr/nsf-certified-products-gmp)** | `info.nsf.org/Certified/` | [![NSF Certified Products & cGMP MCP connector](https://glama.ai/mcp/connectors/io.github.sreelalr/nsf-certified-products-gmp/badges/score.svg)](https://glama.ai/mcp/connectors/io.github.sreelalr/nsf-certified-products-gmp) |
| **[UK GCA (formerly CCS) Public Procurement](https://apify.com/sreelalr/uk-ccs-frameworks-suppliers)** | `gca.gov.uk` (`crowncommercial.gov.uk`) | [![UK GCA & CCS Public Procurement MCP connector](https://glama.ai/mcp/connectors/io.github.sreelalr/uk-ccs-frameworks-suppliers/badges/score.svg)](https://glama.ai/mcp/connectors/io.github.sreelalr/uk-ccs-frameworks-suppliers) |

---

## Quick MCP Setup (Claude Desktop, Cursor, Windsurf, VS Code)

Add either or both hosted servers to your `mcp.json` / `claude_desktop_config.json` (see [`mcp-configs/mcp.json`](./mcp-configs/mcp.json)):

```json
{
  "mcpServers": {
    "nsf-certified": {
      "type": "http",
      "url": "https://mcp.apify.com/?tools=actors,sreelalr/nsf-certified-products-gmp"
    },
    "uk-public-procurement-gca": {
      "type": "http",
      "url": "https://mcp.apify.com/?tools=actors,sreelalr/uk-ccs-frameworks-suppliers"
    }
  }
}
```

---

## 1. NSF Certified Products & cGMP MCP Server

- **Apify Actor:** [sreelalr/nsf-certified-products-gmp](https://apify.com/sreelalr/nsf-certified-products-gmp)
- **Covered Registries:**
  - `Food` (`NSF/ANSI 2, 3, 4, 8...` commercial kitchen & warewashing equipment)
  - `Dietary` (`NSF/ANSI 173` certified dietary supplements, incl. Certified for Sport listings)
  - `GMP` (`NSF/ANSI 173 Section 8` / `21 CFR Part 111` cGMP registered manufacturers & distributors)
  - `PwsChemicals` (`NSF/ANSI/CAN 60` drinking water treatment chemicals & max dosage `mg/L`)
  - `Biosafety` (`NSF/ANSI 49` Class II biosafety cabinetry specs)
  - `Common` (cross-program company certification lookup)
- **MCP Tools:** `search_nsf_certified`, `lookup_nsf_company`, `list_nsf_programs`
- **Ready-to-Run Presets:**
  - [NSF cGMP Supplement Manufacturers Extractor](https://apify.com/sreelalr/nsf-certified-products-gmp/examples/nsf-cgmp-supplement-manufacturers)
  - [NSF/ANSI 60 Drinking Water Chemicals Lookup](https://apify.com/sreelalr/nsf-certified-products-gmp/examples/nsf-ansi-60-water-chemicals-lookup)
  - [NSF/ANSI 173 Dietary Supplements Extractor](https://apify.com/sreelalr/nsf-certified-products-gmp/examples/nsf-ansi-173-dietary-supplements)

---

## 2. UK GCA (formerly CCS) Public Procurement MCP Server

- **Apify Actor:** [sreelalr/uk-ccs-frameworks-suppliers](https://apify.com/sreelalr/uk-ccs-frameworks-suppliers)
- **Covered Data (`gca.gov.uk`):**
  - Active & upcoming `RMxxxx` frameworks (`PA2023` / `PCR2015`, start & expiry dates)
  - Lot-by-lot approved supplier rosters, direct bid contacts, and tender `mailto:` emails
  - Supplier DUNS numbers, UK postal addresses, websites, and **PPN 06/21 Carbon Reduction Plan (CRP) PDF URLs**
- **MCP Tools:** `list_ccs_frameworks`, `get_ccs_framework_suppliers`, `search_ccs_suppliers`, `get_ccs_supplier_profile`
- **Ready-to-Run Presets:**
  - [UK GCA RM6098 Tech Suppliers & Bid Emails](https://apify.com/sreelalr/uk-ccs-frameworks-suppliers/examples/uk-ccs-rm6098-tech-suppliers-contacts)
  - [All Active UK GCA & CCS Frameworks](https://apify.com/sreelalr/uk-ccs-frameworks-suppliers/examples/uk-gca-ccs-active-frameworks)
  - [UK GCA MCF4 Consultancy Suppliers & Emails](https://apify.com/sreelalr/uk-ccs-frameworks-suppliers/examples/uk-gca-mcf4-management-consultancy)

---

## Open Sample Datasets

Browse clean, deterministic outputs verified directly against the live registries in [`samples/`](./samples):

- [`samples/uk-gca-live-agreements-sample.csv`](./samples/uk-gca-live-agreements-sample.csv) ([JSON](./samples/uk-gca-live-agreements-sample.json)) — 60 live UK GCA (`gca.gov.uk`) framework agreements
- [`samples/uk-gca-rm6098-lot1-suppliers-sample.json`](./samples/uk-gca-rm6098-lot1-suppliers-sample.json) — RM6098 Lot 1 suppliers with tender emails & CRP PDFs
- [`samples/nsf-cgmp-california-facilities-sample.csv`](./samples/nsf-cgmp-california-facilities-sample.csv) ([JSON](./samples/nsf-cgmp-california-facilities-sample.json)) — 59 NSF/ANSI 173 Section 8 cGMP facilities in California

---

## Maintainer

Built and maintained by **[@sreelalr](https://apify.com/sreelalr)** (`Sreelal Raveendran Pillai`). Issues, selector edge cases, and schema requests can be filed directly in this repo or on the Apify Actor **Issues** tab.
