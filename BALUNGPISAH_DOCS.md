# 📚 DOKUMENTASI LENGKAP ORGANISASI BALUNGPISAH

Platform: https://balungpisah.id
Status: Proof of Concept (PoC)
Motto: "Government reports progress. Citizens decide resolution."

================================================================================

## 🎯 PLATFORM OVERVIEW

Balungpisah adalah platform civic-tech untuk akuntabilitas pemerintah yang citizen-defined.
Warga mendefinisikan masalah, memberikan bukti, dan memverifikasi resolusi.
Pemerintah melaporkan aksi dan progress — tidak lebih.

**Arsitektur Principles:**
- Modular & replaceable services
- Open standards and APIs
- Privacy-aware by design
- Open-source first

================================================================================

## 🔧 CORE PLATFORM (3 Repositories)

### 1. balungpisah (Main Repository)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
URL: https://github.com/balungpisah/balungpisah
Fungsi: Main repo - dokumentasi platform overview
Isi: Arsitektur platform, daftar semua repo, prinsip desain

Directory: D:\LEARNING\balungpisah\core-platform\balungpisah
Branch: main

### 2. balungpisah-core (Backend API)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
URL: https://github.com/balungpisah/balungpisah-core
Tech Stack:
  - Rust + Axum 0.8
  - PostgreSQL + SQLx
  - JWT/OIDC (Logto)
  - OpenAPI (utoipa)
  - Serde, Validator, Tracing

Fungsi: Backend API & core services
  - Authentication & Authorization
  - Data management
  - API endpoints
  - Feature-based architecture

Port: http://127.0.0.1:3000
Health: curl http://localhost:3000/health

Setup:
  $ cp .env.example .env
  $ createdb balungpisah
  $ sqlx migrate run
  $ cargo run

Directory: D:\LEARNING\balungpisah\core-platform\balungpisah-core
Branch: main

### 3. balungpisah-foundation (Philosophy & Governance)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
URL: https://github.com/balungpisah/balungpisah-foundation
Fungsi: Philosophy, technical specs, governance model

Dokumen Penting:
  📄 White Paper (EN/ID) - Platform vision & technical architecture
  🔧 Technical Specs:
     - Jejak Tapak v1.5 - Reputation engine (Markov chain mathematics) ✅
     - SAKSI Pipeline - Testimony collection system (coming soon)
     - TANDANG Marketplace - Problem marketplace mechanics (coming soon)
     - ESCO-ID Taxonomy - Indonesian skills classification (coming soon)
     - Trust Architecture - Security and integrity mechanisms (coming soon)

  🏛️ Governance (coming soon):
     - Genesis Bootstrap - Initial trust seeding & sunset protocol
     - Stochastic Jury - Dispute resolution mechanism

3 Gerbang Utama:
  1. SAKSI (Witness) - Citizens provide testimony, AI extracts structured data
  2. TANDANG (Action) - Problems become marketplace items, anyone can solve
  3. RESTORASI (Restoration) - Verified contribution builds reputation (CV Hidup)

Directory: D:\LEARNING\balungpisah\core-platform\balungpisah-foundation
Branch: main

================================================================================

## 📱 FRONTEND APPS (3 Repositories)

### 4. balungpisah-citizen-app (Citizen Web Application)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
URL: https://github.com/balungpisah/balungpisah-citizen-app
Tech Stack:
  - Next.js 15 (App Router)
  - TypeScript
  - Tailwind CSS v4
  - shadcn/ui (Radix UI)
  - TanStack Query (data fetching)
  - React Hook Form + Zod
  - Logto (authentication)

Fungsi: Web app untuk warga
  ✅ Report Problems - Submit civic issues with photos, location, description
  ✅ Track Reports - Monitor status dari submission sampai resolution
  ✅ View Progress - See updates from officials
  ✅ Browse Community Issues - Explore problems in the community

Prerequisites: Node.js 20+

Directory: D:\LEARNING\balungpisah\frontend-apps\balungpisah-citizen-app
Branch: main

### 5. balungpisah-android (Android Mobile App)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
URL: https://github.com/balungpisah/balungpisah-android
Tech Stack:
  - 100% Kotlin 2.1.0
  - Jetpack Compose (UI)
  - MVVM + Clean Architecture
  - Retrofit / Ktor (networking)
  - Hilt / Koin (dependency injection)

