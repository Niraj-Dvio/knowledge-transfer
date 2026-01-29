# Knowledge Transfer (KT) – Handover Document

## 📋 Document Information

- **Role:** Software Engineer (SDE-1)
- **Team/Product:** DViO One
- **Tenure:** 1 year 6 months
- **Last Working Day:** January 30, 2026
- **Prepared By:** Niraj Rajesh Chordia

---

## 1. Overview

### 1.1 Role Summary

As the Frontend Developer for DViO One, responsibilities included:

- Leading frontend development for DViO One product
- Contributing to backend development where required
- Managing external legal and compliance-related documents (Facebook feature requests, permissions)
- Creating and submitting video recordings for Facebook feature requests and award nominations
- Preparing connector catalogue documentation
- Integrating and coordinating with external services and APIs
- Distributing tasks and reviewing work within the frontend team
- Gathering and clarifying requirements from internal stakeholders

### 1.2 Handover Status

- **Successor:** To be determined (likely distributed among frontend team)
- **Ongoing Projects:** None
- **Pending Features:** None
- **Critical Deadlines:** None

### 1.3 Key Contacts

| Role | Name(s) | Purpose |
|------|---------|---------|
| Project Heads | Anshul, Preetesh | Product requirements, feature decisions |
| Deployment Owner | Preetesh | Handles all deployment processes |
| Frontend Team  |  Aman, Kanak | Day-to-day frontend coordination, credentials access |
| Credential Access | Kailash (primary) | Primary contact for all account credentials |

### 1.4 Important URLs

