## AtlasStack

AtlasStack is a scalable Flutter mono-repo architecture designed for building multi-region, multi-flavor mobile applications using a single codebase.

It enables:

Single Flutter codebase (Android & iOS)

Multi-region support

Feature modularization via packages

Environment-based configuration

Flavor-based builds

Clean workspace management using Melos

🏗 Architecture Overview

AtlasStack follows a modular mono-repo structure:

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

Key Principles

Single source of truth

Feature-first modularization

Region configuration via injection

Flavor-based build separation

Scalable workspace management

📦 Mono-Repo Management

AtlasStack uses Melos to manage the workspace.

Bootstrap
melos bootstrap


This links all internal packages automatically.

🚀 Running the App

All commands are executed from the root directory.

Run Default
melos run run

Run With Region
flutter run --dart-define=REGION=uk


Or via Melos:

REGION=uk melos run run

🌍 Multi-Region Strategy

AtlasStack supports region-specific behavior using:

--dart-define=REGION=<region>

Region configuration factory

Feature registration per region

Environment-based API endpoints

Example:

const region = String.fromEnvironment('REGION');


Regions are injected at build time and handled via a RegionFactory.

This allows:

Region-specific features

Region-specific APIs

Region-specific toggles

No code duplication

No separate pubspec files

🔧 Flavors & Environments

Flavors are used for:

Different bundle identifiers

Store separation

Environment separation (dev, staging, prod)

Example:

--flavor dev
--flavor prod


Combined usage:

flutter run --flavor prod --dart-define=REGION=uk

📚 Packages

Each feature is implemented as an independent Dart package.

Examples:

core – shared domain & utilities

design_system – UI components & theming

feature_transactions – transaction feature module

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