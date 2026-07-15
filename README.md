<div align="center">

# 📱 TikTok SSL Pinning Bypass

### See every request TikTok's Android app sends and receives. No root. No Frida CLI.


[![Android](https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white)](#)
[![Releases](https://img.shields.io/badge/Releases-181717?style=for-the-badge&logo=github&logoColor=white)](../../releases)
[![GPL-3.0](https://img.shields.io/badge/GPL--3.0-blue?style=for-the-badge&logo=gnu&logoColor=white)](LICENSE)
[![Telegram](https://img.shields.io/badge/Telegram-26A5E4?style=for-the-badge&logo=telegram&logoColor=white)](https://t.me/Aznannnnls1903l)


### 💬 [Questions or issues? Contact me on Telegram](https://t.me/Aznannnnls1903l)


## 🌟 Support the project

**If this project helped you, please consider [starring the repository](../../stargazers).**


☕ **Want to support the project even more?**

[![Buy Me A Coffee](https://img.shields.io/badge/Buy%20Me%20a%20Coffee-FFDD00?style=for-the-badge&logo=buymeacoffee&logoColor=000000)](https://buymeacoffee.com/labounq)

<sub>Your support helps keep this project maintained. Thank you! ❤️</sub>
</div>

</div>

---
<br>

## ✨ Features

| | |
|---|---|
| 🔓 | Bypasses TikTok's SSL pinning |
| 📡 | Inspect all HTTPS requests and responses in **mitmproxy** |
| 📦 | Ready-to-install patched APKs available in **Releases** |
| 🛠️ | Build your own patched APK for unsupported TikTok versions |
| 🤖 | Works on all Android versions |
| ✅ | No root required |
| ✅ | No Frida CLI required |

---
<br>

## 📸 Proof it works

<div align="center">

![mitmweb showing decrypted TikTok traffic](Screenshot.png)

</div>
<br>

---

## 📦 What's in this repo

| File | Purpose |
|---|---|
| [**🚀 Releases**](../../releases) | **Pre-built, ready-to-install patched APKs. Start here.** |
| [`patch_apk.py`](patch_apk.py) | Builds the patched APKs published in Releases |
| [`agent.js`](agent.js) | Embedded Frida script that disables SSL pinning and trust checks |

> [!NOTE]
> `patch_apk.py` and `agent.js` are only needed if you want to build your own APK (for example, for a TikTok version not yet available in Releases). If your version is already available, simply download the APK from **Releases** and skip them entirely.

> `patch_apk.py` requires a **single APK file**. It does **not** support split APKs (`base.apk` + config splits) exported from an Android App Bundle. Merge them first if needed.
<br>

---

# 🚀 Quick Start

> [!TIP]
> Your phone and computer must be connected to the **same Wi-Fi network**.

| Step | What to do |
|---|---|
| **1. Install mitmproxy** | `pip install mitmproxy` |
| **2. Launch the proxy** | Run `mitmweb`, then keep **http://127.0.0.1:8081** open. That's where TikTok's decrypted traffic will appear. |
| **3. Find your computer's local IP** | `Windows` → `ipconfig` (`IPv4 Address`)<br>`macOS` → `ipconfig getifaddr en0`<br>`Linux` → `hostname -I`<br><sub>Usually starts with `192.168.` or `10.`</sub> |
| **4. Configure the Wi-Fi proxy** | On your phone: `Settings → Wi-Fi → (long-press your network) → Modify network → Advanced options → Proxy → Manual` → **Hostname:** your computer's IP • **Port:** `8080` |
| **5. Install the mitmproxy certificate** | Visit **http://mitm.it** on your phone → **Android** → download the certificate → `Settings → Security → Encryption & credentials → Install a certificate → CA certificate` |
| **6. Install the patched APK** | Download the APK from **[Releases](../../releases)** and install it on your phone. |
| **7. Launch TikTok** | Open TikTok normally and watch requests appear live in **mitmweb**. |

> [!IMPORTANT]
> Uninstall the original TikTok app before installing the patched APK. Android won't install it over the official version because it is signed with a different key.
<br>
<br>

---

## 🛠️ Troubleshooting

**Is the patched APK working at all?** Connect your phone via USB with [ADB](https://developer.android.com/tools/adb) and run this **before** launching TikTok:

```bash
adb logcat -s TIKTOK_SSL_PINNING_BYPASS
```

Then launch TikTok.

- **Nothing appears at all** → the patch didn't take. Reinstall the APK from Releases, or re-patch it.
- **Lines like this appear** → it's working:

```
[*][*] Waiting for libttboringssl...
[*][+] Hooked checkTrustedRecursive
[*][+] Hooked SSLContextInit
[*][+] Found libttboringssl at: 0x756710b000
[*][+] Hooked function: SSL_CTX_set_custom_verify
```

| Problem | Solution |
|---|---|
| 🚫 No requests appear | Verify your phone and computer are connected to the same Wi-Fi network. |
| 📡 Other apps work, TikTok doesn't | Reinstall the mitmproxy certificate as an **Android CA certificate**, not just a Wi-Fi certificate. |
| 📦 "App not installed" | Uninstall the original TikTok app before installing the patched APK. |
---
<br>

## 🚀 Want to send your own TikTok requests?

Now that you can inspect TikTok's traffic, you've probably noticed that every request is protected by signatures such as **`X-Gorgon`**, **`X-Argus`**, **`X-Ladon`**, and **`X-Khronos`**.

If you're building a bot, scraper, automation tool, or your own TikTok API client, you'll need to generate valid signatures for every request.

> [!TIP]
> **Need a production-ready signer?**
>
> Generate valid TikTok signatures through the **TikTok Signer API** on RapidAPI:
>
> **👉 https://rapidapi.com/labouakileed122/api/tiktok-signer-working**
---
<br>

## 💬 Contact

Questions, issues, or feedback?

**👉 https://t.me/Aznannnnls1903l**

---
<br>

## ⚖️ Disclaimer

> [!WARNING]
> This project is intended for personal research, transparency, and educational purposes only. It allows you to inspect the network traffic generated by **your own installation of TikTok** on **your own device**.
>
> You are responsible for complying with TikTok's Terms of Service and all applicable laws. This project does **not** attack, modify, or compromise TikTok's servers or other users.
>
> **No warranty is provided. Use at your own risk.**

---
<br>

<div align="center">

## ❤️ Thanks for checking out the project!

If this project saved you time or was useful, you can support its development by starring the repository or buying me a coffee.

<br>

**⭐ [Star the repository](../../stargazers)** • **☕ [Buy me a coffee](https://buymeacoffee.com/labounq)** • **📦 [Releases](../../releases)** • **💬 [Telegram](https://t.me/Aznannnnls1903l)**

</div>

**GPL-3.0 License**

</div>
