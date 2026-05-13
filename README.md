# Oh My Posh - Paladin173 Theme

Custom Oh My Posh theme for PowerShell and WSL/Linux.

Theme includes:

* Multi-line prompt
* Shell indicator
* Time/date
* CPU/RAM usage
* Execution timing
* Clean path display
* Powerline separators
* Nerd Font support

---

# Requirements

Install:

* PowerShell 7+
* Oh My Posh
* Nerd Font
* Windows Terminal (recommended)

Recommended font:

* CaskaydiaCove Nerd Font
* MesloLGM Nerd Font

---

# Windows PowerShell Setup

Run this entire block in PowerShell:

```powershell
winget install JanDeDobbeleer.OhMyPosh --source winget

oh-my-posh font install CascadiaCode

if (-not (Test-Path "$HOME\.poshthemes"))
{
    New-Item -ItemType Directory -Path "$HOME\.poshthemes" | Out-Null
}

Invoke-WebRequest `
    -Uri "https://raw.githubusercontent.com/Paladin173/ohmyposh-paladin173/main/paladin173.json" `
    -OutFile "$HOME\.poshthemes\paladin173.json"

# Shared profile location based on actual PowerShell profile path
$ProfileDirectory = Split-Path $PROFILE
$SharedProfile = Join-Path $ProfileDirectory "paladin173.ps1"

'oh-my-posh init pwsh --config "$HOME\.poshthemes\paladin173.json" | Invoke-Expression' | Set-Content $SharedProfile

# PowerShell 7 profile
if (-not (Test-Path $PROFILE))
{
    New-Item -ItemType File -Path $PROFILE -Force | Out-Null
}

". `"$SharedProfile`"" | Set-Content $PROFILE

# Windows PowerShell 5.1 profile
$WinPSProfile = Join-Path ([Environment]::GetFolderPath("MyDocuments")) "WindowsPowerShell\Microsoft.PowerShell_profile.ps1"

if (-not (Test-Path (Split-Path $WinPSProfile)))
{
    New-Item -ItemType Directory -Path (Split-Path $WinPSProfile) -Force | Out-Null
}

if (-not (Test-Path $WinPSProfile))
{
    New-Item -ItemType File -Path $WinPSProfile -Force | Out-Null
}

". `"$SharedProfile`"" | Set-Content $WinPSProfile

Write-Host ""
Write-Host "Theme installed successfully."
Write-Host "Set Windows Terminal font to: CaskaydiaCove Nerd Font"
Write-Host "Restart PowerShell or Windows Terminal."
```



Then:

1. Restart Windows Terminal
2. Set font to:
   `CaskaydiaCove Nerd Font`

---

# WSL / Ubuntu Setup

Run this entire block in WSL Ubuntu:

```bash
sudo apt update && sudo apt install unzip curl -y

curl -s https://ohmyposh.dev/install.sh | bash -s

mkdir -p ~/.poshthemes

curl -o ~/.poshthemes/paladin173.json \
https://raw.githubusercontent.com/Paladin173/ohmyposh-paladin173/main/paladin173.json

echo 'export PATH=$PATH:~/.local/bin' >> ~/.bashrc

cat > ~/.poshthemes/paladin173.sh << 'EOF'
eval "$(oh-my-posh init bash --config ~/.poshthemes/paladin173.json)"
EOF

grep -qxF 'source ~/.poshthemes/paladin173.sh' ~/.bashrc || \
echo 'source ~/.poshthemes/paladin173.sh' >> ~/.bashrc

exec bash
```


Then:

1. Open Windows Terminal settings
2. Select your Ubuntu/WSL profile
3. Set font to:
   `CaskaydiaCove Nerd Font`

---

# Repository

```text
https://github.com/Paladin173/ohmyposh-paladin173
```

---

# Preview

```text
   10:07:46 PM | Tuesday    CPU: 89% | RAM: 27/31GB   171ms 
╭─  pwsh   D:  Projects 
╰─
```
