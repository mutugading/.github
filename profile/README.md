<p align="center">
  <img src="https://github.com/mutugading/.github/blob/main/FavMGT1.svg" alt="Mutu Gading Tekstil Logo" width="200" />
</p>

<h1 align="center">Mutu Gading Tekstil</h1>

<p align="center">
  <b>Official GitHub Organization of PT. Mutu Gading Tekstil</b><br>
  Sukoharjo, Central Java, Indonesia
</p>

<p align="center">
  <a href="https://website.mutugading.com/" target="_blank">
    <img src="https://img.shields.io/badge/Website-mutugading.com-blue?style=for-the-badge&logo=google-chrome&logoColor=white" alt="Visit Our Website">
  </a>
  <a href="mailto:it@mutugading.com">
    <img src="https://img.shields.io/badge/Email-it%40mutugading.com-green?style=for-the-badge&logo=gmail&logoColor=white" alt="Email Us">
  </a>
</p>

---

## About Us

PT. Mutu Gading Tekstil is a textile manufacturing company based in Indonesia, committed to delivering high-quality products through innovation and cutting-edge technology. Our IT division actively develops internal software systems to support operational efficiency — from human resource management and financial planning to cloud-native infrastructure.

Through this GitHub Organization, we manage all internal project codebases and remain open to collaboration with academics, practitioners, and the open-source community in the textile and manufacturing industries.

---

## Platform Architecture

We operate **two main platforms**, each serving different business needs:

```
PT. Mutu Gading Tekstil — Software Ecosystem
│
├── 🏢 GoApps Platform (Microservices — Cloud-Native)
│   ├── goapps-frontend        → Web Application (Next.js 16)
│   ├── goapps-backend         → Microservices API (Go + gRPC)
│   ├── goapps-shared-proto    → Protocol Buffer Contracts
│   └── goapps-infra           → Infrastructure as Code (K3s + ArgoCD)
│
├── 🏢 Apps Mutugading (Modular Monolith — Laravel 12)
│   └── apps-mutugading        → Modular ERP (HR, Finance, MIS)
│
└── 🏢 MGT HRIS (Legacy — Laravel 8)
    └── mgthris                → Human Resources Information System
```

---

## Repository Catalog

### GoApps Platform

A microservices-based enterprise platform for managing business operations in a modular fashion. Built with cloud-native architecture and deployed on Kubernetes (K3s).

