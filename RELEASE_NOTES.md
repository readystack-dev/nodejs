# Node.js 26.13.1 — ReadyStack release `26.13.1-CE-ubuntu24.04-r2`

Generated 2026-11-20 from this release's build records and strategy. Statements that come from a single record name it in brackets; the others come from this release's strategy and build log.

## Release

- **Image:** `readystack/nodejs:26.13.1-CE-ubuntu24.04-r2` (linux/amd64). Index digest `sha256:d2f9585a4bf8657015e83c4956ec840658c3565301beff06d3bdcf9522cc1de8` [`docs/provenance/LOCKED_DIGEST.txt`].
- **Image manifest digest:** `sha256:d61cd8ac183b8dc5c28c4446b8125cb1e64ad905bbf8991b5bfed5ee18bf8b2d` [`TARGET_DIGEST.txt`].
- **Upstream:** Node.js 26.13.1 built from source at `v26.13.1` of https://github.com/nodejs/node — upstream notes: https://github.com/nodejs/node/releases/tag/v26.13.1 [`docs/provenance/BUILD_RECIPE.json`].
- **Base image:** `ubuntu:24.04`; runtime user `node`.
- **Build:** `source-rebuild-c`, compiled offline with `--network=none`.
- **Supersedes:** ReadyStack release `26.13.1-CE-ubuntu24.04-r1`.

## What changed in this release

- Upstream version unchanged (26.13.1); ReadyStack rebuild.
- Node.js 26.13.1 is unchanged from the release this supersedes (26.13.1-CE-ubuntu24.04-r1); this release rebuilds it. Settings, ports and data volumes are those of 26.13.1-CE-ubuntu24.04-r1: replace the container with this image on the same volumes.

## Security status at release (measured 2026-11-20)

- **Docker Scout:** 0 fixable critical/high vulnerabilities; runs as `node` (non-root); SBOM + provenance attestations present (SPDX SBOM + SLSA v1) [`docs/provenance/SCOUT_VERDICT.json`].
- **OSV cross-check:** no fixable critical/high vulnerability beyond Docker Scout's findings.
- **Signature:** cosign signature verified by ReadyStack's release gate before publishing; check it yourself with `cosign verify --key https://readystack.dev/keys/cosign.pub readystack/nodejs:26.13.1-CE-ubuntu24.04-r2` (signatures are recorded in the public Sigstore transparency log).
- **ReadyStack release check at release:** passed (ReadyStack's own test, not a Docker Scout grade). Vulnerabilities are disclosed every day and the image never changes, so it is re-checked daily, beside Docker Scout's own dated grade, at https://readystack.dev/queue.

## Reproducibility

Rebuilds offline from this archive to the identical image digest `sha256:d61cd8ac183b8dc5c28c4446b8125cb1e64ad905bbf8991b5bfed5ee18bf8b2d`: run `./BUILD_OFFLINE.sh`, then `./VERIFY_OFFLINE.sh` (add `--online` to confirm the Docker Hub tag holds the same digest). Before publishing, ReadyStack rebuilt the kit with `./BUILD_OFFLINE.sh` and compared the result with the published digest [`docs/provenance/REPRO_VERIFICATION.json`], then ran `./BUILD_OFFLINE.sh` and `./VERIFY_OFFLINE.sh` from this archive (without `--online`).

## Validation

- 10 of 10 use cases passed (10 authored) against a container of this image started with `node -e setInterval(() => {}, 1 << 30)` after the image name instead of the image's default command (`node`) [`docs/validation/test-results.json`]. A container started the default way can answer differently.

## Known issues

- None found (reviewed by held semantic review (Claude) on 2026-11-20).

## Differences from upstream (by design)

- The upstream source is modified before the build (1 patch step) [`RSD-nodejs-292cc7475c`]

## Verify this archive

```
sha256sum -c CHECKSUMS.sha256
./BUILD_OFFLINE.sh && ./VERIFY_OFFLINE.sh --online
cosign verify --key https://readystack.dev/keys/cosign.pub readystack/nodejs:26.13.1-CE-ubuntu24.04-r2
```

ReadyStack records every signature in the public Sigstore transparency log (Rekor), so the command needs no extra flags.