Fungsi: Mobile app Android untuk warga
  ✅ Reporting - Instant submission dengan foto & lokasi
  ✅ Tracking - Timeline government responses & community context
  ✅ Resolution - Voting mechanism untuk "Solved" verification

Setup:
  1. Copy local.properties.sample → local.properties
  2. Copy util/AppConfig.example → util/AppConfig.kt
  3. Open in Android Studio
  4. Connect to balungpisah-core backend

Directory: D:\LEARNING\balungpisah\frontend-apps\balungpisah-android
Branch: main
License: MIT

### 6. balungpisah-ios (iOS Mobile App)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
URL: https://github.com/balungpisah/balungpisah-ios
Tech Stack:
  - Swift 6.0
  - SwiftUI
  - MVVM Architecture
  - URLSession + SSE (Server-Sent Events)

Fungsi: Mobile app iOS untuk warga
  ✅ Citizen Reports - Capture & document public service failures
  ✅ Traceability - View progress from government entities
  ✅ Community Validation - Participate in deciding issue closure

Setup:
  1. Navigate to BalungPisah/Shared/
  2. Copy AppConfig.template.swift → AppConfig.swift
  3. Fill in Logto credentials & server endpoints
  4. Open BalungPisah.xcodeproj in Xcode

Directory: D:\LEARNING\balungpisah\frontend-apps\balungpisah-ios
Branch: main
License: MIT

================================================================================

## 🌐 WEB & MISC (4 Repositories)

### 7. balungpisah-landing (Public Landing Page)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
URL: https://github.com/balungpisah/balungpisah-landing
Tech Stack: Next.js + TypeScript

Fungsi: Landing page publik & initial issue intake
  ✅ Communicate platform philosophy in plain language
  ✅ Lower barrier untuk citizen reports
  ✅ Collect early signals & real-world problem statements
  ✅ Support collaboration & contributor onboarding

Scope: INTENTIONALLY LIMITED
  ✅ This IS: Public website, explanation platform, simple intake form
  ❌ This is NOT: Backend, citizen monitoring app, government dashboard

Directory: D:\LEARNING\balungpisah\web-misc\balungpisah-landing
Branch: develop

### 8. balungpisah-dashboard (Admin Dashboard)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
URL: https://github.com/balungpisah/balungpisah-dashboard
Tech Stack:
  - Next.js 15
  - TypeScript
  - Tailwind CSS
  - Recharts (charts)

Fungsi: Admin dashboard untuk monitoring sistem
  ✅ Real-time statistics & metrics
  ✅ Interactive charts (Status, Category, Report type distribution)
  ✅ Recent reports feed
  ✅ Weekly/monthly trends
  ✅ Reports management (search, filter, detailed view)
  ✅ Tickets tracking
  ✅ Categories & locations analysis
  ✅ Settings (rate limit, admin-only access)

Directory: D:\LEARNING\balungpisah\web-misc\balungpisah-dashboard
Branch: main

### 9. balungpisah-llm-gateway (AI Agent SDK)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
URL: https://github.com/balungpisah/balungpisah-llm-gateway
Tech Stack: Rust SDK

Fungsi: AI agent development dengan TensorZero inference gateway

Crates:
  📦 balungpisah-tensorzero - TensorZero client for inference
  📦 balungpisah-adk - Agent Development Kit

Quick Start:
  [dependencies]
  balungpisah-adk = "0.1"

Basic Agent Example:
  use balungpisah_adk::prelude::*;

  let tz_client = TensorZeroClient::new("http://localhost:3000")?;
  let storage = Arc::new(PostgresStorage::connect("postgres://localhost/agents").await?);
  let agent = AgentBuilder::new()
      .tensorzero_client(tz_client)
      .storage(storage)
      .function("my_assistant")
      .max_iterations(10)
      .build()?;

Directory: D:\LEARNING\balungpisah\web-misc\balungpisah-llm-gateway
Branch: develop

### 10. gotong-royong (Archived)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
URL: https://github.com/balungpisah/gotong-royong
Status: ⚠️ ARCHIVED - Read only
Note: Active development pindah ke Meridian monorepo
       https://github.com/sabrang-mdp/meridian

Directory: D:\LEARNING\balungpisah\web-misc\gotong-royong

================================================================================

## 🏗️ ARSITEKTUR PLATFORM

