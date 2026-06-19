# 10 - 3D Printing Construction Industry

## Objective
Build an interactive global map and dashboard of the 3D printing construction industry: companies, projects, technologies, and market analysis - with focus on applicability to Kazakhstan/Central Asia housing development.

## Data Inventory
| Dataset | File(s) | Format |
|---------|---------|--------|
| 3D Printing Building Companies | `3D Printing Building Companies.xlsx` | XLSX |
| Industry map notebook | `3dprinting_construction industry_map.ipynb` | Notebook |
| COBOD workshop task | `Workshop_Task.pdf` | PDF (reference) |
| COBOD global price list 2023 | `GLOBAL_PRICE LIST_2023 (EU).pdf` | PDF (reference) |
| 3D printing overview (Pomazan) | `3dprinting_Pomazan.pdf` | PDF (reference) |
| Seismic design for 3DPC buildings | `2023_AghajaniDelavar_etal_SeismicDesignMethodologyFor3DPCBuildings.pdf` | PDF (reference) |
| Structural health sensors | `3D printed vorticella-kirigami inspired sensors.pdf` | PDF (reference) |
| Automated construction | `Toward automated construction.pdf` | PDF (reference) |
| Other academic papers | `pone.0009596.pdf`, `8f8485357948b22f412a8cd03102637c_original.pdf` | PDF (reference) |
| 3D print robots | `robots/*` | Various |

## Plan

### Phase 1 - Data Preparation
1. Parse `3D Printing Building Companies.xlsx`: extract company name, country, city, technology type, materials, project count, year founded, website
2. Geocode all companies (city/country -> lat/lon coordinates)
3. Review and extract structured data from existing notebook
4. Extract key specs from COBOD price list: printer models, build volumes, speeds, prices
5. Build technology taxonomy: extrusion-based, binder jetting, robotic arm, gantry, etc.
6. Compile project database: notable completed 3D-printed buildings worldwide (from company data + web enrichment)
7. Extract key findings from academic papers for annotation layer

### Phase 2 - Interactive Map (Folium / Deck.gl)
1. **Global company map**: markers for each 3D printing construction company
   - Color by technology type
   - Size by number of completed projects or company maturity
   - Popup: company name, tech, materials, notable projects, website link
2. **Project locations**: where 3D-printed buildings have been built
   - Popup: building type, year, company, size, cost if available
3. **Regional clusters**: auto-clustered markers at zoom-out level
4. **Kazakhstan context layer**:
   - Almaty region highlight
   - Nearest 3D printing companies / potential partners
   - Seismic zone overlay (reuse from project 7) for structural design context
5. **Technology heatmap**: density of companies by technology type per region
6. Filter by: technology, material, country, year range

### Phase 3 - Dashboard (Plotly Dash / Panel)
1. **KPI cards**: total companies worldwide, total completed projects, countries with activity, avg building cost
2. **Technology breakdown**: pie/donut chart of companies by technology type
3. **Geographic distribution**: bar chart of companies by continent/country
4. **Timeline**: line chart of industry growth (companies founded per year, projects completed per year)
5. **Materials comparison**: grouped bar chart showing material types used (concrete, clay, polymer, etc.)
6. **Cost analysis**: scatter plot of building cost vs size (where data available)
7. **COBOD specs table**: interactive table of printer models with specs
8. **Company directory**: searchable/sortable table of all companies
9. **Kazakhstan feasibility panel**:
   - Distance to nearest suppliers/partners
   - Climate compatibility assessment
   - Seismic requirements summary
   - Cost comparison: 3D-printed vs traditional construction in KZ
10. **Academic insights sidebar**: key findings from papers (seismic design, automation, sensors)

### Phase 4 - Data Enrichment (optional)
1. Scrape/API-fetch additional company data from web sources
2. Add recent project completions from news/press releases
3. Include material suppliers and logistics network

### Phase 5 - Integration & Export
1. Unified dashboard with embedded global map
2. Export: company database CSV, technology comparison PDF
3. Deploy as standalone HTML app

## Tech Stack
- HTML5 + CSS3 + Vanilla JavaScript (standalone, no build step)
- Leaflet.js (interactive map with CartoDB dark tiles)
- YouTube Embed API (company videos)
- CSV (data export format)

## Deliverables
- `index.html` - standalone interactive dashboard with global map + company cards + YouTube videos
- `data/processed/3dpc_companies_2026.csv` - cleaned company database (63 companies, 28 countries)
- `data/companies/3D Printing Building Companies.xlsx` - original dataset (74 entries)

## Status (Updated 2026-06-19)
- [x] Phase 1 - Data extracted from XLSX, enriched with web research, 63 companies across 28 countries
- [x] Phase 2 - Interactive Leaflet map with tech-colored markers, popups, legend, fly-to
- [x] Phase 3 - Sidebar dashboard with search, filters (technology/country), company cards, embedded YouTube
- [x] CSV export with full company data (name, country, city, lat/lon, tech, equipment, material, founded, website, YouTube, status)
- [ ] Phase 4 - Optional: further data enrichment, project locations layer, Kazakhstan context
