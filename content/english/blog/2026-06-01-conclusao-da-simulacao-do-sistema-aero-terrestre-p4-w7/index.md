---
title: "Simulation Complete: Full Aerial–Ground Mesh Validated (P4-W7) - Jun 1, 2026"
date: 2026-06-01T18:00:00Z
image: "images/blog/sim-hq-console.png"
image_webp: "images/blog/sim-hq-console.png"
---

The end-to-end simulation of the aerial–ground search-and-rescue system is finished, and it validated the architecture we set out to prove.

The final lab runs real OpenWrt nodes inside Docker-hosted QEMU VMs. They speak Babel IPv6 mesh routing with wireless ETX metrics, and links are impaired using the Al-Hourani 2014 air-to-ground excess loss model — so the radio behaviour reflects realistic conditions rather than ideal ones.

UAV relays navigate autonomously via `pic-gossip`, planning their positions from a minimum spanning tree (MST) of the active ground nodes. They now decide when to return to HQ based on whether they have enough energy to actually make it back, not just a fixed battery percentage — a static 10% threshold was not sufficient for longer deployments.

Ground teams launch from HQ, walk to their assigned destinations, and report position over telemetry. The HQ dashboard above reflects live topology, alerts, and mission state. Push-to-talk voice probes validate the Murmur path over the mesh, end to end.

## What the simulation validated

- **Babel convergence and route stability** under RF impairment
- **UAV relay chain planning** with a backhaul safety margin
- **Energy-aware return-to-home** triggered by distance, not just battery percentage
- **Voice delivery** within the ≤30 ms jitter and ≤5% loss acceptance thresholds

That last point held up under inspection: a per-node voice quality test reports the Murmur service running, a present and stable route, 0% packet loss, and jitter well inside budget.

{{< img-small "sim-voice-test.png" "Per-node voice quality test: PASS — Murmur up, route present and stable, 0% loss, jitter ~1.6 ms." "340px" >}}

With the simulation closed out, the next step is carrying these results into the physical prototype and confirming the same margins hold on real hardware.
