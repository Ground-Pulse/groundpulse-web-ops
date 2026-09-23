### 4. `groundpulse-web-ops`

```markdown
# GroundPulse Operations & Marketplace Portal (`groundpulse-web-ops`)

Internal operations and contractor portal containing the **Admin Oversight Console** and the **Service Provider Dashboard** for GroundPulse.

---

## 📌 Work of This Repo
This repository houses operational management and repair fulfillment workflows:
- **Admin Console (`/admin/dashboard`, `/admin/reassign`):** Platform-wide live metrics (active properties, pending inspections, open issues, in-progress repairs), cross-entity drill-down tables, manual reassignments, and inspector/service-provider verification queues.
- **Service Provider Portal (`/provider/jobs`):** Locality-based assigned jobs, repair instructions, accept/decline actions, and the "Mark Complete" flow requiring notes and after-photos.
- **Marketplace Verification Gate:** Enforces verification badges so only admin-vetted contractors are dispatched.

## ❓ Why We Created This Repo
Administrative and contractor workflows have unique security requirements, high-density data tables, and distinct user authorization flows. Isolating operations into its own web application ensures that sensitive back-office management interfaces and internal controls are completely separated from customer-facing owner accounts.

## 🛠 Tech Stack
- **Framework:** Next.js 14 (App Router) + React 18
- **Language:** TypeScript (Strict Mode)
- **Styling:** Tailwind CSS + shadcn/ui
- **Data Tables & Charts:** TanStack Table, Recharts
- **Data Fetching:** TanStack Query v5
- **Real-Time Client:** Socket.IO Client

## 📁 File Structure
```text
groundpulse-web-ops/
├── app/
│   ├── (admin)/
│   │   ├── dashboard/page.tsx
│   │   ├── reassign/page.tsx
│   │   └── verification/page.tsx
│   ├── (provider)/
│   │   └── jobs/page.tsx
│   ├── layout.tsx
│   └── middleware.ts
├── components/
│   ├── ui/
│   ├── admin/
│   │   ├── LiveCountCard.tsx
│   │   └── ReassignmentDialog.tsx
│   └── provider/
│       ├── JobListItem.tsx
│       └── MarkCompleteDialog.tsx
├── hooks/
│   ├── useAdminDashboard.ts
│   └── useProviderJobs.ts
├── lib/
│   ├── apiClient.ts
│   └── socket.ts
├── package.json
└── README.md
💻 Commands
Bash
# Install dependencies
npm install

# Run operations portal locally
npm run dev

# Build for production
npm run build

# Run unit tests
npm test
🔑 Required Environment Variables
Code snippet
NEXT_PUBLIC_API_URL="http://localhost:3001"
NEXT_PUBLIC_WS_URL="http://localhost:3001"
