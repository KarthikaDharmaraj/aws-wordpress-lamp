# WordPress on a LAMP Stack — Amazon EC2 (Ubuntu)

A WordPress website with an optional WooCommerce demo shop, built from scratch on a single Amazon EC2 server running Ubuntu, Apache, PHP and MariaDB.

> **Status:** 🚧 In progress

---

## Architecture

![Architecture diagram](architecture.png)

| Component | Technology | Role |
|---|---|---|
| Server | Amazon EC2 (Ubuntu Server 24.04 LTS, micro instance) | Hosts the whole stack |
| Firewall | Security group | Allows only HTTP (80) from anywhere and SSH (22) from my IP |
| Web server | Apache (`apache2`) | Receives visitors and returns pages |
| Language | PHP | Builds pages dynamically |
| Database | MariaDB | Stores posts, pages, users, products and orders |
| Application | WordPress (+ WooCommerce) | Website and online shop |

**Region:** Europe (Frankfurt) `eu-central-1`

---

## AWS services and tools used

- Amazon EC2
- Security groups
- AWS Budgets
- Ubuntu Server 24.04 LTS
- Apache, PHP, MariaDB
- WordPress, WooCommerce

---

## Build steps

| Phase | Description | Status |
|---|---|---|
| 1 | Cost guardrails: zero-spend budget, region selection | ✅ Done |
| 2 | Launch EC2 instance, key pair and security group | ⬜ |
| 3 | Connect over SSH, install Apache and PHP | ⬜ |
| 4 | Install MariaDB, create the database and user | ⬜ |
| 5 | Install and configure WordPress | ⬜ |
| 6 | (Optional) WooCommerce demo shop | ⬜ |
| 7 | Test and document | ⬜ |
| 8 | Clean up all AWS resources | ⬜ |

All commands are in [setup-commands.md](setup-commands.md).

---

## Security decisions

- SSH (port 22) allowed only from my own IP address
- Database port (3306) never opened to the internet; only WordPress on the same server can reach it
- Dedicated database user with rights on the WordPress database only
- Default `admin` username avoided for WordPress
- No passwords, keys or `wp-config.php` committed to this repository

---

## Cost decisions

- Single micro EC2 instance on the AWS Free plan (credits)
- Database on the same server instead of Amazon RDS
- No Elastic IP, load balancer, NAT Gateway or domain name
- Zero-spend budget alert and credit balance checked each session
- Instance stopped between work sessions
- All resources deleted after completion

---

## Screenshots

_Added as each phase is completed._

---

## What I learned

_To be written at the end of the project._

## Possible next improvements

- HTTPS with a free certificate
- A custom domain name
- Moving the database to Amazon RDS
- Connecting with AWS Systems Manager Session Manager instead of SSH

---

> **Note:** All AWS resources were deleted after completion to avoid charges, so there is no live demo. Screenshots document each step.
