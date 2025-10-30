# ERPNext Setup Automation

This repository contains an automated installer script for ERPNext on Ubuntu 22.04/24.04 LTS servers.

## Quick Start

```bash
curl -fsSL https://raw.githubusercontent.com/WIKKIwk/erpnext_setup/master/install_erpnext.sh | sudo bash
```

## Configuration

You can override defaults by exporting environment variables before running the script:

- `TARGET_USER` – system user that will own the bench (default: frappe)
- `TARGET_USER_PASSWORD` – optional password if the user is being created
- `FRAPPE_BRANCH` – Frappe branch to checkout (default: version-15)
- `ERPNEXT_BRANCH` – ERPNext branch to checkout (default: version-15)
- `BENCH_NAME` – name of the bench directory (default: frappe-bench)
- `SITE_NAME` – site identifier (default: erp.localhost)
- `SITE_DOMAIN` – public hostname (defaults to `SITE_NAME`)
- `SITE_ADMIN_PASSWORD` – Administrator password (default: Admin@123)
- `MYSQL_ROOT_PASSWORD` – MariaDB root password to set (default: dbroot)
- `NODE_MAJOR_VERSION` – Node.js major version (default: 18)
- `PYTHON_VERSION` – Python executable to use (default: python3.10)
- `INSTALL_PRODUCTION` – set to `true` to run `bench setup production`

Example:

```bash
export TARGET_USER=frappe
export SITE_NAME=erp.example.com
export INSTALL_PRODUCTION=true
curl -fsSL https://raw.githubusercontent.com/WIKKIwk/erpnext_setup/master/install_erpnext.sh | sudo bash
```

## What the Script Does

1. Installs system dependencies (Python, MariaDB, Node.js, Redis, wkhtmltopdf).
2. Configures MariaDB for utf8mb4 and sets the root password.
3. Installs Bench via `pipx` and initialises a bench with the specified branch.
4. Fetches ERPNext, creates a new site, and installs the app.
5. Optionally runs `bench setup production` for supervisor/nginx integration.

Use a fresh Ubuntu server (22.04 or 24.04 recommended) and ensure you secure your credentials after installation.
