# ☁️ WebDAV ⇄ ♻️ GDrive Sync

[![Open In Colab]([https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/everarpitraj/webdav-gdrive-sync/blob/main/WebDAV_Sync.ipynb](https://colab.research.google.com/drive/10XApHmm2s2f3EEBdHWairLHIigmBdM6p?usp=sharing))
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)

A secure Google Colab notebook for syncing files from any WebDAV cloud storage to Google Drive using Rclone with a dark-themed interactive file browser.

## ✨ Features

- 🔐 **Secure Credentials**: Uses Colab Secrets - no credentials in code
- 🔄 **Multi-Provider Support**: Works with PikPak, Nextcloud, OwnCloud, Seafile, Yandex.Disk
- 🎨 **Dark Mode UI**: Beautiful interactive file browser with custom styling
- 📊 **Real-time Progress**: Live transfer statistics and folder size calculation
- ✅ **Dual Verification**: Summary + deep integrity checks with size matching
- 🚀 **Optimized Transfers**: 8 parallel connections, 16 checkers
- 📂 **Smart Browsing**: Pre-calculates folder sizes before selection

## 🚀 Quick Start

### Prerequisites

- Google account with Google Drive
- WebDAV-enabled cloud storage account
- WebDAV credentials (username & password)

### Step 1: Add Credentials to Colab Secrets

1. Open the notebook in Colab (click badge above)
2. Click **🔑 Secrets** icon in the left sidebar
3. Add two secrets:
   - **Name:** `WEBDAV_USER` → **Value:** Your WebDAV username/email
   - **Name:** `WEBDAV_PASS` → **Value:** Your WebDAV password
4. **Toggle access** to grant notebook permission

### Step 2: Configure Your Server

Update the `WEBDAV_HOST` parameter in the first cell:

```
WEBDAV_HOST = "your-webdav-server-url"
```

#### Supported Providers

| Provider | URL Format |
|----------|------------|
| **PikPak** | `https://dav.mypikpak.com` |
| **Nextcloud** | `https://nextcloud.example.com/remote.php/dav/` |
| **OwnCloud** | `https://owncloud.example.com/remote.php/dav/` |
| **Seafile** | `https://seafile.example.com/` |
| **Yandex.Disk** | `https://webdav.yandex.com/` |

### Step 3: Run & Sync

1. Run all cells (Runtime → Run all)
2. Authorize Google Drive access
3. Use the interactive browser:
   - **Blue buttons** → Open folders
   - **Orange "Select"** → Choose folder to transfer
   - **Green "Start Transfer"** → Begin sync
   - **".. (Up)"** → Go back to parent folder

## 📋 How It Works

1. **Auto-Setup**: Installs Rclone & WebDAV client
2. **Secure Connect**: Fetches credentials from Colab Secrets
3. **Mount Drive**: Connects to your Google Drive
4. **Browse**: Interactive UI displays your files with sizes
5. **Transfer**: Rclone copies with multi-threading
6. **Verify**: Two-stage integrity validation

## ⚙️ Technical Details

### Dependencies
- **Rclone** (v1.65+): High-performance file transfer utility
- **webdavclient3** (3.14.6+): Python WebDAV client library
- **ipywidgets** (8.0+): Interactive UI components

### Transfer Configuration
```
--transfers 8        # 8 parallel file transfers
--checkers 16        # 16 parallel integrity checkers
--ignore-existing    # Skip files already in destination
--progress          # Real-time progress display
--stats 1s          # Update stats every second
```

### Verification Process
1. **Summary Check**: Compares total size & file count
2. **Deep Check**: Validates each file individually using `rclone check --size-only`

## 🎯 Use Cases

- Regular backups of cloud storage to Google Drive
- Migrating between cloud providers
- Archiving important files with verification
- Automated sync workflows in free Colab environment
- Multi-provider consolidation to single Drive

## 🔒 Security Features

✅ **No credentials in code** - Uses Colab Secrets API  
✅ **Safe to share publicly** - Repository contains no sensitive data  
✅ **Password obscuring** - Rclone encrypts passwords in config  
✅ **No logging** - Credentials never printed to output  

## ⚠️ Important Notes

- **Session Limits**: Colab disconnects after 90 minutes of inactivity
- **Storage Space**: Ensure sufficient Google Drive quota
- **Transfer Speed**: Depends on your internet bandwidth and Colab's connection
- **Large Folders**: Size calculation may take time for folders with thousands of files
- **Terms of Service**: Comply with both WebDAV provider and Google Drive ToS

## 🤝 Contributing

Contributions welcome! Please:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- [Rclone](https://rclone.org/) - Powerful rsync for cloud storage
- Google Colab - Free GPU/TPU computing resources
- WebDAV protocol community

## 📧 Support

- 🐛 **Bug Reports**: [Open an Issue](https://github.com/everarpitraj/webdav-gdrive-sync/issues)
- 💡 **Feature Requests**: [Start a Discussion](https://github.com/everarpitraj/webdav-gdrive-sync/discussions)
- ❓ **Questions**: Check [existing issues](https://github.com/everarpitraj/webdav-gdrive-sync/issues?q=label%3Aquestion)

---

**⚡ Made with ❤️ for the cloud storage community**
