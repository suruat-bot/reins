# ClawOpen - Project Plan

## Vision

ClawOpen is a multi-platform LLM chat app that seamlessly connects to both **local models** (via Ollama) and **cloud-backed AI** (via OpenClaw Gateway). Users get the best of both worlds: privacy-first local inference when available, and powerful cloud models when needed.

**Target platforms:** iOS, Android, macOS, Windows, Linux

## Why Fork Reins?

[Reins](https://github.com/ibrahimcetin/reins) is a polished, open-source Ollama client with:
- Clean Flutter codebase
- Multi-platform support
- Per-chat configurations (system prompts, model selection, options)
- Streaming, image support, multiple chat management
- Already on App Store and Flathub

Instead of building from scratch, we extend Reins to also support OpenClaw Gateway as a backend.

---

## Phased Development Plan

### Phase 1: Core OpenClaw Integration ✅ (In Progress)
**Goal:** OpenClaw Gateway works as a backend alongside Ollama.

- [x] Fork Reins codebase
- [x] Create `OpenClawService` (OpenAI-compatible API)
- [ ] Add connection type abstraction (Ollama vs OpenClaw)
- [ ] Settings UI: Add/edit OpenClaw connections
  - Gateway URL
  - Auth token
  - Agent ID (default: main)
- [ ] Connection test ("Test Connection" button)
- [ ] Switch between Ollama and OpenClaw in chat

**Deliverable:** Users can add an OpenClaw Gateway connection and chat with it.

---

### Phase 2: Multi-Connection Management
**Goal:** Manage multiple connections (multiple Ollama servers + multiple gateways).

- [ ] Connection list in Settings
- [ ] Add/edit/delete connections
- [ ] Connection types: Ollama (local/remote) or OpenClaw Gateway
- [ ] Per-chat connection selection
- [ ] Default connection preference
- [ ] Connection status indicators (online/offline)

**Deliverable:** Users can configure and switch between multiple backends.

---

### Phase 3: OpenClaw-Specific Features
**Goal:** Leverage OpenClaw Gateway's unique capabilities.

- [ ] Session management
  - Persistent session keys
  - Session history (if exposed by gateway)
- [ ] Agent selection
  - List available agents from gateway
  - Switch agents mid-conversation
- [ ] Node awareness (optional)
  - Show paired nodes status
  - Camera/screen capture from nodes (if permitted)
- [ ] Push notifications
  - Register for gateway push notifications
  - Background message delivery

**Deliverable:** Full OpenClaw Gateway feature integration.

---

### Phase 4: Branding & Polish
**Goal:** ClawOpen identity and app store readiness.

- [ ] Rename package: `dev.ibrahimcetin.reins` → `ai.clawopen.app`
- [ ] Update app name: "Reins" → "ClawOpen"
- [ ] New app icon and branding
- [ ] Update splash screen
- [ ] About page with credits (original Reins + OpenClaw)
- [ ] App Store metadata (screenshots, description)
- [ ] Privacy policy update

**Deliverable:** Publishable app with ClawOpen branding.

---

### Phase 5: Advanced Features (Future)
**Goal:** Power-user and enterprise features.

- [ ] Markdown rendering improvements
- [ ] Code syntax highlighting
- [ ] File attachments (documents, not just images)
- [ ] Voice input/output (TTS integration)
- [ ] Chat export (JSON, Markdown)
- [ ] Keyboard shortcuts (desktop)
- [ ] Widget support (iOS/Android home screen)
- [ ] Apple Watch / WearOS companion

---

## Architecture

```
lib/
├── Services/
│   ├── ollama_service.dart      # Ollama API (original)
│   ├── openclaw_service.dart    # OpenClaw Gateway API (new)
│   └── chat_service.dart        # Abstraction layer (TODO)
├── Models/
│   ├── connection.dart          # Connection config (TODO)
│   └── ...existing models...
├── Providers/
│   ├── connection_provider.dart # Manage connections (TODO)
│   └── ...existing providers...
├── Pages/
│   ├── settings/
│   │   └── connections_page.dart # Connection management (TODO)
│   └── ...existing pages...
└── main.dart
```

## Tech Stack

- **Framework:** Flutter
- **State Management:** Provider
- **Local Storage:** Hive (settings), SQLite (chat history)
- **Networking:** http package
- **Platforms:** iOS, Android, macOS, Windows, Linux, (Web possible)

## Repository

- **Origin:** https://github.com/suruat-bot/reins (to be renamed clawopen)
- **Upstream:** https://github.com/ibrahimcetin/reins (original Reins)

## Contributing

This is a fork of Reins. We maintain compatibility with upstream where possible and contribute back improvements that aren't OpenClaw-specific.

## License

GPL-3.0 (inherited from Reins)