| Repository | Description | Tech Stack | Status |
|---|---|---|---|
| [`goapps-frontend`](https://github.com/mutugading/goapps-frontend) | Web application dashboard for GoApps Platform | Next.js 16, React 19, TailwindCSS 4, shadcn/ui, TanStack Query, Zustand | 🟢 Active |
| [`goapps-backend`](https://github.com/mutugading/goapps-backend) | Backend microservices with Clean Architecture | Go 1.24, gRPC, gRPC-Gateway, PostgreSQL 18, Redis 7, RabbitMQ | 🟢 Active |
| [`goapps-shared-proto`](https://github.com/mutugading/goapps-shared-proto) | Single source of truth for API contracts (Protocol Buffers) | Protobuf, Buf CLI, gRPC, OpenAPI | 🟢 Active |
| [`goapps-infra`](https://github.com/mutugading/goapps-infra) | Infrastructure as Code — Kubernetes manifests, monitoring, GitOps | K3s, Kustomize, Helm, ArgoCD, Prometheus, Grafana, Loki | 🟢 Active |

**GoApps Architecture:**

```
                    ┌─────────────┐
                    │   Browser   │
                    └──────┬──────┘
                           │ HTTPS
                    ┌──────▼──────┐
                    │   NGINX     │
                    │   Ingress   │
                    └──────┬──────┘
               ┌───────────┼───────────┐
               ▼           ▼           ▼
        ┌────────────┐ ┌────────┐ ┌────────┐
        │  Frontend  │ │Grafana │ │ ArgoCD │
        │ (Next.js)  │ │  Loki  │ │ GitOps │
        └─────┬──────┘ └────────┘ └────────┘
              │ gRPC (BFF Pattern)
              ▼
        ┌────────────┐
        │  Backend   │
        │ (Go/gRPC)  │
        └─────┬──────┘
     ┌────────┼─────────┬──────────┐
     ▼        ▼         ▼          ▼
┌──────────┐┌───────┐┌────────┐┌────────┐
│PostgreSQL││ Redis ││RabbitMQ││ Oracle │
│(Primary) ││(Cache)││(Queue) ││(Legacy)│
└──────────┘└───────┘└────────┘└────────┘
```

**Available / Planned Modules:**

| Module | Path | Status | Description |
|---|---|---|---|
| Dashboard | `/dashboard` | ✅ Live | Main dashboard with key metrics |
| Finance | `/finance/*` | ✅ Live | Financial management (UOM, Costing, Parameters) |
| HR | `/hr/*` | 🔜 Planned | Human Resources |
| IT | `/it/*` | 🔜 Planned | IT Management |
| CI | `/ci/*` | 🔜 Planned | Continuous Improvement |
| EXSIM | `/exsim/*` | 🔜 Planned | Export / Import Management |

---

### Apps Mutugading

A modular ERP application built on Laravel 12 for managing integrated company operations. Uses a *modular monolith* architecture powered by `nwidart/laravel-modules`.

| Repository | Description | Tech Stack | Status |
|---|---|---|---|
| [`apps-mutugading`](https://github.com/mutugading/apps-mutugading) | Modular ERP — HR, Finance, MIS, Auth | Laravel 12, Livewire 3, Flux UI Pro, Tailwind CSS 4, Oracle DB | 🟢 Active |

**Modules:**

| Module | Alias | Description |
|---|---|---|
| **Auth** | `auth` | Authentication & authorization, Spatie Permission, dual auth mode |
| **Core** | `core` | Shared services, menu system, base components |
| **Finance** | `finance` | Financial reporting and management |
| **HR** | `hr` | HRIS — employee data, attendance, scheduling, payroll |
| **MIS** | `mis` | Management Information System — reporting, dashboards, analytics |
| **Public** | `public` | Public-facing pages and landing content |
| **UI** | `ui` | Shared Blade component library (buttons, modals, forms, grids) |

**Environments:**

| Environment | Branch |
|---|---|
| Production | `main` |
| Staging | `develop` |

---

### MGT HRIS (Legacy)

The first-generation HRIS that remains actively operational. Built with Laravel 8 and connected directly to Oracle Database.

| Repository | Description | Tech Stack | Status |
|---|---|---|---|
| [`mgthris`](https://github.com/mutugading/mgthris) | Human Resources Information System | Laravel 8, Bootstrap, Oracle SQL, Livewire 2, YajraBox | 🟡 Maintenance |

**Key Features:** Employee Management, Payroll System, Attendance Tracking, Dynamic Role-Based Menus.

---

## Tech Stack Overview

### Languages & Frameworks

| Technology | Version | Used In |
|---|---|---|
| Go | 1.24 | goapps-backend |
| PHP | >= 8.2 | apps-mutugading |
| PHP | 7.4.9 | mgthris |
| TypeScript / JavaScript | 5.x | goapps-frontend |
| Protocol Buffers | 3.x | goapps-shared-proto |

### Frontend

| Technology | Version | Used In |
|---|---|---|
| Next.js | 16 | goapps-frontend |
| React | 19 | goapps-frontend |
| TailwindCSS | 4 | goapps-frontend, apps-mutugading |
| shadcn/ui | latest | goapps-frontend |
| Livewire | 3 | apps-mutugading |
| Livewire | 2 | mgthris |
| Flux UI Pro | 2 | apps-mutugading |
| Bootstrap | — | mgthris |
| Alpine.js | 3 | apps-mutugading |

### Backend & API

| Technology | Version | Used In |
|---|---|---|
| gRPC + gRPC-Gateway | 1.78 | goapps-backend |
| Laravel | 12 | apps-mutugading |
| Laravel | 8 | mgthris |
| Buf CLI | v2 | goapps-shared-proto |

### Database & Storage

| Technology | Used In | Notes |
|---|---|---|
| PostgreSQL 18 | goapps-backend | Primary database (GoApps) |
| Oracle SQL | apps-mutugading, mgthris | Enterprise database (ERP & HRIS) |
| Redis 7 | goapps-backend | Caching layer |
| RabbitMQ | goapps-backend | Message queue |
| MinIO | goapps-infra | Object storage (backup) |

### Infrastructure & DevOps

| Technology | Version | Notes |
|---|---|---|
| K3s | v1.34.x | Lightweight Kubernetes |
| Kustomize | v5.3.0 | Kubernetes config management |
| Helm | v3.x | Kubernetes package manager |
| ArgoCD | v7.7.5 | GitOps continuous delivery |
| Prometheus | — | Metrics & monitoring |
| Grafana | — | Dashboards & visualization |
| Loki + Promtail | — | Log aggregation |
| Jaeger | — | Distributed tracing |
| NGINX Ingress | — | Load balancer & TLS termination |
| GitHub Actions | — | CI/CD pipelines |

---

## CI/CD & DevOps

All repositories use **GitHub Actions** for CI/CD pipelines with **self-hosted runners** on staging and production VPS.

### GoApps Platform (Kubernetes / GitOps)

```
Push/PR → Lint → Test → Build → Docker (GHCR) → ArgoCD Sync → Staging → Production
```

| Stage | Tools |
|---|---|
| Code Quality | golangci-lint, ESLint, buf lint |
| Testing | Go test, TypeScript check |
| Container | Docker multi-stage build, GitHub Container Registry (GHCR) |
| Delivery | ArgoCD auto-sync (staging), manual sync (production) |
| Monitoring | Prometheus + Grafana + Loki + Jaeger |

### Apps Mutugading (VPS / Direct Deploy)

```
Push/PR → Lint (Pint) → Test (Pest) → Release (SemVer) → Deploy (SSH)
```

| Stage | Tools |
|---|---|
| Code Quality | Laravel Pint (PSR-12) |
| Testing | Pest v4, SQLite in-memory |
| Release | Auto SemVer tagging via GitHub Actions |
| Delivery | SSH deploy script, maintenance mode, cache optimization |

---

## Team Structure

| Team | Responsibility |
|---|---|
| **GoApps Platform** | Development and maintenance of the entire GoApps ecosystem (frontend, backend, infra, proto) |
| **Apps Development** | Development of Apps Mutugading (Laravel modular ERP) and MGT HRIS |
| **DevOps & Infrastructure** | Kubernetes management, monitoring, CI/CD pipelines, backup & disaster recovery |
| **QA & Testing** | Ensuring quality and stability of every release through automated testing |

---

## How to Contribute

We welcome all forms of collaboration and contribution. Each repository contains `CONTRIBUTING.md` and `RULES.md` files that describe development conventions in detail.

**Contribution steps:**

1. **Fork** the relevant repository
2. **Create a Branch** from `develop` (format: `feat/feature-name` or `fix/bug-name`)
3. **Follow the conventions** for commits and coding style as described in `RULES.md`
4. **Create a Pull Request** to the `develop` branch for review

We also welcome research partnerships with academics, practitioners, and the open-source community to drive innovation in textile and manufacturing.

---

## Contact

| Channel | Detail |
|---|---|
| **Website** | [https://website.mutugading.com/](https://website.mutugading.com/) |
| **Email** | [it@mutugading.com](mailto:it@mutugading.com) |
| **Location** | Sukoharjo, Central Java, Indonesia |
| **GitHub Issues** | Use the Issues tab in each respective repository |

---

## Licenses

Repositories under this Organization use different licenses depending on each project's requirements:

| Repository | License |
|---|---|
| `goapps-frontend` | Proprietary |
| `goapps-backend` | Proprietary |
| `goapps-shared-proto` | Proprietary |
| `goapps-infra` | Proprietary |
| `apps-mutugading` | MIT License |
| `mgthris` | Proprietary |

Please refer to the `LICENSE` file in each repository for more details.

---

<p align="center">
  <b>Thank you for visiting and supporting PT. Mutu Gading Tekstil!</b><br>
  <em>"Together we build innovation and the highest quality."</em>
</p>

<p align="center">
  <sub>© 2024-2026 PT. Mutu Gading Tekstil. All Rights Reserved.</sub>
</p>
