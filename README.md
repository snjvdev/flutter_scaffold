# AtlasStack

**AtlasStack** is a scalable **Flutter mono-repo architecture** designed for building **multi-region, multi-flavor mobile applications** using a **single codebase**.

It enables teams to scale Flutter applications across multiple markets without duplicating code or maintaining separate repositories.

---

# ✨ Features

- Single Flutter codebase for **Android & iOS**
- **Multi-region support**
- **Feature modularization** using Dart packages
- **Environment-based configuration**
- **Flavor-based builds**
- **Clean workspace management** using **Melos**

---

# 🏗 Architecture Overview

AtlasStack follows a **modular mono-repo structure**:

```
atlas_stack/
│
├── melos.yaml
├── analysis_options.yaml
│
├── apps/
│   └── atlas_mobile/
│       ├── pubspec.yaml
│       └── lib/
│
└── packages/
    ├── core/
    ├── design_system/
    ├── feature_transactions/
    └── feature_x/
```

### Key Principles

- **Single source of truth**
- **Feature-first modularization**
- **Region configuration via dependency injection**
- **Flavor-based build separation**
- **Scalable workspace management**

---

# 📦 Mono-Repo Management

AtlasStack uses **Melos** to manage the workspace and link internal packages.

## Bootstrap the Workspace

Run from the project root:

```bash
melos bootstrap
```

This automatically links all internal packages in the workspace.

---

# 🚀 Running the App

All commands should be executed from the **root directory**.

### Run Default

```bash
melos run run
```

### Run With Region

```bash
flutter run --dart-define=REGION=uk
```

Or using Melos:

```bash
REGION=uk melos run run
```

---

# 🌍 Multi-Region Strategy

AtlasStack supports region-specific behavior using:

- `--dart-define=REGION=<region>`
- Region configuration factory
- Feature registration per region
- Environment-based API endpoints

Example:

```dart
const region = String.fromEnvironment('REGION');
```

Regions are injected at **build time** and handled via a **RegionFactory**.

This allows:

- Region-specific features
- Region-specific APIs
- Region-specific toggles

Without:

- Code duplication
- Separate `pubspec.yaml` files
- Separate repositories

---

# 🔧 Flavors & Environments

Flavors are used for:

- Different **bundle identifiers**
- **App store separation**
- **Environment separation** (dev, staging, prod)

Example:

```
--flavor dev
--flavor prod
```

### Combined Usage

```bash
flutter run --flavor prod --dart-define=REGION=uk
```

---

# 📚 Packages

Each feature is implemented as an **independent Dart package**.

### Example Packages

| Package | Description |
|--------|-------------|
| `core` | Shared domain logic and utilities |
| `design_system` | UI components and theming |
| `feature_transactions` | Transaction feature module |
| `feature_x` | Region-specific feature module |

Each package:

- Has its own `pubspec.yaml`
- Is **independently testable**
- Shares **root lint rules**

---

# 🧪 Code Quality

AtlasStack enforces strong code quality standards:

- `flutter_lints`
- `dart analyze --fatal-warnings`
- Consistent formatting
- Pre-commit hooks via **Husky**

---

# 🎯 Goals of AtlasStack

- Scale to **multiple regions without duplication**
- Keep **Melos workspace stable and business-agnostic**
- Avoid **per-region forks**
- Support **enterprise-level growth**
- Maintain **clean dependency boundaries**

---

# 📌 Future Expansion

AtlasStack is designed to support:

- **2 → 50+ regions**
- Multiple **mobile apps** inside the same workspace
- **Admin panels**
- Shared **backend SDKs**
- **CI/CD pipelines per region**

---

# 🏛 Philosophy

> Workspace tooling should not know business domains.  
> Regions are configuration, not separate applications.  
> Features are packages, not folders.