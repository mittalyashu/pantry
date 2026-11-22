# AGENTS: pantry

Public repository for package recipes and metadata.

## Core Commands

It's possible one of these commands might not be installed on this machine, in that case prefix it with `pkgx`.

When `dev` is not integrated (i.e. `bk` is not on your `PATH`), run brewkit through pkgx from inside this checkout. With pkgx v2, pkgx does not apply the `env:` block in `pkgx.yaml`, so brewkit falls back to the global pantry (which may not contain the package you are working on). Point both pantry variables at this checkout:

```sh
cd /path/to/pantry
PKGX_PANTRY_DIR="$PWD" PKGX_PANTRY_PATH="$PWD" pkgx bk build <pkg>
PKGX_PANTRY_DIR="$PWD" PKGX_PANTRY_PATH="$PWD" pkgx bk test <pkg>
PKGX_PANTRY_DIR="$PWD" PKGX_PANTRY_PATH="$PWD" pkgx bk audit <pkg>
```

Both are required with pkgx v2.x + brewkit v1.x:
- `PKGX_PANTRY_PATH` lets brewkit resolve `<pkg>` against the local pantry.
- `PKGX_PANTRY_DIR` lets pkgx itself use the local pantry when building the test environment.

(With pkgx v1 only `PKGX_PANTRY_PATH` was needed; pkgx v2 reads `PKGX_PANTRY_DIR` instead, but brewkit still needs `PKGX_PANTRY_PATH`.)

- `dev`
- `bk build <pkg>`
- `bk test <pkg>`
- `bk audit <pkg>`

## Always Do

- Keep package recipes reproducible and auditable.
- Validate changed package recipes with build, test, and audit.
- Keep recipe metadata and tests aligned.

## Ask First

- Bulk recipe rewrites.
- Workflow changes that affect packaging/release pipelines.

## Never Do

- Never merge changed package recipes without at least one successful test path.
- Never include internal-only environment details in public recipe docs.
