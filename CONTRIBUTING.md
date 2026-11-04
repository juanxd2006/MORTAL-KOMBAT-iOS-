<!-- coderabbit-ai-generated:v1 -->

# Contributing

This port is experimental. Focused fixes with reproducible evidence are welcome.

## Reporting an issue

Include the source commit, workflow ID, device model, iOS version, game edition/version and exact reproduction steps. For a crash, include the newest matching MK9 `.ips` report and relevant startup log lines. Remove personal paths, identifiers and download links before posting. Do not upload game files, shader captures or signing material to public issues.

For rendering/input/audio reports, distinguish what is visible from what responds correctly. State whether the problem occurs at startup, menus or gameplay, and whether a physical controller was connected.

## Making a change

1. Read [Architecture](docs/ARCHITECTURE.md) and the relevant tests before changing renderer or SDK conventions.
2. Keep SDK patches anchored, repeatable and reversible where their existing interface supports it.
3. Preserve the shader resource ABI, metadata specialization and cache identity rules. Invalidate caches deliberately when compiler inputs change.
4. Add focused tests for behavior changes and run the source checks in the README. Tests requiring external pinned sources report a skip when unavailable; list those limits in the change description.
5. Validate runtime changes with a macOS IPA build and a physical device when available. A Linux fixture test cannot establish correct Metal rendering or sound.

Use `tools/ios/mk9-nx.pin` and `plume-metal.pin` to identify the source revisions used by the build. Optional integration test fixtures can be selected using `MK9_UPSTREAM_APP`, `MK9_UPSTREAM_GPU`, `MK9_UPSTREAM_SDK` and `MK9_PLUME_METAL_SOURCE`; point them to the corresponding pinned trees.

## Repository hygiene

Commit source and synthetic test fixtures only. Keep `default.xex`, extracted game assets, generated C++, IPAs, metallibs, caches and signing identities out of Git. Never use `git add -f` to bypass these exclusions. Run `python3 tools/ios/check_public_tree.py` after staging your change.

Preserve the GPL license and third-party notices. Avoid broad changes to retained SDK compatibility paths unless the active build and affected consumers are checked.
