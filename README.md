# Laratix – A lean ticket system for developers who are done with overengineered ticket system

Laratix is a lightweight, extensible ticket system built on the **Laravel** PHP framework, born out of frustration with bloated, expensive, and hard‑to‑customize enterprise solutions like the one from the famous Aussies.  
Instead of click hell, feature bloat, and license chaos, you get: clear concepts, clean code, and full control over your own ticket universe.

---

## Motivation

I’m a developer, not a license manager.  
I want to:

- Create, edit, and track tickets – **without** clicking through 50 submenus.
- Define workflows that actually fit my team – **without** needing a certification.
- Structure permissions in a meaningful way – **without** cryptic permission matrices.
- Integrate external tools and IdPs – **without** proprietary plugins and extra fees.

That’s why **Laratix** exists: a ticket system that is modern, understandable, self‑hostable – and puts the focus back on **development and collaboration**, not tool frustration.

---

## Project status – very young, contributions highly welcome

Laratix is a **very young project**, and a lot is still under construction:

- The **role model**, **graphical workflow editor**, and **OAuth integration** are partly just skeletons or still in the planning phase.
- API, database schema, and UI are subject to change.
- Documentation, tests, and best practices are being added continuously.

If you want to help build a ticket system born from real developer frustration, contributions are highly welcome – especially around:

- Extending and refining the **role model**
- UX and implementation of the **graphical workflow editor**
- Integration of additional **OAuth/OIDC providers** and SSO scenarios
- Performance, stability, and test coverage

Just open an issue with your idea or jump right in with a pull request (see “Contributing” below).

---

## Features

### 🎫 Ticketing & boards

- Classic ticket types: bug, feature, task (extendable via configuration)
- Status‑ and workflow‑dependent actions (e.g. only certain roles may close tickets)
- Configurable fields (required fields, validation rules, custom field types)
- Board view (Kanban‑like) with drag & drop for moving tickets between status columns
- Filters & search (by status, type, priority, assignee, tags)

---

### 👥 Role model & permissions

Laratix uses a clear, understandable role model that reflects real development and project teams:

- **Roles** (e.g. `admin`, `project_manager`, `developer`, `reporter`, `viewer`)
- **Role‑based access control (RBAC)**: permissions are assigned to roles, not individuals.
- **Project‑scoped role assignment**: a user can be `project_manager` in project A and `developer` in project B.
- Granular permissions, including:
  - Create, edit, delete tickets
  - Manage workflows/statuses
  - Assign users & roles within projects
  - Configuration & system administration

Roles and permissions are represented in code and in the database and can be extended or replaced as needed.

---

### 🔄 Graphical workflow editor

Complex workflows without XML hell or obscure configuration files:

- **Visual editor** in the browser:
  - Statuses as nodes
  - Transitions as edges
- Drag & drop to create and adjust workflows
- Support for multiple workflows per project or ticket type
- Configurable conditions per transition, e.g.:
  - Only specific roles may perform certain transitions
  - Required fields on status changes (e.g. “Resolution” when closing a ticket)
  - Validations and hooks (e.g. webhooks, Laravel events)
- Workflow versioning to keep changes traceable

Goal: workflows should be **understandable** and **visible** – not hidden somewhere in JSON.

---

### 🔐 OAuth / Single Sign-On

Laratix includes modern, integrated authentication:

- Support for common OAuth/OIDC providers:
  - GitHub
  - GitLab
  - Google
  - Azure AD / Microsoft Entra ID
  - Keycloak (and other OpenID providers)
- Ability to configure multiple providers in parallel
- Mapping of OAuth identities to Laratix users
- Optional auto‑provisioning of users on first login (configurable)
- Role assignment via:
  - manual assignment
  - or optional mapping based on OAuth groups / claims

This allows Laratix to integrate cleanly into existing organizational environments – without becoming yet another isolated user directory.

---

### 🧱 Tech stack

- **Framework**: [Laravel](https://laravel.com/)
- **Language**: PHP (>= 8.1 recommended)
- **Database**: MySQL/MariaDB or PostgreSQL (others possible via Laravel ORM)
- **Frontend**:
  - Blade templates or optionally Vue/React (depending on setup)
  - TailwindCSS / Bootstrap (configurable)
- **Auth**: Laravel Sanctum/Passport + OAuth/OIDC integration
- **Containers** (optional): Docker Compose setup for a quick start

---

## Installation

> Note: Laratix is in an early development stage. API, database schema, and features may still change.

### Requirements

- PHP 8.1+
- Composer
- Node.js & npm (for frontend builds, if needed)
- MySQL/MariaDB or PostgreSQL
- Git

### Steps

```bash
# Clone repository
git clone https://github.com/your-user/laratix.git
cd laratix

# Install PHP dependencies
composer install

# Create environment file
cp .env.example .env

# Generate app key
php artisan key:generate

# Adjust database configuration in .env

# Run migrations & seeders
php artisan migrate --seed

# Build assets (if a frontend build is used)
npm install
npm run build

# Start local server
php artisan serve

