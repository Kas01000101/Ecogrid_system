# EcoGrid Connectivity

## Overview

EcoGrid uses HTTP polling to retrieve environmental measurements from either an ESP32 reachable on the local network or an external HTTP API. The connection layer is centralized in `ConnectionManager`.

The current implementation does not use WebSockets. A WebSocket enum value exists in the service, but the runtime falls back to HTTP polling.

## Connection states

```text
disconnected
connecting
connected
reconnecting
error
```

These states are exposed through a broadcast stream so the UI can represent connectivity explicitly.

## Data sources

`ConnectionManager.initialize(...)` accepts:

- `apiBaseUrl` for an external HTTP API;
- `esp32Ip` for direct ESP32 access;
- `sensorType` for sensor-specific requests;
- an optional polling interval;
- a flag controlling lifecycle-aware behavior.

If an API base URL is configured, the service uses it. Otherwise, it can poll the ESP32 directly.

## Polling behavior

The active defaults in `lib/services/connection_manager.dart` are:

```text
Foreground interval   58 seconds
Background interval   5 minutes
HTTP timeout          10 seconds
Maximum retries       5
Base retry delay      2 seconds
Retry strategy        Exponential backoff
```

The initial request is performed when polling starts. A periodic timer then refreshes data while the connection remains active.

## Lifecycle awareness

When lifecycle-aware behavior is enabled, `LifecycleManager` recommends the appropriate refresh interval for the app state. The polling timer is adjusted when the foreground/background state changes.

This design keeps active monitoring reasonably fresh while reducing background network work.

## Data and status streams

The connection service exposes two broadcast streams:

- `dataStream` for incoming decoded sensor data;
- `statusStream` for `ConnectionStatus` changes.

Screens can subscribe to these streams without implementing their own connection loops.

## Error and retry behavior

Polling errors transition the connection into an error/recovery path. Retry attempts are bounded and use an increasing delay based on the configured base retry duration.

The current service also supports manual refresh and reconnection through the centralized manager.

## Troubleshooting

When live data does not appear:

1. Confirm that the configured API URL or ESP32 address is reachable from the device running EcoGrid.
2. For local ESP32 access, verify that the phone/emulator and ESP32 are on a network path that permits direct communication.
3. Confirm that the endpoint returns valid JSON.
4. Check application logs for connection-state changes and polling errors.
5. If using an external web API from a web build, verify that its CORS configuration permits the client origin.
6. Do not place private API keys, Wi-Fi credentials, or signing secrets in source-controlled configuration.

## Historical note

Older repository documents described several experimental timeout values, polling frequencies, and performance benchmarks. Those files have been consolidated because some of those values no longer match the implementation. This document follows the current connection service and should be treated as the maintained reference.
