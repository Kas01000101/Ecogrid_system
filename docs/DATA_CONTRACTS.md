# EcoGrid Data Contracts

## Scope

This document consolidates the older connection, routes, and chart documentation into a single English reference for the Flutter mobile client.

EcoGrid currently works with environmental measurements for:

- temperature;
- humidity;
- pH;
- TDS;
- UV.

Not every historical endpoint documented in earlier planning files is guaranteed to be implemented by the external backend. The external API and ESP32 firmware are outside this repository, so their deployed behavior must be verified independently.

## Direct ESP32 mode

The mobile client can be configured with an ESP32 address for direct HTTP access over the local network.

A typical aggregated contract used by earlier EcoGrid integrations is:

```json
{
  "timestamp": "2026-01-01T12:00:00Z",
  "temperatura": 26.2,
  "humedad": 66.6,
  "ph": 5.74,
  "tds": 1301,
  "uv": 2.8
}
```

Sensor-specific integrations may expose one measurement at a time. Exact ESP32 routes belong to the firmware contract and should be kept consistent with the client configuration.

## External API mode

`ConnectionManager` can use an external API base URL. The current polling service requests:

```text
<apiBaseUrl>?endpoint=last1min
```

The response must be valid JSON that the active screen/service can decode into sensor values.

Historical reporting is handled separately by the reporting flow and may use additional API endpoints defined by the external service.

## Sensor units

| Variable | Typical unit |
| --- | --- |
| Temperature | °C |
| Humidity | % |
| pH | pH scale |
| TDS | ppm |
| UV | implementation-specific UV value/index |

The backend should use stable field names and numeric values. If timestamps are supplied, ISO 8601 UTC is preferred so the mobile client can format them for the user locale.

## Application responsibilities

### Sensor dashboard

`SensorDashboardScreen` presents the available environmental sensors and routes the user to a sensor-specific detail page.

### Sensor detail

`SensorDetailPage` is responsible for detailed sensor presentation and charting. It receives the sensor type and connection context from navigation.

### Device configuration

`DeviceConfigScreen` stores device configuration used by the application. Environment-specific addresses should not be treated as secrets unless they expose private infrastructure, but production credentials and tokens must never be committed.

### Reports

`PDFPage` handles historical reporting and export. The repository includes dependencies for PDF generation, printing, CSV export, file access, and sharing.

## Charting expectations

Charts are rendered with `fl_chart`. Incoming values should be normalized as numeric data before they reach visualization code. Invalid or missing fields should be handled safely instead of crashing the UI.

## Backend compatibility guidance

When implementing or changing an ESP32 firmware/API backend for EcoGrid:

1. Keep sensor keys stable across responses.
2. Return `application/json` for JSON endpoints.
3. Normalize numeric values with a period as the decimal separator.
4. Prefer UTC ISO 8601 timestamps.
5. Keep historical result sets bounded for mobile performance.
6. Document units explicitly.
7. Avoid exposing private device credentials in responses.

## Legacy documentation consolidation

The former root files `README_BLOQUES_RUTAS.md`, `README_CONEXION.md`, `README_CONEXION_ACTUALIZADA.md`, `README_CONEXION_BLOQUES.md`, and `README_GRAFICOS.md` described different stages of the integration and contained overlapping or conflicting endpoint examples. They have been consolidated here to avoid presenting obsolete routes as current runtime guarantees.
