<div align="center">

# setup-rokit


[![Latest Release](https://img.shields.io/github/v/release/ThatTimothy/setup-rokit?style=for-the-badge)](https://github.com/ThatTimothy/setup-rokit/releases/latest)
[![Star](https://img.shields.io/github/stars/ThatTimothy/setup-rokit?style=for-the-badge)](https://github.com/ThatTimothy/setup-rokit)
[![Issues](https://img.shields.io/github/issues-pr/ThatTimothy/setup-rokit?style=for-the-badge)](https://github.com/ThatTimothy/setup-rokit/issues)

A quick & optimized action to setup [Rokit](https://github.com/rojo-rbx/rokit)

</div>

----

## Usage

Quick & easy:

```yaml
- uses: ThatTimothy/setup-rokit@v1
```

Full options:

```yaml
- uses: ThatTimothy/setup-rokit@v1
  with:
    token: ${{ github.token }}
    cache: true
    working-directory: .
```

| Input               | Description                                                                | Default               |
| ------------------- | -------------------------------------------------------------------------- | --------------------- |
| `token`             | GitHub token for authenticated requests (prevents aggressive ratelimiting) | `${{ github.token }}` |
| `cache`             | Whether to cache Rokit and tools                                           | `true`                |
| `working-directory` | Directory containing `rokit.toml`                                          | `.`                   |

*Note: this action is intended for linux-based GitHub Actions runners - if you need support for another OS feel free to make a issue/PR*

## Motivation

When looking for an action, several exist, but they do not cover the following criteria that I wanted:
- Speed. This action takes 1-2s for my workflow (With/without caching), while others I tried took upwards of 5s.
- Properly use token for all requests (initial download of rokit + rokit installed tools) to prevent ratelimiting
  - 60 downloads per hour unauthenticated on GitHub, which can be blown through easily due to how rokit works
- Properly cache both rokit and rokit installed tools
  - Some of the actions I looked at only cache one or the other
- Script based action instead of slower node-based action
  - While functionality correct, launching node for an action adds ~2 seconds for spin-up which matters a lot for a setup action

## Contributing

If you find anything I missed, feel free to open an issue/PR!

## License

[Licensed under MIT](./LICENSE.md)
