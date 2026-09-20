A guide on how to **download** and **install mods** in [R.E.P.O.](https://store.steampowered.com/app/3241660/REPO/) on PC, using [Thunderstore](https://thunderstore.io/c/repo/), [Vortex](https://www.nexusmods.com/about/vortex/), or no mod manager at all.

R.E.P.O. is a Unity game and its mods are [BepInEx](https://github.com/BepInEx/BepInEx) plugins. Almost everything lives on Thunderstore, and Nexus Mods carries a much smaller selection that Vortex can manage for you if that is the workflow you already know.

The example we install is [SharedHostUpgrades](https://thunderstore.io/c/repo/p/Schleimi/SharedHostUpgrades_by_Schleimi/), which shares upgrades across the whole crew instead of only the player who bought them.

[**View Guide On TMC (Recommended Due To Better Formatting)**](https://moddingcommunity.com/blog/how-to-install-mods-in-repo/)

## Table Of Contents
* [Requirements](#requirements)
* [Where R.E.P.O. Mods Come From](#where-repo-mods-come-from)
* [Finding Your Game Folder](#finding-your-game-folder)
* [Method 1 - Thunderstore Mod Manager](#method-1---thunderstore-mod-manager)
* [Method 2 - Gale](#method-2---gale)
* [Method 3 - Vortex](#method-3---vortex)
* [Method 4 - Manual](#method-4---manual)
* [Method 5 - The TMC App](#method-5---the-tmc-app)
* [Host And Client Mods](#host-and-client-mods)
* [Verifying The Install](#verifying-the-install)
* [Keeping Mods Updated](#keeping-mods-updated)
* [Uninstalling](#uninstalling)
* [Troubleshooting](#troubleshooting)
* [Conclusion](#conclusion)
* [See Also](#see-also)

## Requirements
* A PC running **Windows 10** or later, or **Linux**.
* **R.E.P.O.** on Steam.
* Around **500 MB** free for a typical mod list.
* [7-Zip](https://www.7-zip.org/) or similar if you go the manual route.

R.E.P.O. has no anti-cheat, so there is no ban risk in modding it.

## Where R.E.P.O. Mods Come From
Two places, and they are not equal in size.

**[Thunderstore](https://thunderstore.io/c/repo/)** is where essentially the whole scene is. Mods there are packaged with a machine-readable dependency list, which is why mod managers can install a mod and everything it needs in one click.

**[Nexus Mods](https://www.nexusmods.com/repo)** has a R.E.P.O. section and [Vortex](https://www.nexusmods.com/about/vortex/) supports it. The catalogue is far smaller and most authors do not mirror there, but if you already run Vortex for other games it is a perfectly reasonable place to manage what you do find.

Whichever you use, the loader underneath is the same: [BepInExPack](https://thunderstore.io/c/repo/p/BepInEx/BepInExPack/) hooks the game on launch and loads `.dll` plugins out of `BepInEx/plugins`.

## Finding Your Game Folder
You will want this for every method here, including the mod manager ones, if only for troubleshooting.

Right-click **R.E.P.O.** in your Steam library, then **Manage** followed by **Browse local files**. A default Windows install puts it at:

```
C:\Program Files (x86)\Steam\steamapps\common\REPO
```

You should see `REPO.exe` and `REPO_Data`. That is the folder BepInEx goes into.

## Method 1 - Thunderstore Mod Manager
The most common recommendation, and the one Thunderstore mod pages link to with their **Install with Mod Manager** button.

1. Install [Thunderstore Mod Manager](https://www.overwolf.com/app/Thunderstore-Thunderstore_Mod_Manager). It runs on Overwolf, so you will get that too.
2. Open it and pick **R.E.P.O.** from the game list.
3. Select a profile. **Default** is fine; a named profile per friend group is better once you have more than one mod list you care about.
4. Click **Get mods** and search for **SharedHostUpgrades**.
5. Click **Download**, then confirm the dependency dialog. BepInExPack comes with it.
6. Click **Start modded**.

**WARNING** - **Start modded** is the only launch that applies your mods. Starting R.E.P.O. from Steam runs it vanilla, and this catches almost everyone at least once.

## Method 2 - Gale
[Gale](https://thunderstore.io/c/repo/p/Kesomannen/GaleModManager/) does the same job in a smaller, faster app with no Overwolf requirement, and it has a proper Linux build.

1. Download Gale from [Thunderstore](https://thunderstore.io/c/repo/p/Kesomannen/GaleModManager/) or [GitHub](https://github.com/Kesomannen/gale/releases).
2. Launch it and select **R.E.P.O.**
3. Open **Browse mods**, find **SharedHostUpgrades**, and click **Install**.
4. Click **Launch game (modded)**.

Gale reads and writes the same profile codes as Thunderstore Mod Manager and r2modman, so mixing managers within a friend group is fine.

## Method 3 - Vortex
Worth using if Vortex is already your daily driver for Skyrim, Fallout or anything else. Bear in mind Vortex pulls from Nexus Mods, not Thunderstore, so the mod selection is different and SharedHostUpgrades is not necessarily there.

1. Install [Vortex](https://www.nexusmods.com/about/vortex/) and sign in to your Nexus Mods account.
2. Open the **Games** tab, search for **R.E.P.O.**, hover the tile and click **Manage**.
3. Vortex may prompt you to install its R.E.P.O. extension. Accept, then restart Vortex when it asks.
4. Install BepInEx first. Vortex will not do this for you, so follow the manual BepInEx steps below before installing plugins through Vortex.
5. Find a mod on [Nexus Mods](https://www.nexusmods.com/repo) and click **Mod Manager Download**, then **Install** and **Enable** in Vortex.
6. Launch the game from Vortex or from Steam. Vortex deploys files into the game folder directly rather than injecting at launch, so once BepInEx is in place, a normal Steam launch works.

**NOTE** - That last point is the real difference between Vortex and the Thunderstore managers. Vortex puts files on disk permanently; Thunderstore managers keep a profile outside the game folder and apply it per launch. Neither is wrong, but do not run both against the same install at once, because they will fight over `BepInEx/plugins`.

## Method 4 - Manual
Two stages, and the first one is a one-off.

**Install BepInEx:**

1. Open the [BepInExPack page](https://thunderstore.io/c/repo/p/BepInEx/BepInExPack/) and click **Manual Download**.
2. Extract the zip somewhere outside the game folder.
3. Open the extracted folder, then the `BepInExPack` folder inside it.
4. Copy the **contents** of `BepInExPack` into your R.E.P.O. folder, so `BepInEx`, `doorstop_config.ini` and `winhttp.dll` sit next to `REPO.exe`.
5. Start the game once and close it, which makes BepInEx build `BepInEx/plugins` and `BepInEx/config`.

**Install the mod:**

1. Open the [SharedHostUpgrades page](https://thunderstore.io/c/repo/p/Schleimi/SharedHostUpgrades_by_Schleimi/) and click **Manual Download**.
2. Extract the zip.
3. Copy the `.dll` into `REPO\BepInEx\plugins`.

The `manifest.json`, `icon.png` and `README.md` in the zip are Thunderstore packaging and can be left behind.

If you install manually, dependency handling is on you. Check the **Dependencies** section of the mod's Thunderstore page and install each entry at the version listed.

## Method 5 - The TMC App
Worth knowing about, with an honest caveat attached. [The TMC App](https://moddingcommunity.com/tmc-app) is our own mod manager and server browser. It does one-click installs, **sandboxes** (named mod profiles per game, each with its own load order and deployment method, switchable without re-downloading anything), a server browser with live latency graphs, and RCON.

**R.E.P.O. is not in its supported games list yet.** Adding a game is four JSON files and no code, so it is a small job rather than a rewrite, and it is on our list.

The caveat is that **the app is in very early development.** Its own README calls it partially tested and we are not going to oversell it here. For now it belongs alongside methods 1 to 4 rather than replacing any of them. If you are willing to try it anyway, that helps us a lot, and a report of what broke helps even more.

It is **open source** under GPL-3.0 at [github.com/modcommunity/tmc-app](https://github.com/modcommunity/tmc-app). Bugs and feature requests go in [the issue tracker](https://github.com/modcommunity/tmc-app/issues), pull requests are welcome, and the repository documents the per-game format if you want to add R.E.P.O. support yourself.

Installing it:

* **Linux**: one line, no root and no package manager.

```bash
curl -fsSL https://raw.githubusercontent.com/modcommunity/tmc-app/main/scripts/install.sh | sh
```

* **Windows**: the `setup.exe` or `setup.msi` from the [releases page](https://github.com/modcommunity/tmc-app/releases). There is a portable build too, though it does not register the launcher entry or the `tmc://` link handler.
* **macOS**: the `.dmg` from the same releases page.

## Host And Client Mods
R.E.P.O. is co-op, so this matters.

Mods fall into roughly three buckets:

| Type | Who needs it | Example |
| ---- | ------------ | ------- |
| Host only | Just the person hosting the lobby | Many rule and economy tweaks |
| Everyone | Every player in the lobby | Mods that add items, enemies or UI everyone sees |
| Client side | Only you | Cosmetics, camera tweaks, personal quality of life |

SharedHostUpgrades changes how upgrades are distributed across the crew, which is a shared-state change, so the whole lobby wants it.

The mod's Thunderstore description normally tells you which bucket it is in. When it does not, assume everyone needs it and export a profile for your group. Every Thunderstore manager can export a profile as a code or a file that the others import in one click.

## Verifying The Install
BepInEx opens a console window alongside the game. Watch it during startup and you will see each plugin get loaded by name and version.

No console at all means BepInEx is not loading. That is either a wrong folder layout or a launch that did not go through your mod manager.

For SharedHostUpgrades, host a lobby with someone else, buy an upgrade, and check whether it applied to both of you.

## Keeping Mods Updated
Thunderstore managers flag outdated mods and update them in a click. Vortex does the same for Nexus mods, showing an update indicator in the mods list.

Updating is worth doing after a game patch and worth avoiding mid-run, since a version change can invalidate a save or desync a lobby. If you want to test an update without risking a working setup, clone your profile and update the clone.

## Uninstalling
* **Thunderstore managers**: uninstall in the **Installed** list, or toggle the mod off to keep the files for later.
* **Vortex**: disable or remove the mod, then click **Purge Mods** under **Mods** to pull its files back out of the game folder.
* **Manually**: delete the `.dll` or folder from `BepInEx/plugins`.

To get back to a clean game, delete `BepInEx`, `doorstop_config.ini` and `winhttp.dll` from the game folder. Steam's **Verify integrity of game files** will not do it, since none of those came from Steam.

## Troubleshooting
**Game runs, no mods.** Launched from Steam rather than from the mod manager.

**No BepInEx console window.** BepInEx is not installed where it needs to be. `winhttp.dll` must sit directly beside `REPO.exe`.

**A mod loads for the host but nothing happens for other players.** It probably needs to be on every client. Check the mod page.

**Crash immediately after a game update.** R.E.P.O. patches break BepInEx mods regularly. Empty `BepInEx/plugins` to confirm, then wait for authors to catch up.

**Vortex and a Thunderstore manager are fighting.** Pick one. Purge Vortex's deployment or clear the Thunderstore profile, but do not run both against one install.

**Linux and Proton.** Set R.E.P.O.'s Steam launch options to `WINEDLLOVERRIDES="winhttp=n,b" %command%` so BepInEx gets loaded. Gale and r2modman do this for you when launching through them.

## Conclusion
For almost everyone, the answer is a Thunderstore manager: install it, pick R.E.P.O., download the mod with dependencies, and launch modded. Vortex is a reasonable choice if you already live in it, as long as you install BepInEx yourself first and do not mix the two approaches.

The co-op side is where a bit of care pays off. Work out whether a mod is host-only, client-side or needs to be everywhere, and share a profile with your group rather than comparing lists.

If you fancy helping with something, the [TMC App](https://github.com/modcommunity/tmc-app) is open source and early in development, and feedback on it is worth a lot to us.

## See Also
* [R.E.P.O. on Thunderstore](https://thunderstore.io/c/repo/)
* [R.E.P.O. on Nexus Mods](https://www.nexusmods.com/repo)
* [REPO Modding Discord](https://discord.gg/vPJtKhYAFe)
* [REPO Mods](https://repomods.com/)
* [TMC App](https://github.com/modcommunity/tmc-app)

We keep this guide as current as we can, but the game, BepInEx and the mod managers all update on their own schedules. If something here no longer matches what you see, please tell us or open a [pull request](https://github.com/modcommunity/how-to-install-mods-in-repo/pulls) on this guide's GitHub repository.

Join our [Discord server](https://discord.moddingcommunity.com) if you have any questions or need help with anything modding related!
