<p align="center">
  <a href="https://computeruseprotocol.com">
    <img src="assets/banner.png" alt="Computer Use Protocol">
  </a>
</p>

<p align="center">
  <b>A universal protocol for AI agents to perceive and interact with any desktop UI</b>
</p>

<br>

<p align="center">
  <a href="https://pypi.org/project/cup"><img src="https://img.shields.io/pypi/v/cup?style=for-the-badge&color=FF6F61&labelColor=000000" alt="PyPI"></a>
  <a href="https://github.com/computeruseprotocol/computer-use-protocol/blob/main/LICENSE"><img src="https://img.shields.io/badge/License-MIT-0cc0df?style=for-the-badge&labelColor=000000" alt="MIT License"></a>
  <a href="https://computeruseprotocol.com"><img src="https://img.shields.io/badge/Website-7ed957?style=for-the-badge&logo=google-chrome&logoColor=white&labelColor=000000" alt="Website"></a>
</p>

The Computer Use Protocol (CUP) is an open protocol that provides a universal way for AI agents to perceive and interact with any desktop UI. Every platform exposes accessibility differently — CUP unifies them into one schema, one format, and a set of language SDKs.

## The problem

Every platform exposes UI accessibility trees differently:

| Platform | API | Roles | IPC |
|----------|-----|-------|-----|
| Windows | UIA (COM) | ~40 ControlTypes | COM |
| macOS | AXUIElement | AXRole + AXSubrole | XPC / Mach |
| Linux | AT-SPI2 | ~100+ AtspiRole values | D-Bus |
| Web | ARIA | ~80 ARIA roles | In-process / CDP |
| Android | AccessibilityNodeInfo | Java class names | Binder |
| iOS | UIAccessibility | ~15 trait flags | In-process |

AI agents like Claude Computer Use, OpenAI CUA, and Microsoft UFO2 each independently reinvent UI perception. CUP solves this with one schema, one format, and a set of language SDKs.

## Quick start

```bash
pip install cup
```

```python
import cup

# Full accessibility tree as a CUP envelope (dict)
envelope = cup.get_tree()

# Just the foreground window
envelope = cup.get_foreground_tree()

# Compact text format — optimized for LLM context windows
text = cup.get_compact()
print(text)
```

Output (compact format):

```
# CUP 0.1.0 | windows | 2560x1440
# app: Discord
# 87 nodes (353 before pruning)

[e0] window "Discord" @509,62 1992x1274
    [e1] document "General | Lechownia" @509,62 1992x1274 {readonly}
        [e2] button "Back" @518,66 26x24 [click]
        [e3] button "Forward" @546,66 26x24 {disabled} [click]
        [e7] tree "Servers" @509,94 72x1242
            [e8] treeitem "Lechownia" @513,190 64x48 {selected} [click,select]
```

## Platform support

| Platform | Tree Capture | Actions |
|----------|-------------|---------|
| Windows | Stable | Stable |
| macOS | Stable | Planned |
| Linux | Stable | Planned |
| Web (Chrome) | Stable | Stable |
| Android | Planned | Planned |
| iOS | Planned | Planned |

## Schema

CUP defines a JSON envelope format built on ARIA roles:

- **54 ARIA-derived roles** — the universal subset that maps cleanly across all 6 platforms
- **16 state flags** — only truthy/active states are listed (absence = default)
- **15 canonical actions** — what can an agent *do* with this element?
- **Platform escape hatch** — raw native properties preserved in `node.platform.*` for advanced use

Full schema: [cup.schema.json](https://github.com/computeruseprotocol/computer-use-protocol/blob/main/schema/cup.schema.json) | Compact format: [compact.md](https://github.com/computeruseprotocol/computer-use-protocol/blob/main/schema/compact.md) | Role mappings: [mappings.json](https://github.com/computeruseprotocol/computer-use-protocol/blob/main/schema/mappings.json)

## Repositories

| Repository | Description |
|-----------|-------------|
| [computer-use-protocol](https://github.com/computeruseprotocol/computer-use-protocol) | Protocol specification, schema, and documentation |
| [python-sdk](https://github.com/computeruseprotocol/python-sdk) | Python SDK — `pip install cup` |

## Documentation

- **[Protocol Specification](https://github.com/computeruseprotocol/computer-use-protocol)** — Schema, roles, states, actions, compact format
- **[Python SDK](https://github.com/computeruseprotocol/python-sdk)** — Installation, API reference, MCP server
- **[API Reference](https://github.com/computeruseprotocol/python-sdk/blob/main/docs/api-reference.md)** — Session API, actions, envelope format

## Contributing

CUP is in early development (v0.1.0). Contributions welcome:

- **Specification** — role/action proposals, schema improvements, platform mappings → [computer-use-protocol](https://github.com/computeruseprotocol/computer-use-protocol/blob/main/CONTRIBUTING.md)
- **Python SDK** — platform adapters, action execution, tests → [python-sdk](https://github.com/computeruseprotocol/python-sdk/blob/main/CONTRIBUTING.md)
- **New language SDKs** — TypeScript, Go, Rust, and more

## License

[MIT](https://github.com/computeruseprotocol/computer-use-protocol/blob/main/LICENSE)
