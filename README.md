**gh-heatmap** is a powerful Bash script to visualize Git commit activity as a calendar heatmap. Developed by [Cipher Shad0w (Jannis Krija)](https://github.com/cipher-shad0w).

![Sample Output](https://via.placeholder.com/800x200.png?text=Sample+Heatmap+Output)

## ✨ Features

- **Calendar Heatmap** with daily commit visualization
- **Multiple Themes** (dark/light/8colors)
- **Customizable Display**:
  - Cell width (2-3 characters)
  - Week start day (Mon-Sun)
  - Month gaps
  - Breakpoint multiplier
- **Filtering**:
  - Author/committer regex filtering
  - Year range limit
  - Show commit counts
- **Smart Formatting**:
  - Automatic year gaps
  - Responsive layout
  - Legend system
- **Multi-configuration**:
  - System/user config files
  - Environment variable support

## 📦 Installation

1. **Download script**:
```bash
wget https://github.com/cipher-shad0w/gh-heatmap -O ~/bin/gh-heatmap
```

2. **Make executable**:
```bash
chmod +x ~/bin/gh-heatmap
```

3. **Verify dependencies**:
- Bash 5+
- Git 2.20+
- GNU Core Utilities

## 🚀 Basic Usage

```bash
gh-heatmap [OPTIONS] [REPOSITORY_PATH]
```

**Example**: Basic execution in current directory  
```bash
gh-heatmap
```

**Example**: Last 3 years with legend  
```bash
gh-heatmap -y3 -l
```

## 🔧 Options Overview

| Option | Description |
|--------|-------------|
| `-a PATTERN` | Filter commits by author (regex) |
| `-b MULTIPLIER` | Breakpoint multiplier (1-10) |
| `-c` | Show commit counts in cells |
| `-d` | Display days of month |
| `-e` | Hide empty years |
| `-g GAP` | Month gap spacing (0-32) |
| `-l` | Show legend |
| `-s START_DAY` | Week start (1=Mon, 7=Sun) |
| `-t THEME` | Select theme (dark/light/8colors) |
| `-w WIDTH` | Cell width (2-3) |
| `-y YEARS` | Number of years to show |


## � Configuration

### Config Files
1. **System-wide**: `/etc/gh-heatmap/config.conf`
2. **User-specific**: `$XDG_CONFIG_HOME/gh-heatmap/config.conf`

**Example config**:
```bash
# Theme settings
config_theme_name="light"
config_show_legend=true
config_cell_width=3

# Filter options
config_authors=("john|jane")
config_years=5
```

### Theme Development
Themes are defined as associative arrays:
```bash
declare -A theme_custom=(
    [color_breakpoints]="0 2 5 10"
    [color_commits]="\e[35m \e[36m \e[37m"
    [symbol_has_commits]="▇ "
)
```

## 🛠️ Troubleshooting

**Common Errors**:
```bash
# Old Bash version
Error: Your bash version (4.4.20) is outdated.

# Invalid repository
Error: Directory is not a git repository

# Theme error
Error: Theme "space" doesn't exist
```

**Solutions**:
1. Update Bash:
```bash
sudo apt update && sudo apt upgrade bash
```

2. Verify Git repo:
```bash
git -C /path rev-parse
```

## 🤝 Contributors

- **Jannis Krija (Cipher Shad0w)** - Sole Developer  
[![GitHub](https://img.shields.io/badge/GitHub-Profile-blue?logo=github)](https://github.com/cipher-shad0w)

## 📜 License

This project is licensed under the [MIT License](LICENSE).