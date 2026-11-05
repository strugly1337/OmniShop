### Features

- **Shop stall block.** Place it and a red-robed shopkeeper drops from the sky. He is invulnerable, ignored by mobs and always stays at his stall.
- **Every item.** The shop automatically lists all items from Minecraft and every installed mod. Creative-only items (spawn eggs, spawners, command blocks) are hidden.
- **Automatic prices.**
  - An item costs the value of its ingredients through every vanilla and modded recipe.
  - Modded materials without recipes are valued by the gear made from them.
  - Whole-coin prices; selling pays half the buy price.
  - No profit from buy → craft → sell.
- **Coin wallet.** Coins are a balance shown in the GUI, not an inventory item. Ways to earn:
  - **structure chests**, including modded structures;
  - **mobs**: peaceful ~10, zombie ~100, strong modded ~1000, bosses ~10,000+;
  - **selling** items in the shop.
- **Handy GUI.** Search (`@mod` filters by mod), sorting by price, rarity, name and mod, selling one item or every identical one at once.

### Recipe

```
Iron Ingot | White Wool | Emerald
Red Wool   | Diamond    | Red Wool
Stick      | Gold Ingot | Stick
```

### Installation

| Loader | Version | Dependencies |
|---|---|---|
| NeoForge | 21.1+ | — |
| Forge | 52.1+ | — |
| Fabric | Loader 0.16+ | [Fabric API](https://modrinth.com/mod/fabric-api); [Mod Menu](https://modrinth.com/mod/modmenu) optional |

Required on **both the server and the client**.

### Config & commands

All settings live in `config/omnishop.json` and can also be edited in-game via the mod's config button (Fabric: through Mod Menu). They cover:
- the price multiplier;
- chest coin chance and amounts;
- mob and boss rewards;
- hidden items;
- manual item prices.

| Command | Description |
|---|---|
| `/omnishop reload` | Reload settings and recalculate prices |
| `/omnishop coins get <player>` | Show a balance |
| `/omnishop coins set <player> <amount>` | Set a balance |
| `/omnishop coins add <player> <amount>` | Add or remove coins |

Commands require operator permission level 2.

### Reporting bugs

Open an [issue](../../issues) and include:
- your loader and its version;
- the OmniShop version;
- your mod list;
- the crash report or `latest.log`.

---

## Building from source

The project is a multi-loader setup: one shared codebase plus thin loader modules.

```
common/     shared code and assets (vanilla Minecraft API only)
neoforge/   NeoForge entry point, events, networking, wallet storage
forge/      Forge entry point, events, networking, wallet storage
fabric/     Fabric entry point, events, networking, mixins, Mod Menu integration
```

Each loader folder is a standalone Gradle project that compiles `common/` together with its own sources.
JDK 21 is required:

```bash
cd neoforge   # or forge / fabric
./gradlew build
```

The jar ends up in `<loader>/build/libs/`.

## License

[MIT](LICENSE)
