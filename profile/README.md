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
  <a href="https://pypi.org/project/computeruseprotocol"><img src="https://img.shields.io/pypi/v/computeruseprotocol?style=for-the-badge&color=FF6F61&labelColor=000000&label=PyPI&v=1" alt="PyPI"></a>
  <a href="https://www.npmjs.com/package/computeruseprotocol"><img src="https://img.shields.io/npm/v/computeruseprotocol?style=for-the-badge&color=CB3837&labelColor=000000&label=npm" alt="npm"></a>
  <a href="https://github.com/computeruseprotocol/computeruseprotocol/blob/main/LICENSE"><img src="https://img.shields.io/badge/License-MIT-0cc0df?style=for-the-badge&labelColor=000000" alt="MIT License"></a>
  <a href="https://computeruseprotocol.com"><img src="https://img.shields.io/badge/Website-7ed957?style=for-the-badge&logo=google-chrome&logoColor=white&labelColor=000000" alt="Website"></a>
</p>

Every platform exposes UI accessibility trees differently — Windows uses UIA, macOS uses AXUIElement, Linux uses AT-SPI2, the web uses ARIA. AI agents like Claude Computer Use, OpenAI CUA, and Microsoft UFO2 each independently reinvent UI perception. CUP unifies them into one schema, one format, and a set of language SDKs.

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
| [computeruseprotocol](https://github.com/computeruseprotocol/computeruseprotocol) | Protocol specification — schema, roles, states, actions, compact format |
| [python-sdk](https://github.com/computeruseprotocol/python-sdk) | Python SDK — tree capture, actions, MCP server |
| [typescript-sdk](https://github.com/computeruseprotocol/typescript-sdk) | TypeScript SDK — tree capture, actions, MCP server |

## Contributing

CUP is in early development (v0.1.0). Contributions welcome — see the individual repos for guidelines.

## License

[MIT](https://github.com/computeruseprotocol/computeruseprotocol/blob/main/LICENSE)
