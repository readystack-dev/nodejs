# Provenance — Node.js (`26.13.1-CE-ubuntu24.04-r2`)

Every item below is copied from a record in this archive; the record is named in brackets.

## Source

- Upstream repository: https://github.com/nodejs/node
- Revision built: `v26.13.1` (commit `e9c277643b0249c50f6e6de5413be8a88ea11b6a`)
- Source tree: `93bab83f1af3497de22f540b555e1936607b01ce148ef482172182a4e1cc8a01` over 52300 files [`docs/provenance/SOURCE_TREE_HASH.json`]
- Community Edition only: enterprise code is removed or refused before the build (CE audit at acquire).

## Build

- Method: `source-rebuild-c`; base image `ubuntu:24.04`
- Compiled with `--network=none` from vendored source, dependencies and base images; BuildKit pinned to `moby/buildkit:v0.31.2` (shipped in `toolchain/`).
- SOURCE_DATE_EPOCH: `1795159451` [`SOURCE_DATE_EPOCH.txt`]
- Frozen inputs: [`docs/provenance/FREEZE_MANIFEST.json`], build recipe: [`docs/provenance/BUILD_RECIPE.json`].

## Output

- Published image: `readystack/nodejs:26.13.1-CE-ubuntu24.04-r2` — index digest `sha256:d2f9585a4bf8657015e83c4956ec840658c3565301beff06d3bdcf9522cc1de8` [`docs/provenance/LOCKED_DIGEST.txt`]
- linux/amd64 image digest `sha256:d61cd8ac183b8dc5c28c4446b8125cb1e64ad905bbf8991b5bfed5ee18bf8b2d` — reproduced from this archive before publishing [`docs/provenance/REPRO_VERIFICATION.json`].

## Attestations and signature

- SBOM + SLSA provenance attached to the image: attached: an SPDX SBOM and SLSA v1 provenance [`docs/provenance/SCOUT_VERDICT.json`]
- cosign signature by the ReadyStack release key: verified before publishing. Check it: `cosign verify --key https://readystack.dev/keys/cosign.pub readystack/nodejs:26.13.1-CE-ubuntu24.04-r2`

## Pinned inputs, and why

- 15 pinned inputs, each with where it came from, why this one, how it was checked and when it was decided: `docs/PINS.md` [`docs/provenance/PINS.json`] (upstream source 2, base and build images 3, image digests 1, dependency versions readystack sets 2, components from other repositories 2, pins in the kit's dockerfiles 2, readystack's build engine 1, dependencies upstream chose 2).

## Build trail

- How this release passed through the ReadyStack harness, record by record (every chain, drive, stage, review round, defect and check, each naming the record it is copied from): `ReadyStack-nodejs-26.13.1-CE-ubuntu24.04-r2.trail.json`, published beside this archive and signed with the release key (`ReadyStack-nodejs-26.13.1-CE-ubuntu24.04-r2.trail.json.sigstore`), and readable at https://readystack.dev/products/nodejs/trail/26.13.1-CE-ubuntu24.04-r2.

