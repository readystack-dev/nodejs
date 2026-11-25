# Node.js: ReadyStack build kit

The offline build kit for the Docker image `readystack/nodejs:26.13.1-CE-ubuntu24.04-r2`. It holds what the image is built from (upstream source, base images, toolchain, pinned dependencies) and the documents, so the image can be rebuilt with no network access (`docker build --network=none`).

- Release: [26.13.1-CE-ubuntu24.04-r2](https://github.com/readystack-dev/nodejs/releases/tag/26.13.1-CE-ubuntu24.04-r2)
- Image: [`docker.io/readystack/nodejs:26.13.1-CE-ubuntu24.04-r2`](https://hub.docker.com/r/readystack/nodejs/tags), manifest digest `sha256:d61cd8ac183b8dc5c28c4446b8125cb1e64ad905bbf8991b5bfed5ee18bf8b2d`
- Product page: https://readystack.dev/products/nodejs
- Source and build recipe: https://readystack.dev/products/nodejs/recipe
- Build trail: https://readystack.dev/products/nodejs/trail/26.13.1-CE-ubuntu24.04-r2
- Defects: this repository's Issues (defects recorded from 25 November 2026 on) and https://readystack.dev/defects.html?product=nodejs

## The image

A language runtime image: use it as the FROM base of your own image, or run a script with `docker run --rm`. It runs no service.

## This release

- Docker Scout policy grade at release: **A** (94%), graded 2026-11-20 with `docker scout policy` (CLI 1.26.0, docker-default configuration).
  - Docker Scout counts 83 packages with copyleft licences (GPL, LGPL, MPL), all of them operating-system packages (it counts only packages whose licence it can read; the SBOM lists every component).
- Signed with ReadyStack's release key (fingerprint `04daa92344a52dbc`): https://readystack.dev/keys/cosign.pub.
- Runs as a non-root user (`node`).
- Attestations on the image: an SPDX SBOM and SLSA provenance v1.
- Rebuilt from this kit with network egress blocked on 2026-11-20; the rebuilt image digest is the published one.
- Base: Ubuntu 24.04.

The current grade, measured again every day, is on https://readystack.dev/products/nodejs.

Node.js is distributed under its upstream licence (MIT); the kit contains upstream's source under that licence, and each vendored component under its own.

## Download

From the [26.13.1-CE-ubuntu24.04-r2 release](https://github.com/readystack-dev/nodejs/releases/tag/26.13.1-CE-ubuntu24.04-r2): `ReadyStack-nodejs-26.13.1-CE-ubuntu24.04-r2.tar.gz` (503.0 MB), SHA-256 `5c15821dc565df9e79d5c150a2d8337940552e49df256cce8d46e9558a986cc4`.

```sh
sha256sum --check --ignore-missing SHA256SUMS
```

## Verify and rebuild

The rebuild statement is signed with the ReadyStack release key. Check the signature before you rely on it:

```sh
cosign verify-blob --key https://readystack.dev/keys/cosign.pub \
  --bundle ReadyStack-nodejs-26.13.1-CE-ubuntu24.04-r2.rebuild.json.sigstore ReadyStack-nodejs-26.13.1-CE-ubuntu24.04-r2.rebuild.json
```

Unpack with `-p` so file modes are kept, then follow the kit's own README.md and docs/REBUILD.md:

```sh
tar -xpzf ReadyStack-nodejs-26.13.1-CE-ubuntu24.04-r2.tar.gz
cd 26.13.1-CE-ubuntu24.04-r2
less README.md docs/REBUILD.md
```

The build trail (`ReadyStack-nodejs-26.13.1-CE-ubuntu24.04-r2.trail.json`, signed the same way, and its Markdown copy) records how this release was built and checked.

## This repository

`recipe/` holds the kit's recipe files (Dockerfiles, build scripts, pins) as published at https://readystack.dev/products/nodejs/recipe. The complete kit is the release download. Each release is a tag here.

— ReadyStack · https://readystack.dev
