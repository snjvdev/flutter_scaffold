## 📚 Packages

Each feature is implemented as an independent Dart package.

Examples:

core – shared domain & utilities

design_system – UI components & theming

feature_x – region-specific feature module

Each package:

Has its own pubspec.yaml

Is independently testable

Shares root lint rules

🧪 Code Quality

AtlasStack enforces:

flutter_lints

Pre-commit hooks via Husky

dart analyze --fatal-warnings

Consistent formatting

🎯 Goals of AtlasStack

Scale to multiple regions without duplication

Keep Melos stable and business-agnostic

Avoid per-region forks

Support enterprise-level growth

Maintain clean dependency boundaries

📌 Future Expansion

AtlasStack is designed to support:

2 → 50+ regions

Multiple mobile apps inside the same workspace

Admin panels

Shared backend SDKs

CI/CD pipelines per region

🏛 Philosophy

Workspace tooling should not know business domains.
Regions are configuration, not separate applications.
Features are packages, not folders.

If you’d like, I can also generate:

A shorter public GitHub version

A more enterprise internal documentation version

A version with diagrams

Or a contribution guideline section

Tell me where this repo will live (internal enterprise / public GitHub / template project).

create an md file for package folder?
 
 To Generate an Packages use very_good_cli - COMMAND. 

very_good create dart_package #package_name.

Here’s a clean README.md you can place inside the /packages folder.

It explains the purpose, structure, and how to generate new packages using very_good_cli.

Packages

This directory contains all modular feature and shared packages used by AtlasStack.

Each package is an independent Dart module and follows a feature-first architecture.
Packages must be reusable, testable, and isolated from app-level concerns.

🧱 Package Philosophy

Each feature is a package.

Shared logic lives in core.

UI components live in design_system.

Region-specific logic should be isolated and injected.

No direct app-level dependencies inside packages.

📦 Creating a New Package

AtlasStack uses very_good_cli to generate standardized Dart packages.

Install CLI (if not installed)
dart pub global activate very_good_cli

Generate a Package

From the root directory:

very_good create dart_package package_name


Example:

very_good create dart_package feature_transactions


After generation:

Move the package into the /packages directory if needed.

Run:

melos bootstrap

📂 Expected Package Structure

Each package should follow this structure:

feature_example/
│
├── lib/
│   └── feature_example.dart
│
├── test/
│
├── pubspec.yaml
└── README.md

🏛 Naming Conventions

Use snake_case

Prefix feature packages with feature_

Shared domain packages use simple names like:

core

design_system

shared_domain

Examples:

feature_transactions
feature_authentication
design_system
core
region_uk