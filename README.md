# Minecraft Server Manager (Google Colab / Jupyter)

Run a PaperMC Minecraft server directly from a Jupyter notebook -- Google Colab, Replit, or any Linux environment with Python 3.

## Quick Start

1. Open `minecraft_server_colab.ipynb` in Google Colab (or any Jupyter-compatible environment).
2. Run **Cell 1** to set up the environment.
3. Run **Cell 2** to create a new server or load an existing one.
4. Run **Cell 3** to start the server and interact via the built-in console.
5. *(Optional)* Run **Cell 4** to edit `server.properties` in the browser.

## Features

- **PaperMC integration** -- automatically fetches the latest stable build for any supported Minecraft version.
- **Automatic Java installation** -- detects the required Java version (11, 17, or 21) and installs it via `apt-get` if needed.
- **Interactive console** -- send commands, view server output, and use quick-action buttons (list players, set time, weather, etc.).
- **Server manager** -- create multiple named servers, each with its own world and configuration.
- **Settings editor** -- edit `server.properties` directly in the notebook UI.
- **SHA-256 verification** -- downloaded JARs are verified against PaperMC's published checksums.
- **Aikar's JVM flags** -- optimised garbage-collection flags are applied automatically.

## File Structure

```
MinecraftServers/
  <ServerName>/
    paper-<version>-<build>.jar
    server.properties
    eula.txt
    .mc_meta.json          # metadata (MC version, Java version, JAR name)
    world/                 # Minecraft world data
    plugins/               # drop plugin JARs here
```

All server files live in the `MinecraftServers/` directory next to the notebook.

## Connecting to the Server

The Minecraft server listens on port **25565**. In cloud/notebook environments you need a TCP tunnel to connect from outside:

- [playit.gg](https://playit.gg) -- free, no account required
- [ngrok](https://ngrok.com) -- `ngrok tcp 25565`

## FAQ

| Question | Answer |
|---|---|
| **Where are my worlds?** | `MinecraftServers/<name>/world/` |
| **How do I change RAM?** | RAM is auto-detected (75% of system memory, max 8 GB). Override by editing `_detect_ram()` in Cell 2 |
| **How do I install plugins?** | Drop `.jar` files into `MinecraftServers/<name>/plugins/`, then restart |
| **online-mode=false?** | Lets non-premium accounts join. Change it in Cell 4 |
| **Multiple servers?** | Create each with a different name and set a different `server-port` in Cell 4 |

## Requirements

- Python 3.7+
- `requests`, `ipywidgets` (pre-installed on Google Colab)
- Internet connection (to download PaperMC builds and Java)

## License

See [LICENSE](LICENSE) for details.