┌─────────────────────────────────────────────────────────┐
│                    BALUNGPISAH PLATFORM                  │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  🌐 LANDING PAGE        📱 MOBILE APPS (iOS/Android)    │
│  (Initial intake)        (Report & Track)               │
│        ↓                        ↓                        │
│  ┌────────────────────────────────────────┐             │
│  │     CITIZEN WEB APP (Next.js)          │             │
│  │  Submit → Track → Verify Resolution    │             │
│  └────────────────────────────────────────┘             │
│                    ↓                                     │
│  ┌────────────────────────────────────────┐             │
│  │      CORE API (Rust + Axum)            │             │
│  │   Auth, Data, Workflows, APIs          │             │
│  └────────────────────────────────────────┘             │
│                    ↓                                     │
│  ┌────────────────────────────────────────┐             │
│  │    ADMIN DASHBOARD (Next.js)           │             │
│  │     Monitor, Manage, Analytics         │             │
│  └────────────────────────────────────────┘             │
│                                                          │
│  🤖 LLM GATEWAY (Rust SDK - Optional)                   │
│     AI agents + TensorZero                              │
│                                                          │
└─────────────────────────────────────────────────────────┘

================================================================================

## 🚀 LOCAL DIRECTORY STRUCTURE

D:\LEARNING\balungpisah\
│
├── 🔧 core-platform/
│   ├── balungpisah/              (main repo)
│   ├── balungpisah-core/         (backend API)
│   └── balungpisah-foundation/   (philosophy & governance)
│
├── 📱 frontend-apps/
│   ├── balungpisah-android/      (Android app)
│   ├── balungpisah-citizen-app/  (citizen web app)
│   └── balungpisah-ios/          (iOS app)
│
├── 🌐 web-misc/
│   ├── balungpisah-dashboard/    (admin dashboard)
│   ├── balungpisah-landing/      (landing page)
│   ├── balungpisah-llm-gateway/  (AI SDK)
│   └── gotong-royong/            (archived)
│
└── 📄 BALUNGPISAH_DOCS.md        (this file)

================================================================================

## 🎯 GUIDE KONTRIBUSI: WHERE TO START?

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

🌍 FRONTEND / WEB DEVELOPMENT
  → balungpisah-citizen-app (Next.js 15 + Tailwind + shadcn/ui)
  → balungpisah-landing (Landing page + forms)

⚙️ BACKEND / SYSTEMS
  → balungpisah-core (Rust API + Axum + PostgreSQL)
  → balungpisah-llm-gateway (AI agents + TensorZero)

📱 MOBILE DEVELOPMENT
  → balungpisah-android (Kotlin + Jetpack Compose)
  → balungpisah-ios (Swift 6 + SwiftUI)

📚 RESEARCH / DOCUMENTATION
  → balungpisah-foundation (Philosophy, governance, technical specs)

📊 ANALYTICS / DASHBOARD
  → balungpisah-dashboard (Admin monitoring + charts)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## 🔄 KONTRIBUSI WORKFLOW (SEBAGAI ORANG LUAR)

1. Fork repo ke akun GitHub kamu (sudah dilakukan: farkhanmaul)
2. Clone fork-mu (sudah dilakukan di D:\LEARNING\balungpisah)
3. Checkout branch baru:
   $ git checkout -b fitur-baru-atau-bugfix

4. Lakukan perubahan & commit:
   $ git add .
   $ git commit -m "deskripsi perubahan"

5. Push ke fork-mu:
   $ git push origin fitur-baru-atau-bugfix

6. Buat Pull Request:
   - Buka https://github.com/farkhanmaul/[nama-repo]
   - Klik "Contribute" → "Open Pull Request"
   - Jelaskan perubahanmu

7. Update fork dari repo asli (opsional):
   $ git fetch upstream
   $ git checkout main
   $ git merge upstream/main
   $ git push origin main

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## 📝 SETUP REMOTE

Setiap repo sudah memiliki:
  • origin    → fork kamu (https://github.com/farkhanmaul/[repo])
  • upstream  → repo asli (https://github.com/balungpisah/[repo])

Cek remote:
  $ git remote -v

Tambahkan upstream (belum ada):
  $ git remote add upstream https://github.com/balungpisah/[nama-repo].git

================================================================================

## 🔗 USEFUL LINKS

Platform:       https://balungpisah.id
Organization:   https://github.com/balungpisah
Your Forks:     https://github.com/farkhanmaul

================================================================================

Generated: 2026-03-09
Last Updated: Documentation from all repositories
