# Decentraland Creators Tool Workspace

A unified workspace containing the creator-facing tools and libraries for the Decentraland platform. This repository uses **Git Submodules** to aggregate multiple repositories, making it easier to work across projects during development.

For creator documentation, see the [Decentraland Creator Docs](https://docs.decentraland.org/creator/).

---

## 📦 Submodules Overview

### Creator Tools

| Submodule | Description |
|-----------|-------------|
| **[creator-hub](creator-hub/)** | Electron-based desktop application for creating, editing, and deploying Decentraland scenes |
| **[builder](builder/)** | Web-based 3D scene editor for Decentraland |
| **[builder-client](builder-client/)** | Client library for the Builder application |
| **[builder-server](builder-server/)** | Backend service for the Builder application |

### SDK & Development

| Submodule | Description |
|-----------|-------------|
| **[js-sdk-toolchain](js-sdk-toolchain/)** | Toolchain to build JavaScript & TypeScript scenes for Decentraland (SDK7) |
| **[urn-resolver](urn-resolver/)** | URN resolver for Decentraland assets (`@dcl/urn-resolver`) |

### Preview & Validation

| Submodule | Description |
|-----------|-------------|
| **[wearable-preview](wearable-preview/)** | Renders interactive previews of wearables and emotes |
| **[gltf-validator](gltf-validator/)** | Validates glTF 3D models for Decentraland compatibility |

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
