# jamazan fork of SecKatie/ha-wyzeapi

Based on upstream v0.1.41 (Apache-2.0). Merged open upstream PRs:

| PR | What | Notes |
|----|------|-------|
| #928 | IoT3 support for DX locks (Lock Bolt v2, Palm Lock) | merged as-is |
| #907 | Robot vacuum (JA_RO2) | fixed for HA 2026.11: removed `VacuumEntityFeature.BATTERY`; battery is now an attribute plus a battery sensor |
| #895 | Wyze Scale sensors | sensor additions re-applied cleanly on top of #928/#907; missing asyncio markers added to its tests |
| #936 | WebRTC signaling / snapshot reliability | its third-party `wyzeapy` git pin (diogormendes fork, commit not found) was NOT taken |

Library: `wyzeapy` fork (jamazan/wyzeapy) = wyzeapy main (0.8.1) + wyzeapy #325 (vacuum) + #311 (scale).
The manifest pins it to one full commit SHA.

Local hardening: snapshot URLs must be https; TURN credentials no longer written to debug logs;
per-stream WebRTC "connected" log lowered from WARNING to INFO.

Not covered by tests: camera/WebRTC code, and none of the vacuum, scale or DX-lock code has run against real devices.
