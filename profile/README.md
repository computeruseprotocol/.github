<p align="center">
  <a href="https://computeruseprotocol.com">
    <img src="assets/banner.png?v=2" alt="Computer Use Protocol" width="1200">
  </a>
</p>

<p align="center">
  A universal protocol for AI agents to perceive and interact with any desktop UI.
</p>

<p align="center">
  <a href="https://www.npmjs.com/package/computeruseprotocol"><img src="https://img.shields.io/npm/v/computeruseprotocol" alt="npm version"></a>
  <a href="https://pypi.org/project/computeruseprotocol/"><img src="https://img.shields.io/pypi/v/computeruseprotocol" alt="PyPI version"></a>
  <a href="https://github.com/computeruseprotocol/computer-use-protocol/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-MIT-blue" alt="MIT License"></a>
  <a href="https://computeruseprotocol.com"><img src="https://img.shields.io/badge/website-computeruseprotocol.com-green" alt="Website"></a>
</p>

---

Computer Use Protocol is a universal schema for representing UI accessibility trees, one format that works identically across Windows, macOS, Linux, Web, Android, and iOS. It includes a compact text encoding optimized for LLM context windows (~97% smaller than JSON), making it ideal for AI agents that need to perceive and act on desktop UIs.

## Why CUP?

Every platform exposes UI accessibility differently. Windows uses UIA with ~40 ControlTypes, macOS has AXUIElement with its own role system, Linux uses AT-SPI2 with 100+ roles, and the web has ~80 ARIA roles.

Today, every agent framework reinvents this translation layer independently. CUP solves it once at the representation level:

- **One format everywhere** - write agent logic once, run it on any platform
- **Built for LLMs** - compact encoding fits complex UIs into context windows at ~15x fewer tokens than the next closest format
- **Built for actions** - 15 canonical verbs that map to native platform APIs
- **No information loss** - raw native properties preserved via `node.platform.*`

## Compact Format

```
# CUP 0.1.0 | windows | 2560x1440
# app: Spotify
# 63 nodes (280 before pruning)

[e0] win "Spotify" 120,40 1680x1020
  [e1] doc "Spotify" 120,40 1680x1020
    [e2] btn "Back" 132,52 32x32 [clk]
    [e3] btn "Forward" 170,52 32x32 {dis} [clk]
    [e7] nav "Main" 120,88 240x972
      [e8] lnk "Home" 132,100 216x40 {sel} [clk]
```

```bash
pip install computeruseprotocol
npm install computeruseprotocol
```

## Repositories

| Repository | Description |
|-----------|-------------|
| [computer-use-protocol](https://github.com/computeruseprotocol/computer-use-protocol) | Protocol specification — JSON schema, role mappings, compact format spec |
| [python-sdk](https://github.com/computeruseprotocol/python-sdk) | Python SDK — tree capture, actions, MCP server |
| [typescript-sdk](https://github.com/computeruseprotocol/typescript-sdk) | TypeScript SDK — tree capture, actions, MCP server |

## SDKs

SDKs implement the protocol. They capture native accessibility trees, normalize them into CUP format, execute actions, and optionally expose everything through MCP servers for AI agent integration.

| Language | Package |
|----------|---------|
| Python | `pip install computeruseprotocol` |
| TypeScript | `npm install computeruseprotocol` |

Building your own SDK? All you need is the [spec](https://github.com/computeruseprotocol/computer-use-protocol). Implement tree capture for your target platform, normalize into the CUP schema, and you're compatible with every tool in the ecosystem.

## Contributing

CUP is in early development (v0.1.0). Contributions welcome — see the individual repos for guidelines.

## License

[MIT](https://github.com/computeruseprotocol/computer-use-protocol/blob/main/LICENSE)
