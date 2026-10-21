# Repository map workflow

For every repository exploration or implementation request, identify the active repository or repositories and check the persistent map cache before reading source files.

- For this repository, check `agent-cache/maps/wealth-ops.md`; if it exists, read and reuse it.
- For cross-repository work involving `wealthops-ai-be` or `wealthops-ai-web`, query each relevant repository's committed `graphify-out/graph.json` instead of loading entire graphs. Check staleness and incrementally update with Graphify when needed. Use the compact platform workspace map for deployment/configuration exploration.
- For work across repositories, check `agent-cache/workspace/workspace-map.md` and read only the maps for relevant repositories.
- If a required map is missing, use the installed `codebase-navigation` skill or the sibling `wealthops-ai-agent-skills/tools/code_map.py` utility to generate and save it in `agent-cache/`, then read it before exploring source. Keep generated maps untracked and never commit them.
- Regenerate only when missing, clearly stale after structural changes, or explicitly requested. Confirm current behavior against source and tests.
- If the skill or generator is unavailable, report that; do not claim a map was checked or generated.
