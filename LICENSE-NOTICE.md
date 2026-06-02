# LICENSE-NOTICE — kinet-labs/pqclean

Snapshot of [PQClean/PQClean](https://github.com/PQClean/PQClean), the clean
post-quantum cryptography reference implementations curated for portability and
constant-time correctness.

| Field      | Value                                                    |
| ---------- | -------------------------------------------------------- |
| Upstream   | https://github.com/PQClean/PQClean                       |
| Snapshot   | master @ 3730b32a (snapshot taken 2026-04-28)            |
| License    | CC0-1.0 (Creative Commons Public Domain Dedication)      |
| SPDX       | `SPDX-License-Identifier: CC0-1.0`                       |
| Tag        | `v0.0.1-kinet-labs` (kinet-labs internal pin)                    |

## Why a fork

kinet-labs/crypto consumes specific PQClean parameter sets (SLH-DSA, ML-DSA, ML-KEM)
via FetchContent at a pinned tag. Forking guarantees:

1. Reproducibility — kinet-labs/crypto builds against an exact tree, never upstream HEAD.
2. Audit surface — any kinet-labs-side modification requires an explicit commit on this fork.
3. No dependency on upstream availability mid-CI.

## Tag policy

* Semver tags only: `vX.Y.Z` for stable upstream releases re-tagged with the
  same version, or `vX.Y.Z-kinet-labs` when the snapshot does not correspond to a
  named upstream release.
* No `latest` / no `main` consumption — kinet-labs/crypto pins by tag.
* New tags are cut only after KATs in kinet-labs/crypto pass against the new tree.

## Updating

1. `git fetch upstream master`
2. Audit the diff against upstream changelog.
3. Run kinet-labs/crypto KATs (`ctest -R 'slhdsa|mldsa|mlkem'`) against this branch.
4. Tag a new `vX.Y.Z` (or `vX.Y.Z-kinet-labs`) only after KATs pass.

Upstream tracks NIST PQC reference implementations. CC0 means "no rights
reserved" — no attribution requirement, but this notice exists so the
provenance is unambiguous.
