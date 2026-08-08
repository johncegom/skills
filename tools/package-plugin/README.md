# package-plugin

Zips this repo's git-tracked plugin files into a distributable
`<name>-<version>.plugin` archive, named from `.claude-plugin/plugin.json`.
Excludes repo-maintenance-only paths (`.github/`, `.claude/`, `tools/`) and
the marketplace-only `.claude-plugin/marketplace.json`.

## Usage

```
cd tools/package-plugin
go run . [output-dir]
```

`output-dir` defaults to `<repo-root>/dist` (git-ignored).

## Known caveat: `claude --plugin-dir <file>.plugin`

Claude Code's CLI can load a `.plugin` zip directly for a single session via
`claude --plugin-dir path/to/file.plugin`, but as of testing (Claude Code
2.1.226) this session-only zip loader reads the manifest but does **not**
discover the plugin's skills — even with an explicit `"skills"` array in
`plugin.json`. Unzipping the same archive to a real directory and pointing
`--plugin-dir` at that directory works correctly and loads every skill.

This is believed to be specific to the CLI's ad-hoc `--plugin-dir` zip
loader, not necessarily how Claude Desktop's "install plugin from file"
handles a `.plugin` archive (which almost certainly extracts it to disk
first, the same way a normal marketplace install does — the code path
already confirmed to work). If installing this package in Desktop still
doesn't surface skills, that would indicate the same limitation applies
there too, and is worth reporting upstream.
