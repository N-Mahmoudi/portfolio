# Portfolio Admin — Implementation Task Plan

This plan is based on the confirmed requirements. Provider choices remain open until official documentation and current free-tier limits are reviewed.

## Phase 0 — Requirements and project foundation

### T-001 — Freeze the confirmed requirements and create a traceable feature checklist.
- **Acceptance criteria:** Every confirmed requirement maps to a screen, API/module, test or explicit future decision.

### T-002 — Create the admin sitemap, route map and navigation hierarchy.
- **Acceptance criteria:** All 27 screens have stable route identifiers and no duplicated module is presented as a separate feature without a reason.

### T-003 — Define the shared UI design tokens and component inventory.
- **Acceptance criteria:** Colors, typography, spacing, breakpoints, radii, borders, elevation, icon rules and component states are documented.

### T-004 — Create a Figma file structure and shared components plan.
- **Acceptance criteria:** Pages are grouped by module; shared shell, tables, forms, dialogs, badges, navigation and states are reusable components.

## Phase 1 — Visual references and Figma

### T-010 — Generate a reference image for each admin screen using the matching JSON prompt.
- **Acceptance criteria:** Each image follows the same global shell and visual tokens; no screen invents conflicting navigation or styles.

### T-011 — Review images for consistency before rebuilding them in Figma.
- **Acceptance criteria:** Sidebar, header, typography, buttons, spacing, table density and status colors match across the screen set.

### T-012 — Rebuild approved references as editable Figma frames and components.
- **Acceptance criteria:** UI is made from editable layers/components rather than using the generated screenshot as a flat background.

### T-013 — Create responsive variants and Persian RTL versions for shared patterns.
- **Acceptance criteria:** The design system defines desktop/tablet/mobile behavior and RTL mirroring for navigation, forms, tables and directional icons.

### T-014 — Prototype key flows in Figma.
- **Acceptance criteria:** Clickable flows cover login/MFA, edit content, submit for approval, approve/publish, invite user and restore backup confirmation.

## Phase 2 — Technical architecture and secure foundation

### T-020 — Compare current official provider options for frontend hosting, backend/API, database, authentication/MFA, media storage and backup storage.
- **Acceptance criteria:** Decision record compares free-tier limits, security, cost, exportability, regional availability and lock-in using current official documentation.

### T-021 — Define the application architecture, data model and API contracts before implementation.
- **Acceptance criteria:** Entities cover users, roles, permissions, localized content, workflow states, revisions, media, resumes, pages, SEO, notifications, audit events and backups.

### T-022 — Set up repository, linting, type checking, automated tests and separate Preview/Production environments.
- **Acceptance criteria:** CI validates code and tests; secrets are isolated by environment and never exposed to client code.

### T-023 — Implement authentication, invited-user onboarding, password recovery, rate limiting and MFA policy.
- **Acceptance criteria:** Public registration is disabled; MFA is enforced for administrators and sensitive roles; recovery and failed-login behavior are tested.

### T-024 — Implement server-enforced RBAC and permission checks.
- **Acceptance criteria:** View/create/edit/delete/approve/publish permissions are checked server-side and tested against unauthorized requests.

### T-025 — Implement audit events and the notification inbox foundation.
- **Acceptance criteria:** Security events and key content operations record actor ID, timestamp and result; field-level before/after diffs are not stored.

## Phase 3 — Content modules and publishing

### T-030 — Implement reusable localized content fields and validation.
- **Acceptance criteria:** Fields support types, required/optional flags, validation and independent per-language values.

### T-031 — Implement projects, work experience, skills and education CRUD.
- **Acceptance criteria:** Create/read/update/archive, ordering, localization, visibility and permission checks pass tests.

### T-032 — Implement blog article CRUD and taxonomy.
- **Acceptance criteria:** Articles support categories, tags, authors, localized content and workflow status.

### T-033 — Implement content workflow and approval queue.
- **Acceptance criteria:** Draft, pending approval, published and archived transitions are permission-checked and audited.

### T-034 — Implement revision history and restore.
- **Acceptance criteria:** Previous versions can be viewed and restored; restoration creates a new version and preserves the history.

### T-035 — Implement centralized media library and usage tracking.
- **Acceptance criteria:** Uploads, metadata, alt text, search, preview, reuse and in-use delete warnings work.

### T-036 — Implement navigation menu management.
- **Acceptance criteria:** Header/footer menus support nested items, sorting, localized labels, internal/external links and validation.

## Phase 4 — Pages, resumes, SEO and insights

### T-040 — Implement visual page builder with reusable sections and responsive settings.
- **Acceptance criteria:** A page can be assembled without code, previewed at supported breakpoints and saved as a draft.

### T-041 — Implement controlled custom-page repository sync and approval.
- **Acceptance criteria:** Unreviewed code cannot reach production; secrets are protected server-side; preview and activation are permission-checked.

### T-042 — Implement resume variants with upload and structured-data PDF generation paths.
- **Acceptance criteria:** Role/language variants are independent; public/private access is enforced server-side.

### T-043 — Implement brand profiles and page-specific overrides.
- **Acceptance criteria:** Pages can inherit central fields or override selected values without unintentionally changing unrelated pages.

### T-044 — Implement localization-aware SEO and share metadata.
- **Acceptance criteria:** Localized metadata, canonical URLs, social previews, sitemap and robots behavior are validated.

### T-045 — Implement privacy-conscious analytics.
- **Acceptance criteria:** Date-filtered aggregate metrics cover page/project views, landing pages, PDF downloads and contact/social link clicks.

## Phase 5 — Operations, reliability and release

### T-050 — Implement system pages and safe public error messages.
- **Acceptance criteria:** Localized 404, access denied, maintenance and generic error pages are editable without exposing sensitive diagnostics.

### T-051 — Implement manual backup listing and guarded restore.
- **Acceptance criteria:** Admins can inspect backup coverage, choose a backup and confirm restore; an emergency backup is encouraged or required where feasible.

### T-052 — Implement system health and safe operational diagnostics.
- **Acceptance criteria:** Health checks and failed operations are visible without exposing credentials or internal secrets.

### T-053 — Implement export and portability package.
- **Acceptance criteria:** Content, translations, page-builder structures, resume metadata, asset manifest and migration documentation can be exported.

### T-054 — Run risk-based end-to-end tests and production-readiness review.
- **Acceptance criteria:** Login/MFA, RBAC, content CRUD, preview/publish, code approval, private files, restore and localization have passing critical tests.

### T-055 — Document deployment, environment configuration, rollback and administrator procedures.
- **Acceptance criteria:** A new maintainer can deploy to Preview, validate, obtain approval and release to Production using the documented process.

## Screen coverage

The JSON artifact includes 27 independent screen prompts: Dashboard, Projects List, Project Editor, Work Experience, Skills, Education, Blog List, Blog Editor, Page Builder, Custom Pages, Navigation Menus, Media Library, Resume Versions, Brand Profiles, Analytics, SEO, Users & Roles, Notifications Inbox, Activity Logs, Backups & Restore, System Pages, Settings, System Health, Login/MFA, Forgot Password, Content Revision History and Approval Queue.

## Figma implementation rule

Do not place generated screenshots as flat backgrounds in the final file. Rebuild approved designs as editable frames, components, variants and auto-layout structures.