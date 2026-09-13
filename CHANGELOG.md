# Changelog

All notable changes to the Relay Client Obsidian plugin project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [0.8.12-openrelay] - 2026-09-12

### Added
- **Direct Email & Password Authentication (`src/LoginManager.ts`, `src/components/LoggedIn.svelte`)**:
  - Implemented `loginWithPassword(identity, password)` and `registerWithPassword(email, password, name)`.
  - Added inline login and registration forms directly in the plugin settings view.
  - Added a "⚙️ Configure Relay Server" modal dialog for easy endpoint entry.
- **Self-Hosted Endpoints Support (`src/EndpointManager.ts`)**:
  - Unlocked `http://` and `https://` protocols for custom control planes and relay servers across all release flavors.
  - Bypassed proprietary RSA JWT license validation checks against `api.system3.md`.
- **Folder Privacy Toggling (`src/components/ManageRemoteFolder.svelte`)**:
  - Added a **"Make public"** action button alongside "Make private" to allow folder owners to toggle shared folder visibility for all relay members.
- **Immediate Vault Attachment Sync (`src/components/Relays.svelte`)**:
  - Trigger `void folder.connect()` and `plugin.sharedFolders.notifyListeners()` immediately upon confirming "Add to vault", connecting the folder instantly without requiring a note open or app reload.
  - Added descriptive guidance when remote folders exist on a relay but require public access or role assignment.

### Fixed
- **Defensive Role & User Lookups (`src/RelayManager.ts`)**:
  - Resolved `Uncaught Error: Unable to find user: <id>` when secondary accounts join relays by returning graceful fallback user representations if PocketBase synchronization lags.
  - Resolved `Uncaught Error: invalid role: unable to find relay <id> on role <id>` by making `RelayRoleAuto`, `FolderRoleAuto`, `RemoteFolderAuto`, and `RelayInvitationAuto` defensive against transient unpopulated relations.
  - Fixed `RemoteFolderAuto.get permissionParents()` to ensure folder creators always retain permission management access to their own folders.
- **Missing Policy Definition (`src/PolicyManager.ts`)**:
  - Registered missing `["folder", "manage_users"]` policy rule in `PolicyManager.ts` to allow folder creators and owners to manage collaborators without policy evaluation exceptions.
- **Role Synchronization**:
  - Added `"roles"` collection synchronization to ensure role IDs map correctly to PocketBase definitions.
  - Added real-time user record fetching on SSE role change notifications.

### Security
- Removed third-party tracking, proprietary telemetry, and license phone-home checks.
- All communications route strictly to the user-configured self-hosted Open-Relay Control Plane and Relay Server.
