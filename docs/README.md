# EcoGrid Documentation

This directory contains the maintained technical documentation for the EcoGrid mobile client.

## Current documentation

| Document | Purpose |
| --- | --- |
| [`ARCHITECTURE.md`](ARCHITECTURE.md) | High-level application architecture and layer responsibilities |
| [`CONNECTIVITY.md`](CONNECTIVITY.md) | ESP32/API connectivity, polling, retries, lifecycle behavior, and troubleshooting |
| [`DATA_CONTRACTS.md`](DATA_CONTRACTS.md) | Sensor data sources, supported variables, endpoint contracts, and export flow |
| [`NAVIGATION.md`](NAVIGATION.md) | Current GoRouter routes, screen responsibilities, and bottom navigation |
| [`IMPLEMENTATION_STATUS.md`](IMPLEMENTATION_STATUS.md) | Current application status, implemented screens, and known maintenance notes |
| [`UI_HISTORY.md`](UI_HISTORY.md) | Consolidated historical design notes from earlier main-menu and dashboard iterations |

## Documentation policy

The documents in this directory are written in English and are intended to describe the current repository as accurately as possible.

Historical implementation proposals have been consolidated into `UI_HISTORY.md` instead of remaining as multiple root-level planning files. When a historical note conflicts with the current Flutter code, the current code is authoritative.

The repository contains only the Flutter mobile client. ESP32 firmware, Google Apps Script code, hosted APIs, and external infrastructure are outside this repository unless a future change explicitly adds them.
