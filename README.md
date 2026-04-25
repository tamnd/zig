# zig (tamnd mirror)

Daily GitHub mirror of [codeberg.org/ziglang/zig](https://codeberg.org/ziglang/zig), the Zig compiler.

The original `ziglang/zig` GitHub repo has been frozen with the description "Moved to Codeberg" and no longer receives updates. This mirror exists so tamnd/* projects (and anything else that needs a current GitHub-hosted Zig source) can fetch the latest commits without leaving GitHub.

## Layout

- `main` holds this README and the sync workflow. It is not a checkout of Zig.
- `upstream/master` tracks upstream's `master` branch.
- `upstream/<branch>` mirrors every other upstream branch.
- Tags (`0.13.0`, `0.14.0`, and so on) mirror from upstream as-is.

If you want a checkout of the Zig source, fetch a tag or the `upstream/master` branch.

## Sync

`.github/workflows/mirror.yml` runs every day at 06:00 UTC. It clones upstream as a bare repo and force-pushes every branch under `refs/heads/upstream/*` and every tag 1:1 to this repo.

Some upstream tags include workflow files under `.github/workflows/`. The default `GITHUB_TOKEN` cannot push refs that contain workflow files. To get those refs synced as well, create a Personal Access Token with the `workflow` scope and add it to this repo's secrets as `MIRROR_PAT`. Without it, the affected refs are skipped silently by GitHub's permission check; everything else syncs fine.

## License

Zig is licensed under MIT by the Zig Software Foundation. See the LICENSE file inside any tag or the `upstream/master` branch.