| URL | Purpose |
|-----|---------|
| [dvio.one](https://dvio.one) | Landing page |
| [app.dvio.one](https://app.dvio.one) | Web application (Production) |
| [node-2.dvio.one](https://node-2.dvio.one) | Backend API |

---

## 2. Systems & Architecture

### 2.1 High-Level Architecture

DViO One is a single product with a React-based frontend consuming backend APIs. The architecture is frontend-centric with strong backend integrations for data processing, ELT pipelines, and AI-powered features.

```
┌─────────────────┐
│   Flamingo      │  React Router v7 Frontend
│   (Frontend)    │  (app.dvio.one)
└────────┬────────┘
         │
         ↓ API Calls
┌─────────────────┐
│   Stardust      │  FastAPI Backend
│   (Backend)     │  (node-2.dvio.one)
└────────┬────────┘
         │
         ↓
┌────────────────────────────────────┐
│  Data Layer & External Services    │
│  - MySQL                           │
│  - Redis                           │
│  - Snowflake                       │
│  - Airbyte (ELT)                   │
│  - Temporal (Workflows)            │
│  - AWS Bedrock (AI)                │
│  - Meta Graph API                  │
│  - Langfuse                        │
│  - Bota (external service)         │
└────────────────────────────────────┘
```

### 2.2 Technology Stack

#### Frontend Stack (Flamingo)

| Technology | Purpose |
|------------|---------|
| React Router v7 | Framework (Declarative Mode) |
| Tailwind CSS | Styling |
| shadcn/ui | UI component library |
| Zustand | State management |
| TanStack Query | Data fetching & caching |
| ai-sdk | AI integration |
| Sentry | Error tracking |
| lucide-react | Icon library |

#### Backend Stack (Stardust)

| Technology | Purpose |
|------------|---------|
| FastAPI | API framework |
| MySQL | Primary database |
| Redis | Caching layer |
| Snowflake | Data warehouse |
| [Airbyte](https://airbyte.com) | ELT connector platform (Powered by Airbyte) |
| Temporal | Workflow orchestration |
| AWS Bedrock | AI/ML services |
| Langfuse | AI observability |
| Sentry | Error tracking |

### 2.3 Key Repositories

| Service/Repo | Tech Stack | Purpose | Owner |
|--------------|------------|---------|-------|
| Flamingo | React (RR v7) | Main frontend application | Frontend Team |
| Stardust | FastAPI | Core backend services & APIs | Backend Team |

**Note:** Frontend was migrated multiple times during development:
- Nebula → Sparrow (Vue) → Flamingo (React Router v7)

### 2.4 Environments

| Environment | Purpose | Access | URL |
|-------------|---------|--------|-----|
| **Local** | Primary development environment | All developers | localhost |
| **Production** | Live customer-facing environment | Managed by Preetesh | app.dvio.one |
| **Staging (Workaround)** | Cloudflare Tunnel exposing local services to tunnel domain | Used as needed | - |

**Note:** Deployment is fully managed by Preetesh. No CI/CD pipeline is currently configured.

### 2.5 Environment Configuration

#### Backend Environment Variables

The backend requires configuration for multiple services:

- Airbyte credentials
- Facebook App credentials
- Google Cloud Console project credentials
- LinkedIn App credentials
- Database configuration (MySQL)
- Temporal configuration
- Snowflake configuration
- Cache configuration (Redis)
- Sentry configuration
- AI API keys (AWS Bedrock, etc.)
- Langfuse credentials
- Frontend host configuration

#### Frontend Environment Variables

The frontend requires:

- Microsoft Clarity key
- Sentry keys
- CSRF keys
- Backend host URL (node-2.dvio.one)

**Credentials Access:** All credentials have been shared with team members. Contact **Kailash** or any frontend team member (Aman, Kanak) for access.

---

## 3. Daily & Weekly Responsibilities

### 3.1 Daily Tasks

- **Monitoring:**
  - Check Sentry for frontend/backend errors (regularly, not strictly daily)
  - Monitor Microsoft Clarity for user behavior issues
  - Check Airbyte and Temporal for ELT/workflow pipeline health

- **Development:**
  - Fix frontend and backend bugs
  - Work on new feature development
  - Share and clarify frontend requirements with backend team
  - Review and refactor code for stability and performance

### 3.2 Weekly Tasks

- **Requirements Gathering:**
  - Gather requirements from Project Heads (Anshul, Preetesh)
  - Coordinate with internal teams to understand requirements, reference documents, and expectations

- **External Platform Management:**
  - Decide on and submit app/feature requests to external platforms (e.g., Meta, Google Cloud Console)

- **Code Quality:**
  - Improve and refactor codebase for:
    - Bug reduction
    - Performance improvements
    - Cost optimization
    - General tech-debt cleanup and architectural improvements

### 3.3 Monitoring Schedule (Handover)

**Team has been informed to check the following at least once a week:**
- Sentry (error monitoring)
- Microsoft Clarity (user analytics)
- Airbyte (ELT pipeline health)

---

## 4. Key Features & Modules

### 4.1 Core Frontend Ownership

**Historical Context:**
- Single-handedly built and maintained the frontend for approximately 1 year
- Led and executed multiple frontend migrations:
  - Nebula → Sparrow (Vue)
  - Sparrow → Flamingo (React Router v7)
- Owned architecture decisions, refactors, and performance improvements
- Contributed to backend development alongside frontend ownership

### 4.2 Competitor Analytics Dashboard

#### Description
Dashboard to view and analyze competitor Facebook and Instagram metrics with end-to-end ownership including requirements, frontend, backend, and platform approvals.

#### Technical Details

**Frontend Areas:**
- Routes: `/competitors`
- Components: `CompetitorsList`, `CompetitorContext`

**Backend Touchpoints:**
- API: `/social/competitors`

**External Integrations:**
- [Meta Graph API](https://developers.facebook.com/docs/graph-api/) (Facebook & Instagram Insights)

#### Platform & Compliance Work
- Handled Facebook App requests and feature approvals related to competitor analytics
- Managed permissions and access token lifecycle

#### Common Issues & Resolutions

| Issue | Cause | Resolution |
|-------|-------|------------|
| Metrics break unexpectedly | Meta access tokens expire | Generate and rotate long-lived access tokens |
| Missing competitor data | Token permissions insufficient | Request additional permissions via Meta App Review |

---

## 5. Integrations & External APIs

### 5.1 Meta (Facebook & Instagram)

#### Primary Usage

1. **Competitor Dashboard:**
   - Fetching Facebook & Instagram insights and metrics
   - Supports both self-owned and competitor public pages

2. **Organic Social Dashboard:**
   - Data ingestion for Facebook Pages via custom connector
   - Integrated with Snowflake for analytics

#### Backend Flow

```
Meta Graph API
      ↓
Custom Facebook Pages Connector (Temporal)
      ↓
Data Processing & Transformation
      ↓
Snowflake (Data Warehouse)
```

#### Permissions & Feature Requests

Meta App permissions and features are requested incrementally based on product needs.

**Request Process:**
1. Create demo screen recording following [Meta's review guidelines](https://developers.facebook.com/docs/app-review/)
2. Provide clear explanation of feature usage and data flow
3. Submit request through [Meta App Dashboard](https://developers.facebook.com/apps/)
4. Wait for approval (typically 5-7 business days)

**Requirements for Video Demo:**
- Must include English subtitles
- Should clearly demonstrate the use case
- Must follow Meta's specific recording guidelines
- Should show actual product functionality

**Useful Resources:**
- [Meta Graph API Documentation](https://developers.facebook.com/docs/graph-api/)
- [Meta App Review Process](https://developers.facebook.com/docs/app-review/)
- [Meta Business Tools](https://business.facebook.com/)

#### Important Notes & Gotchas

⚠️ **Critical Issues to Watch:**

1. **Access Token Expiration:**
   - Tokens can expire and break data fetching
   - Long-lived tokens must be generated and rotated regularly
   - Monitor for token-related errors in Sentry

2. **Permission Requirements:**
   - Any new metric or feature may require additional Meta approval
   - Advanced access must be explicitly requested
   - Never assume a permission is granted by default

3. **Approval Timeline:**
   - Plan for 5-7 business days minimum for Meta reviews
   - Complex requests may take longer
   - Build buffer time into product roadmap for Meta approvals

### 5.2 AI Integrations

#### Initial MVP Implementation

**Early Version:**
- Integrated Anthropic SDK directly in the frontend
- Generated Insights summaries as a key USP for early MVP

**Frontend Responsibilities:**
- End-to-end ownership of AI integration
- Implemented streaming responses in the UI
- Constructed prompts dynamically using:
  - Metrics data
  - Insights data
  - Current viewport/visible dashboard context

#### Evolution

The AI integration evolved from simple summary generation to a **two-way AI chat interface** for deeper analysis and interaction with dashboard data.

**Current Architecture:**
- AI services layer in backend
- AWS Bedrock for model inference
- Langfuse for AI observability and monitoring
- Frontend handles streaming and real-time updates

### 5.3 ELT / Data Pipeline Integrations

#### Airbyte Connectors

Standard ELT integrations for common data sources powered by [Airbyte](https://airbyte.com):
- Scheduled and monitored via backend workflows
- Managed through Airbyte UI
- Status should be checked weekly

**About Airbyte:**
DViO One leverages Airbyte's open-source ELT platform for reliable data integration from various sources into our data warehouse.

#### Custom ELT Pipelines (Temporal)

Built using Temporal for platforms where Airbyte connectors are insufficient:
- Custom extraction logic
- Transformation pipelines
- Direct loading into Snowflake
- More control over data flow and error handling

#### File-based Upload Pipelines

Support for manual data uploads:
- Accepts CSV and Excel files
- Files are parsed and uploaded directly into Snowflake
- Used for ad-hoc or one-time data ingestion scenarios
- Useful for clients who can't provide API access

**Use Cases:**
- Historical data imports
- One-off data analysis requests
- Clients with limited technical integration capabilities

---

## 6. External Platform Management

### 6.1 Meta (Facebook & Instagram) Management

#### Access & Credentials

**Location:** Shared with team (contact Kailash)

**Key Accounts:**
- Facebook App (for Graph API access)
- Meta Business Suite
- Individual page access tokens

**Access Points:**
- [Meta for Developers](https://developers.facebook.com/)
- [Meta Business Suite](https://business.facebook.com/)
- [Graph API Explorer](https://developers.facebook.com/tools/explorer/)

#### Feature Request Process

When new features or permissions are needed:

1. **Preparation:**
   - Clearly define the use case
   - Determine which permissions are needed
   - Check [Meta's documentation](https://developers.facebook.com/docs/) for requirements

2. **Demo Recording:**
   - Record screen demonstration showing the feature in action
   - Add English subtitles explaining each step
   - Show data flow and user benefit
   - Keep it concise but comprehensive

3. **Submission:**
   - Fill out [Meta App Review form](https://developers.facebook.com/docs/app-review/)
   - Upload demo video
   - Provide detailed written explanation
   - Submit for review

4. **Follow-up:**
   - Monitor submission status
   - Respond promptly to any Meta questions
   - Update team on approval status

#### Timeline Expectations

- **Standard Reviews:** 5-7 business days
- **Complex Requests:** Up to 2 weeks
- **Rejections:** Can resubmit with improvements

---

## 7. Testing Strategy

**Current Status:** No formal test suite or testing framework is currently set up.

**Implications:**
- Manual testing is required for all changes
- Regression testing should be thorough
- Consider implementing automated testing in the future

**Recommended Future Improvements:**
- Unit tests for critical frontend components
- Integration tests for API endpoints
- E2E tests for critical user flows

---

## 8. Handover Notes & Best Practices

### 8.1 For New Team Members

#### Getting Started

1. **Understand the Why:**
   - Start by understanding why DViO One was built
   - Learn about the target users and their needs
   - Review product documentation and user stories

2. **High-Level First:**
   - Get a high-level product and technical overview before diving into code
   - Directly jumping into the codebase can be overwhelming
   - Ask questions about architecture and data flow

3. **Gradual Deep Dive:**
   - Once overall context is clear, move gradually into repositories
   - Focus on one feature or module at a time
   - Trace data flow from frontend to backend to understand the system

### 8.2 Working with External Integrations

#### General Approach

- External integrations are generally manageable if official documentation is followed carefully
- Always read the full documentation before starting integration
- Keep credentials secure and rotated regularly

#### Meta-Specific Guidelines

Meta (Facebook & Instagram) requires special attention:

1. **Advance Access Requests:**
   - Must be requested for required permissions/features
   - Cannot assume access based on similar features

2. **Clear Use Case:**
   - Must be filled during the request with specific details
   - Vague descriptions lead to rejections

3. **Demo Video Requirements:**
   - Mandatory for most permission requests
   - Must follow [Meta's specific guidelines](https://developers.facebook.com/docs/app-review/screencast)
   - English subtitles are required
   - Must clearly prove the stated use case

4. **Review Timeline:**
   - Approvals depend on Meta's review timeline (5-7 business days)
   - Plan feature launches accordingly
   - Build in buffer time for potential resubmissions

### 8.3 Major Improvement Opportunity

#### Requirements Management Challenge

**Current Pain Point:**
- Requirements from internal stakeholders are not always clear upfront
- This leads to redundant work and multiple refactors
- Significant time is wasted on rework and clarification cycles

**Recommended Solution:**

Create a **mutual agreement/requirement sign-off document** between:
- Internal stakeholders requesting features
- Engineering team implementing features

**Benefits:**
- Clear documentation and alignment early in the process
- Reduced rework and refactoring
- Better time estimates and planning
- Shared accountability for requirements
- Historical record of decisions and changes

**Suggested Document Sections:**
- Feature description and user stories
- Acceptance criteria
- Technical constraints
- Timeline and milestones
- Sign-off from both parties

### 8.4 Monitoring & Maintenance

#### Weekly Checks (Minimum)

The team should perform the following checks at least once per week:

1. **Sentry:**
   - Review error trends
   - Check for new error patterns
   - Prioritize critical errors affecting users

2. **Microsoft Clarity:**
   - Review user session recordings for UX issues
   - Check for confused navigation patterns
   - Identify areas for improvement

3. **Airbyte:**
   - Verify all scheduled syncs are running
   - Check for failed connections
   - Monitor data freshness

4. **Temporal:**
   - Check workflow execution status
   - Monitor for stuck or failed workflows
   - Review execution times for performance issues

#### Escalation Path

For production issues:
1. Check Sentry for error details
2. Contact backend team for API-related issues
3. Escalate to Preetesh for deployment or infrastructure issues
4. For external API issues (Meta, etc.), check service status pages first

---

## 9. Quick Reference

### 9.1 Common Commands

```bash
# Frontend Development (Flamingo)
pnpm install                 # Install dependencies
pnpm run dev                 # Start development server
pnpm run build              # Build for production

# Backend Development (Stardust)
docker compose build # Build docker image   
docker compose up -d    # Start development server
```

### 9.2 Important Links

| Resource | URL |
|----------|-----|
| Landing Page | [dvio.one](https://dvio.one) |
| Web Application | [app.dvio.one](https://app.dvio.one) |
| Backend API | [node-2.dvio.one](https://node-2.dvio.one) |
| Meta Graph API Docs | [developers.facebook.com/docs/graph-api/](https://developers.facebook.com/docs/graph-api/) |
| Meta App Review | [developers.facebook.com/docs/app-review/](https://developers.facebook.com/docs/app-review/) |
| Airbyte | [airbyte.com](https://airbyte.com) |

### 9.3 Emergency Contacts

| Issue Type | Contact Person | Notes |
|------------|----------------|-------|
| Deployment Issues | Preetesh | Handles all deployments |
| Frontend Questions | Kailash, Aman, Kanak  |
| Backend Questions | Backend Team | Via team channel |
| Product Requirements | Anshul, Preetesh | Project heads |
| Credentials Access | Kailash | Primary contact |

---

## 10. Closing Notes

This document represents the collective knowledge from 1.6 years of building and maintaining DViO One. The product has undergone significant evolution, including multiple framework migrations and architectural improvements.

**Key Takeaways:**

1. **Architecture is Stable:** The current React Router v7 architecture is mature and performant
2. **External Integrations Work Well:** Especially Meta integration, though it requires ongoing maintenance
3. **Requirements Process Needs Improvement:** Implementing a sign-off document would significantly reduce rework
4. **Monitoring is Critical:** Regular checks on Sentry, Clarity, and Airbyte prevent issues from escalating
5. **Team is Capable:** The frontend team (Aman, Kanak) can collectively handle all responsibilities

**For Questions:**
- Technical: Contact team members (Kailash, Aman, Kanak)
- Product: Contact project heads (Anshul, Preetesh)
- Access: Contact Kailash

---
