# Bun peer deps resolution failing

The CI of this repo will fail as long as Bun don't segregate the installation of dependencies (peer deps auto installed in this example).

Root pkg depends on:

- `pkg1` -> [`./apps/pkg1`](./apps/pkg1/package.json) which has `{"ethers": "5"}` as `peerDependencies`
- `pkg2` -> [`./apps/pkg2`](./apps/pkg2/package.json) which has `{"ethers": "6"}` as `peerDependencies`

The packages `pkg1` and `pkg2` use `ethers` in an incompatible way, because `pkg2` uses a breaking change from `ethers@v6`[^ethers-breaking-change].

[^ethers-breaking-change]: https://docs.ethers.org/v6/migrating/
