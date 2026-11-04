# Synthetic GitHub protected-merge acceptance

**Fixture only. No native Mac tests or production privacy qualification are claimed.**

The corrected PR-HEAD / strict-current-base profile produced **11 actual blocked
merge attempts (HTTP405)** and **2 genuinely accepted merges (HTTP200)**.
Both required contexts retained their real App identities:
`Publication privacy (all new commits)` — Actions15368;
`HyperCI / Mac relay` — Reporter5612385.
Protection included administrators, strict current-base checks and no force
pushes/deletions. This is a stronger proposed policy than existing production.

## Accepted controls

| Fixture PR | Approved HEAD | Base | Actual merge |
| --- | --- | --- | --- |
| 24 | `589f0c5496616f557a85c620c5e7c2c7e6e47fa9` | `03c29dd7c63971229712ab7e5477a25779ae333c` | `b14df33f001624ee72daf9e3b9a6c5dad33ff799` |
| 23, renewed | `9c1eebf365ce29c89b2f37f32925b5d4febce072` | `b14df33f001624ee72daf9e3b9a6c5dad33ff799` | `48642ecbf48e2f108d24c994ec1596ceff781fb8` |

Checks126748533438 and126752041810 were genuine Reporter5612385 successes;
genuine Actions15368 privacy successes were present. Actual merged Trees equal
the approved candidate Trees, with the expected Base/Head parents.

## Stale-candidate controls

PR22: new HEAD `075985a3e6b331aebb4024941e6acf32ac98349e` was blocked despite
old-HEAD success126739590059. PR23: old HEAD
`1d47b488e07cb820151907f66931733da8cc9747` had genuine green checks, including
Reporter126748442563, but was blocked after main advanced to `b14df33f001624ee72daf9e3b9a6c5dad33ff799`.
The old local approval was invalidated independently of cached PR metadata.
A fresh Head containing the new Base, fresh approval and fresh checks then merged.

The other nine rejected cases cover missing, wrong-App/same-name, controller
absence, pending, failed/cancelled lanes, wrong nonce/run/lane. All decisions,
check IDs/App IDs, evaluated SHAs, effective rules, Trees and parents are in:

- [Full merge-decision receipt](pr-head-strict-v1.json)
- [Head/Base/test-merge bindings and invalidated approvals](candidate-bindings-v1.json)

The initial test-merge-SHA profile failed its positive control (PR12) and remains
recorded as failure. It does not count toward acceptance. A skipped Actions job
with the relay's name was never treated as a valid Reporter success.

GitHub validates context/App/SHA/conclusion, not nonce/run/lane semantics. Those
bindings must be enforced by the trusted controller. This receipt qualifies the
synthetic fixture policy, not the uninstalled production controller or a release.
