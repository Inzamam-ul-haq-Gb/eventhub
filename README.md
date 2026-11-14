# EventHub — University Event Management & QR Verification Platform

EventHub is a multi-tenant, cloud-ready SaaS platform designed for university **Students**, **Event Organizers**, and **Platform Super Administrators**. Built for AWS Student Builder Group demonstrations and institutional technology events, EventHub runs immediately in **Local Demo Mode** (zero AWS billing or cloud account required) and supports configurable deployment to **AWS Cloud Mode** (Amazon Cognito, API Gateway, AWS Lambda, DynamoDB, S3, CloudFront, and CloudWatch).

---

## Core Capabilities

- **Three Dedicated Role Portals**:
  - **Student Portal (`/student/*`)**: Personalized dashboard, eligible event discovery with filters, capacity-controlled registration, signed digital QR passes (view/print/PDF), attendance history, and verified certificates.
  - **Organizer Portal (`/organizer/*`)**: Command center with Recharts analytics, multi-section event creation/editing/publishing, participant management, real camera + manual fallback QR attendance scanner, attendance-gated certificate issuance/revocation, and CSV report exports.
  - **Super Admin Console (`/admin/*`)**: Multi-university tenant provisioning, organizer application approval queue, student/organizer moderation, platform-wide event moderation, category management, audit logs, and global policy settings.
- **Security & Multi-Tenant Isolation**:
  - Authoritative backend JWT + HttpOnly cookie session verification (`scrypt` password hashing).
  - University tenant isolation (`universityId`) and organizer ownership (`organizerId`) enforced on every API endpoint.
  - Cryptographically signed opaque QR ticket tokens (`EHTKT.<payload>.<hmac>`) preventing tampering, event mismatches, and duplicate check-ins.
  - Certificates strictly require verified `PRESENT` attendance and carry unique verification codes validated at `/verify-certificate/:code`.

---

## Local Setup & Running

### Prerequisites
- Node.js 20+ and npm

### 1. Install Dependencies
```bash
npm install
```

### 2. Configure Environment (Optional)
Copy `.env.example` to `.env` if customizing settings. By default, `VITE_APP_MODE` defaults to `"local"` (**Local Demo Mode**).

### 3. Start Full-Stack Development Server
```bash
npm run dev
```
Open `http://localhost:3000`.

### 4. Run Automated Business Rules Tests
```bash
npm test
```

---

## Local Demo Mode Credentials

All seeded records are clearly labeled as **Local Demo Mode** demonstration data:

| Role | Name | University | Email | Password |
| :--- | :--- | :--- | :--- | :--- |
| **Student** | Maya Lin | Stanford Cloud Institute | `maya.lin@sci.edu` | `DemoStudent!2026` |
| **Student** | Liam Patel | Pacific Tech University | `liam.patel@ptu.edu` | `DemoStudent!2026` |
| **Organizer (Active)** | Elena Vance | Stanford Cloud Institute | `elena.vance@sci.edu` | `DemoOrganizer!2026` |
| **Organizer (Active)** | Marcus Chen | Pacific Tech University | `marcus.chen@ptu.edu` | `DemoOrganizer!2026` |
| **Organizer (Pending)** | Nora Kim | Stanford Cloud Institute | `nora.kim@sci.edu` | `DemoApplicant!2026` |
| **Super Admin** | Dr. Evelyn Brooks | Platform Governance | `admin@eventhub.cloud` | `DemoAdmin!2026` |

---

## Documentation Index

- [Application Architecture](./docs/architecture.md)
- [DynamoDB Database Schema](./docs/database.md)
- [REST API Reference](./docs/api.md)
- [AWS Configuration & Deployment Guide](./docs/aws-setup.md)
- [AWS Student Builder Workshop Guide](./docs/workshop-guide.md)
