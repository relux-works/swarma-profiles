# Swarma profiles

Curator profiles for the roles of the Swarma platform.

- `swarma-core` is the base profile that every platform role extends. It carries the shared context modules and skill dependencies, including Swarm Memory.
- Role profiles extend the base: lead, orchestrator, producer, reviewer, keeper.

Profiles are installed with Curator (`curator profile install`). A profile declares context modules and skill dependencies; it never ships runtime hooks. Hooks are delivered by the operator, pinned by digest.

Changes go through pull requests with review. Commits are signed.

## License

Apache-2.0. See `LICENSE` and `NOTICE`.
