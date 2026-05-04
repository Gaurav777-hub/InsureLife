# InsureLife Analytics — Azure Databricks Project

## Overview
End-to-end life insurance analytics pipeline built on Azure Databricks
using Delta Lake, DLT, Unity Catalog and Delta Sharing.

## Architecture
ADLS Gen2 (Landing) → DLT Pipeline → Bronze → Silver → Gold → Delta Sharing

## Catalog Structure
insurelife_catalog
├── bronze      → raw ingested data (Auto Loader)
├── silver      → cleaned, validated, typed
├── gold        → business aggregates
└── governance  → masking functions & row filters

## Notebooks — Run Order
1. notebooks/00_setup/00_catalog_setup     → one-time UC setup
2. Trigger InsureLife_DLT_Pipeline         → populates all layers
3. notebooks/03_delta_ops/03_delta_ops     → MERGE + OPTIMIZE
4. notebooks/05_analytics/05_analytics     → validate gold layer

## Config
- config/dev.yml   → development environment
- config/prod.yml  → production environment
Load via: notebooks/load_config (add as first cell in every notebook)

## Storage
- Account   : adlsstorage44
- Container : lifeinsuranceproject
- Landing   : /landing/
