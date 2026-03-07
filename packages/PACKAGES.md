# 📦 Packages

This directory contains all **modular feature and shared packages** used by **AtlasStack**.

Each package is an **independent Dart module** following a **feature-first architecture**.

Packages must remain:

- Reusable
- Testable
- Isolated from application-level concerns

---

# 🧱 Package Philosophy

AtlasStack follows a **strict modular architecture**.

Guidelines:

- Each **feature is implemented as a package**
- Shared business logic lives in **`core`**
- UI components live in **`design_system`**
- Region-specific logic should be **isolated and injected**
- Packages must **not depend on the app layer**

---

# 📚 Example Packages

| Package | Purpose |
|------|------|
| `core` | Shared domain logic and utilities |
| `design_system` | UI components and theming |
| `feature_x` | Region-specific feature module |

---

# 📦 Creating a New Package

AtlasStack uses inbuilt templates to generate standardized Dart packages.

## Generate a Package

```bash
flutter create --template=package package_name
```

or create an Package with very_good_cli for creation of packages.

## Install the CLI

```bash
dart pub global activate very_good_cli
```

---

## Generate a Package

Run the following command from the **project root**:

```bash
very_good create dart_package package_name
```

### Example

```bash
very_good create dart_package feature_transactions
```

---

## After Package Creation

1. Move the generated package into the `/packages` directory (if created elsewhere).

2. Run:

```bash
melos bootstrap
```

This will link the package inside the workspace.

---

# 📂 Expected Package Structure

Each package should follow this structure:

```
feature_example/
│
├── lib/
│   └── feature_example.dart
│
├── test/
│
├── pubspec.yaml
└── README.md
```

---

# 🏛 Naming Conventions

Follow these rules when naming packages.

### Use `snake_case`

Example:

```
feature_transactions
feature_authentication
```

---

### Feature Packages

Feature modules must start with:

```
feature_
```

Examples:

```
feature_transactions
feature_authentication
feature_payments
```

---

### Shared Packages

Shared packages use simpler names:

```
core
design_system
shared_domain
```

---

### Region Packages (Optional)

If region-specific packages are needed:

```
region_uk
region_eu
region_us
```

---

# 🧪 Code Quality

All packages must follow the workspace quality rules:

- `flutter_lints`
- `dart analyze --fatal-warnings`
- Consistent formatting
- Pre-commit hooks via **Husky**

---

# 🎯 Goals of the Package System

- Scale to **multiple regions without code duplication**
- Maintain **clean dependency boundaries**
- Enable **independent feature development**
- Support **enterprise-level Flutter architecture**

---

# 📌 Future Expansion

The package system is designed to support:

- **2 → 50+ regions**
- Multiple mobile apps in the same mono-repo
- Shared backend SDKs
- Modular admin dashboards
- Region-based CI/CD pipelines

---

# 🏛 AtlasStack Philosophy

> Workspace tooling should not know business domains.  
> Regions are configuration, not separate applications.  
> Features are packages, not folders.