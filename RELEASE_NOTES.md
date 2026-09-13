# Release Notes: Relay Client Obsidian Plugin (Open-Relay Edition)

**Release Date:** September 12, 2026  
**Plugin Version:** `0.8.12-openrelay`  
**Compatibility:** Obsidian v1.6.6+  
**License:** MIT  

---

## Overview

This release of the **Relay Client Obsidian Plugin** removes proprietary licensing locks, introduces native email/password authentication, and provides complete support for self-hosted Open-Relay backends.

---

## Key Highlights

### 1. Unlocked Endpoint Configuration
- Connect to any self-hosted Open-Relay control plane over `http://` or `https://`.
- Removed proprietary license checks that prevented connections to custom servers.
- Configure endpoints with a single click using the **⚙️ Configure Relay Server** button in settings.

### 2. Built-in Account Creation & Login
- Sign up and log in directly in Obsidian using email and password.
- No need for complex OAuth setup or external authentication gateways for self-hosted users.

### 3. Folder Privacy & Sharing Controls
- Easily toggle folders between **Public** (available to all relay members) and **Private** (restricted to invited members).
- Creators always retain full control over their folders.

### 4. Resilient Real-Time Syncing
- Defensive entity resolution prevents client crashes during multi-user onboarding and real-time collaboration.
- Newly added shared folders connect immediately and begin syncing notes without requiring an app reload.

---

## Installation & Setup

1. Copy `main.js`, `manifest.json`, and `styles.css` from the `Relay/` directory into your vault:
   ```text
   <Your-Vault>/.obsidian/plugins/open-relay-client/
   ```
2. In Obsidian, go to **Settings $\rightarrow$ Community Plugins** and enable **Relay**.
3. In **Settings $\rightarrow$ Relay**, click **⚙️ Configure Relay Server** and set your Control Plane URL (e.g. `http://localhost:8090` or your LAN IP `http://192.168.1.x:8090`).
4. Register or log in with your credentials.
