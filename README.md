### 4. `groundpulse-web-ops`

```markdown
# groundpulse-web-ops

Back-office operations portal for Platform Administrators and Service Providers[cite: 1].

---

## 🎯 Purpose of This Repo
This Next.js application serves internal platform administrators managing network-wide oversight and vetted third-party service providers (plumbers, electricians, contractors) completing assigned repairs[cite: 1].

## ❓ Why We Created This Repo
Operations and marketplace fulfillment have distinct workflows, security parameters, and data-density needs compared to customer portals:
- **Admin Console:** Requires data-dense tables, platform-wide aggregate counts, contractor verification queues, and manual reassignment controls[cite: 1].
- **Service Provider Hub:** Gives contractors a focused interface to view assigned jobs, check issue locations/notes, and submit completion reports with after-photos[cite: 1].
- **Security Boundaries:** Segregates administrative tooling into its own web surface to prevent accidental leakage of internal capabilities into consumer-facing bundles[cite: 1].

## 📂 File Structure
```text
groundpulse-web-ops/
├── app/
│   ├── (admin)/
│   │   ├── dashboard/page.tsx         # Live count cards & platform metrics
│   │   ├── verification/page.tsx      # Inspector & provider vetting queue
│   │   └── reassign/page.tsx          # Manual reassignments console
│   ├── (provider)/
│   │   ├── jobs/page.tsx              # Active and historical assigned repairs
│   │   └── job/[id]/page.tsx          # Repair scope, location & directions
│   ├── layout.tsx                     # Admin/Ops layout shell
│   └── middleware.ts                  # Enforces ADMIN and PROVIDER access tokens
├── components/
│   ├── admin/
│   │   ├── LiveCountCard.tsx          # Aggregated metric display card
│   │   └── DrillDownTable.tsx         # Cross-entity searchable data grid
│   ├── provider/
│   │   ├── RepairActionCard.tsx       # Accept / decline repair assignment
│   │   └── MarkCompleteDialog.tsx     # Confirmation notes & after-photo uploader
│   └── ui/                            # Shared Radix/shadcn UI primitives
├── hooks/
│   ├── useAdminMetrics.ts             # TanStack Query hook for dashboard metrics
│   └── useProviderJobs.ts             # TanStack Query hook for repair jobs
├── lib/
│   ├── apiClient.ts                   # Typed API client targeting groundpulse-api
│   └── socket.ts                      # WebSocket client for real-time status changes
├── package.json
├── tailwind.config.ts
├── tsconfig.json
└── README.md
💻 Commands
Bash
# 1. Install dependencies
npm install

# 2. Configure environment variables
cp .env.example .env.local

# 3. Start development server (runs on port 3002 to avoid collision)
npm run dev -- -p 3002

# 4. Run component tests
npm test

# 5. Build for production
npm run build
🔑 Required Environment Variables
Code snippet
NEXT_PUBLIC_API_URL="http://localhost:3001"
NEXT_PUBLIC_WS_URL="http://localhost:3001"
