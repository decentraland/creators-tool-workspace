# Decentraland Creators Tool Workspace

A unified workspace containing the creator-facing tools and libraries for the Decentraland platform. This repository uses **Git Submodules** to aggregate multiple repositories, making it easier to work across projects during development.

For creator documentation, see the [Decentraland Creator Docs](https://docs.decentraland.org/creator/).

---

## 📦 Submodules Overview

### Builder Ecosystem (Web)

Web-based scene and wearable editor.

| Submodule | Description |
|-----------|-------------|
| **[builder](builder/)** | Web frontend — drag-and-drop 3D editor for scenes and wearables |
| **[builder-server](builder-server/)** | Backend API — persistence, authentication, and curation workflows |
| **[builder-client](builder-client/)** | Programmatic SDK — TypeScript client for interacting with builder-server |
| **[wearable-preview](wearable-preview/)** | 3D preview — renders wearables and emotes, embedded via iframe in builder |

```
Builder (UI) ←→ Builder Server (API) ←→ Builder Client 
                      ↕
              Wearable Preview (iframe)
```

### Creator Hub & SDK (Desktop)

Desktop application + development toolchain + deployments.

| Submodule | Description |
|-----------|-------------|
| **[creator-hub](creator-hub/)** | Electron app — desktop environment for creating and deploying scenes |
| **[js-sdk-toolchain](js-sdk-toolchain/)** | SDK7 — ECS, CLI, compilation, and development commands |
| **[linker-dapp](linker-dapp/)** | Deployment dApp — web GUI for deploying scenes to LAND/Worlds, managing ACLs and storage |

```
Creator Hub (Desktop) → js-sdk-toolchain (SDK + CLI)
                              ↓
                     linker-dapp (Deploy GUI)
                              ↓
                     World content server / Catalyst
```

### Shared Libraries

Cross-cutting libraries used by both ecosystems.

| Submodule | Description |
|-----------|-------------|
| **[urn-resolver](urn-resolver/)** | Resolves Decentraland asset URNs to content server URLs (`@dcl/urn-resolver`) |
| **[gltf-validator-ts](gltf-validator-ts/)** | Validates glTF/GLB 3D models against the official spec (TypeScript) |

---

## 🚀 Getting Started

### Prerequisites

- Git 2.13+ (for improved submodule support)
- Node.js 20.x+
- Docker & Docker Compose (for some services)

### Cloning the Repository

**Clone with all submodules:**

```bash
git clone --recurse-submodules git@github.com:decentraland/creators-tool-workspace.git
cd creators-tool-workspace
```

**If you already cloned without submodules:**

```bash
git submodule update --init --recursive
```

---

## 📚 Essential Git Submodules Commands

### Updating Submodules

```bash
# Update all submodules to their latest remote commits
git submodule update --remote --merge

# Update a specific submodule
git submodule update --remote --merge <submodule-path>

# Pull latest changes in parent repo AND update submodules
git pull --recurse-submodules
```

### Working Inside a Submodule

```bash
# Navigate into the submodule
cd <submodule-path>

# Work normally with git (checkout, branch, commit, push)
git checkout main
git pull origin main

# Make changes and commit
git add .
git commit -m "Your changes"
git push origin main
```

### After Making Changes in a Submodule

```bash
# Go back to the parent repository
cd ..

# The parent repo will show the submodule as modified
git status

# Stage the submodule reference update
git add <submodule-path>

# Commit the updated submodule reference
git commit -m "Update <submodule-name> to latest version"

# Push parent repo changes
git push
```

### Workflow Example: Work on a Specific Tool

```bash
# Navigate to the service
cd creator-hub

# Create a feature branch
git checkout -b feature/my-new-feature

# Make your changes, then commit and push
git add .
git commit -m "feat: add new feature"
git push origin feature/my-new-feature

# Create a PR in the submodule repository
# After merge, update the parent repo reference
cd ..
git submodule update --remote creator-hub
git add creator-hub
git commit -m "chore: update creator-hub with new feature"
git push
```

---

## 🤝 Contributing

Each submodule has its own contribution guidelines. Please refer to the individual repository's `README.md` and `CONTRIBUTING.md` files for specific instructions.

## 📄 License

Each submodule may have its own license. Please check the individual repositories for license information.
