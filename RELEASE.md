# Release checklist

1. [ ] Create a new _"Release v{VERSION}"_ issue with this checklist
  - `$ cat RELEASE.md | sd '\{VERSION\}' '{NEW_VERSION}' | xclip -sel clip`
  - Create the issue in GitHub
1. [ ] Ensure that all entries in the man page are up to date
  - Manually verify with the entries in `xtask/src/gen.rs`
1. [ ] Regenerate static assets
  - `$ cargo xtask gen`
1. [ ] Update `rust-version` in `Cargo.toml`
  - `$ cargo msrv --min 1.40 -- cargo check`
1. [ ] Bump `version` in `Cargo.toml`
1. [ ] Update the `CHANGELOG.md`
1. [ ] Merge changes through a PR to make sure that CI passes
1. [ ] Publish on [crates.io](crates.io)
  - `$ cargo publish`
1. [ ] Publish on GitHub by pushing a version tag
  - Make sure the branch you're on is fully up to date
  - `$ git tag v{VERSION}`
  - `$ git push upstream/origin v{VERSION}`
1. [ ] Make a release announcement on GitHub after the release workflow finishes
