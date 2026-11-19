# FixYoutubeEmbeds Custom CSS

A custom CSS modification for Vencord's `FixYoutubeEmbeds` plugin. This patch injects custom styles directly into YouTube embed iframes, allowing the embedded player controls and volume slider to be customized.


 Volume Slider Fixes for Youtube Embeds on Discord
 
- Reverted back to horizontal volume bar
- Visibility toggle area for volume bar is much larger
- Volume bar pop out is closer to mute button
- Border-radius styling is removed
- Title font size is lowered to better fit embed sizes
- Closed caption button moved to top left

### Before
https://github.com/user-attachments/assets/38e2d49d-1b7e-4a21-8774-88bc9e97513d

### After
https://github.com/user-attachments/assets/9fd83451-4df2-4514-89b6-47fa8d3f9e5d

## Requirements

- Windows
- [Git](https://git-scm.com/downloads)
- [Node.js](https://nodejs.org/)
- [pnpm](https://pnpm.io/installation)
- An existing Discord installation

Verify the tools are installed by running:

```powershell
git --version
node --version
pnpm --version
```

## Installation

### 1. Download Vencord

Open PowerShell and navigate to your preferred download directory:

```powershell
cd H:\Downloads
```

Clone the Vencord repository:

```powershell
git clone https://github.com/Vendicated/Vencord Vencord-CustomCSS
```

Enter the new directory:

```powershell
cd .\Vencord-CustomCSS
```

### 2. Download the patch

Download the patch from this repository:

```powershell
Invoke-WebRequest "https://raw.githubusercontent.com/sanitysama/FixYoutubeEmbeds-CustomCSS/main/patches/fixYoutubeEmbeds.patch" -OutFile fixYoutubeEmbeds.patch
```

### 3. Check and apply the patch

First, check whether the patch applies cleanly:

```powershell
git apply --check .\fixYoutubeEmbeds.patch
```

If there are no errors, apply it:

```powershell
git apply .\fixYoutubeEmbeds.patch
```

**Important:** If the check reports an error, do not continue. The patch may need updating to match the current Vencord source.

### 4. Install dependencies

```powershell
pnpm install --frozen-lockfile
```

### 5. Build Vencord

```powershell
pnpm build
```

### 6. Install your custom build

Fully close Discord, including the system tray process.

Run:

```powershell
pnpm inject
```

Follow the installer prompts to patch your Discord installation.

Restart Discord when finished.

## Updating

When Vencord updates, you may need to download a fresh Vencord source checkout and reapply this patch.

Always check that the patch applies successfully before building.

## Uninstalling

From your Vencord source directory, run:

```powershell
pnpm uninject
```

This removes the custom Vencord installation from Discord.

## Files

- `youtube-embed.css` — Custom stylesheet.
- `patches/fixYoutubeEmbeds.patch` — Patch for Vencord's native `FixYoutubeEmbeds` implementation.

The patch currently contains an embedded copy of the stylesheet.
