# factorio-ghost-scanner-4

Originally based on https://github.com/Tiavor/GhostScanner2.

Ported to typescript for (my) ease of development.

Please open an issue if you have a problem.

## Features

- Scans ghost entities and tiles in logistic networks
- **Space Age Compatible**: Works on space platforms without requiring logistic networks
- Supports entity upgrades, cliff deconstruction, and item request proxies
- Quality-aware scanning

## Space Age Support

On space platforms (where roboports don't function), the scanner operates in a special mode:

- Scans a 100-tile radius around the scanner
- No logistic network required
- Works the same way as on regular surfaces otherwise

## Development

You'll need a node 22+ environment setup. VSCode is the recommended IDE.

### Setup

Run `corepack enable` to ensure you're using the correct yarn version.

Run `yarn` to install dependencies like the typescript-to-lua compiler and typed-factorio definitions.

### Recommended VSCode Extensions

- Factorio Modding Tool Kit (`justarandomgeek.factoriomod-debug`)
- Lua Language Server (`sumneko.lua`)
- Prettier (`esbenp.prettier-vscode`)

### Building

Run `yarn build` to build the mod `.zip` in the `build/` directory.

Run `yarn install_mod` to build and copy the mod to `~/AppData/Roaming/Factorio/mods`.

### Performance

This is a rough 1-to-1 port of GhostScanner2. In writing it, I've come to realize that there's a big opportunity for performance improvements if, instead of scanning for ghosts/related entities, the control script was reworked to be purely event driven when ghosts are created/built/deleted and scan only when logistic areas are created/updated/deleted.
