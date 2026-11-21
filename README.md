<p align="center">
  <img src="docs/logo.png" alt="TH Control" width="220">
</p>

<h1 align="center">TH Control</h1>

<p align="center">
  Hardware monitor, fan and power profiles, and network optimizer for gaming, in one dashboard.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Windows-10%20%7C%2011-0078D6?logo=windows" alt="Windows">
  <img src="https://img.shields.io/badge/.NET-8-512BD4?logo=dotnet" alt=".NET 8">
  <img src="https://img.shields.io/badge/license-MIT-green" alt="MIT License">
</p>

<p align="center"><a href="LEIAME.md">🇧🇷 Leia em português</a></p>

---

## ✨ Features

### 📊 Hardware monitor
- **Dashboard** with CPU (temperature, load, clock, power), GPU (temperature, hot spot, load, clock, power, VRAM), RAM, fans and drives
- **Chart** of CPU and GPU temperatures over the last 2 minutes
- **SSD/HDD health**: remaining life, temperature, total data written and used space
- **All sensors** (HWMonitor style) grouped by device, with current, minimum and maximum values
- Filter, reset min/max and export to CSV or TXT
- °C or °F and configurable refresh interval

### 🌀 Fans and power
- **Silent**, **Balanced** and **Performance** profiles (plus "System default")
- Each profile sets the Windows power plan, CPU limit, cooling policy and fan curve
- Performance uses the "Ultimate Performance" plan when it's available
- **Automatic curve**: fan speed follows temperature; above 90 °C fans go to 100% for safety
- Each fan can follow the profile, run at a manual speed (0–100%) or go back to BIOS control
- Fan control is handed back to the BIOS on exit (optional)
- Switch profiles from the tray icon

### 🌐 Network for gaming
- **Live ping** with chart, average, minimum, maximum, jitter and packet loss
- **One-click DNS switch**: Cloudflare, Google, Quad9, OpenDNS, AdGuard or automatic
- **DNS speed test** to find the fastest one for you
- **Tweaks**:
  - disable Nagle's algorithm (game packets are sent immediately)
  - turn off Windows network throttling
  - network priority (QoS) for the games you choose
- Real-time download/upload speed and connection details
- Flush DNS cache and reset the Windows network stack

### 🎨 Customization
- Dark, black and light themes, 8 color combos or your own colors, adjustable logo color
- Starts with Windows and lives in the tray

## ⚠️ Important limitations

- CPU temperature, motherboard sensors and fan control require the **PawnIO** driver. TH Control warns when it's missing and installs it through winget (`winget install PawnIO`).
- **Fan control** only works on motherboards and graphics cards that allow it. On laptops and many motherboards, control is locked by the BIOS or the manufacturer's app; in that case profiles only change power settings.
- Network tweaks **don't increase your internet plan's speed**. QoS priority depends on your router honoring the marking.
- The interface is currently in Portuguese.

## 📥 Download

Get the latest version from [**Releases**](https://github.com/Thiagosystems/THControl/releases).

> Requires the [.NET 8 Desktop Runtime](https://dotnet.microsoft.com/download/dotnet/8.0) (x64) and **administrator** permission.

## 🛠️ Build

Requirement: [.NET 8 SDK](https://dotnet.microsoft.com/download/dotnet/8.0)

```bat
git clone https://github.com/Thiagosystems/THControl.git
cd THControl
build.bat
```

The executable is created at `publish\THControl.exe`.

## 📁 Structure

| File | Purpose |
|---|---|
| `HardwareService.cs` | Sensor reading (LibreHardwareMonitor) |
| `FanAndPower.cs` | Power profiles and fan control |
| `NetworkTools.cs` | DNS, DNS test, tweaks and QoS |
| `Util.cs` | Commands, PawnIO and start with Windows |
| `ThemeManager.cs` | Themes and colors |
| `Settings.cs` | Settings (`%AppData%\THControl\settings.json`) |
| `MainWindow.xaml` | User interface |

## 📄 License

Distributed under the MIT License. See [LICENSE](LICENSE).

Uses the [LibreHardwareMonitor](https://github.com/LibreHardwareMonitor/LibreHardwareMonitor) library (MPL-2.0) and the [PawnIO](https://github.com/namazso/PawnIO.Setup) driver. See [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md).
