# 🇮🇳 India IPTV Playlist Generator

Auto-generates categorized India IPTV playlists with EPG by scraping IPTVCat — runs automatically via GitHub Actions every 6 hours.

---

## 🚀 Quick Setup (5 Minutes)

### 1. Fork this Repository
Click **Fork** → name it whatever you like (e.g., `india-iptv`) → keep it **Private**.

### 2. Enable GitHub Actions
Go to your repo → **Actions** tab → click **"I understand my workflows, go ahead and enable them"**

### 3. (Optional) Set Up Geo-Bypass
For geo-blocked channels, add secrets in **Settings → Secrets → Actions**:

| Secret | Value |
|--------|-------|
| `CLOUDFLARE_WORKER_URL` | Your CF Worker URL (see [VPN Guide](docs/vpn_setup.md)) |
| `PROXY_URL` | Your proxy URL (optional alternative) |

### 4. Run the Workflow
Go to **Actions → Generate India IPTV Playlist → Run workflow**

### 5. Use Your Playlist
After the workflow completes, your playlist URL will be:
```
https://raw.githubusercontent.com/YOUR_USERNAME/YOUR_REPO/main/output/india_iptv.m3u
```

---

## 📺 Adding to Your IPTV Player

### IPTV Smarters Pro / TiviMate / OTT Navigator
1. Add playlist → **M3U URL** → paste your raw URL above
2. EPG URL: `https://epgshare01.online/epgshare01/epg_ripper_IN1.xml.gz`

### VLC
Media → Open Network Stream → paste M3U URL

### Kodi
1. Install **PVR IPTV Simple Client**
2. Set M3U URL and EPG URL in addon settings

### Smart TV (Samsung/LG/Android TV)
Use **Smart IPTV** or **IPTV Smarters** app with the M3U URL.

---

## 📡 EPG Sources

| Source | URL |
|--------|-----|
| Primary | `https://epgshare01.online/epgshare01/epg_ripper_IN1.xml.gz` |
| Secondary | `https://www.open-epg.com/files/india1.xml` |
| Tertiary | `https://raw.githubusercontent.com/iptv-org/epg/gh-pages/guides/in.epg.xml` |

---

## 📂 Channel Categories

| Category | Description |
|----------|-------------|
| 📰 News | NDTV, Aaj Tak, Republic, Times Now, India Today... |
| 🎬 Entertainment | Star Plus, Zee TV, Sony, Colors, SAB... |
| 🎥 Movies | Star Gold, Zee Cinema, Sony Max, B4U Movies... |
| ⚽ Sports | Star Sports, Sony Six, Sony Ten, DD Sports... |
| 👶 Kids | Disney, Nick, Cartoon Network, Pogo, Hungama... |
| 🎵 Music | MTV, VH1, 9XM, Zing, B4U Music... |
| 🙏 Devotional | Aastha, Sanskar, Ishwar, Peace... |
| 🗺️ Regional - Tamil | Sun TV, Vijay, Kalaignar, ZEE Tamil... |
| 🗺️ Regional - Telugu | Gemini, MAA TV, ZEE Telugu, ETV... |
| 🗺️ Regional - Malayalam | Asianet, Surya, Mazhavil, Flowers... |
| 🗺️ Regional - Kannada | Star Suvarna, ZEE Kannada, Colors Kannada... |
| 🗺️ Regional - Bengali | Star Jalsha, ZEE Bangla, Sony Aath... |
| 🗺️ Regional - Marathi | Star Pravah, ZEE Marathi, Colors Marathi... |
| 🌍 Infotainment | Discovery, Nat Geo, History TV18, Animal Planet... |
| 🌏 English | BBC, CNN, Star World, Fox... |

---

## 🌐 Geo-Blocked Channel Bypass

The generator automatically detects and routes geo-blocked streams through your configured proxy.

See the **[Geo-Bypass Setup Guide](docs/vpn_setup.md)** for detailed instructions on:
- **Cloudflare Worker** (FREE, recommended)
- **Personal VPS Proxy**
- **WireGuard VPN** (best for all devices)
- **Streamlink + Proxy** (local playback)

---

## 🔧 Local Usage

```bash
# Clone and install
git clone https://github.com/YOUR_USERNAME/YOUR_REPO.git
cd YOUR_REPO
pip install -r requirements.txt

# Generate playlist
python main.py

# With more pages
python main.py --pages 10

# Include offline channels
python main.py --all

# Enable proxy for geo-blocked channels
CLOUDFLARE_WORKER_URL=https://your.worker.dev python main.py
```

---

## ⚙️ Schedule

The workflow runs automatically every **6 hours**. You can change this in `.github/workflows/generate_playlist.yml`:

```yaml
schedule:
  - cron: '0 */6 * * *'   # every 6 hours
  # - cron: '0 */12 * * *' # every 12 hours
  # - cron: '0 2 * * *'    # daily at 2 AM UTC
```

---

## ⚠️ Disclaimer

This tool is for **personal use only**. It scrapes publicly available IPTV stream links from IPTVCat.com. Respect copyright laws in your country. The developer is not responsible for any misuse.

---

*Last updated by bot. See [Actions](../../actions) for run history.*
