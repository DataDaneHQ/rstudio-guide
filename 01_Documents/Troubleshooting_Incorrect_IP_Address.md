<img src="../00_Resources/incorrect_ip_address_banner.png" alt="Incorrect IP Address Troubleshooting" width="100%">

<br>

## Overview

When connecting to a cloud database from RStudio, you may receive a `dbConnect()` error if your current IP address isn't authorised on the database server's firewall. This guide walks through how to fix it across the three major cloud platforms.

> [!IMPORTANT]
> You'll need sufficient permissions on your cloud platform to modify firewall rules. If you don't have access, contact your database administrator.

---

<br>

## Why Does This Happen?

Cloud database servers use IP allowlists (firewall rules) to control who can connect. If your IP address has changed — which happens regularly on home and office networks — the server will reject your connection even if your credentials are correct.

---

<br>

## Find Your Current IP Address

Before updating any firewall rules, confirm your current public IP address:

1. Go to [whatismyip.com](https://www.whatismyip.com)
2. Note your **public IPv4 address** — it will look like `xxx.xx.xx.xx`

> [!NOTE]
> Your public IP address can change each time you reconnect to a network. If this error recurs regularly, check your IP first before troubleshooting anything else.

---

<br>

## Fix by Platform

### Azure SQL

1. Go to the **Azure Portal** → navigate to your **SQL Server** resource
2. Under **Security**, select **Networking**
3. Scroll to **Firewall rules**
4. Add or update your rule:

| Field | Value |
|---|---|
| Rule name | Your name or identifier |
| Start IPv4 address | Your current public IP |
| End IPv4 address | Your current public IP |

5. Click **Save**

> [!WARNING]
> Do not overwrite another user's firewall rule — scroll through the list to find your own entry before editing.

---

<br>

### AWS RDS

1. Go to the **AWS Console** → navigate to **RDS** → select your database instance
2. Under **Connectivity & security**, click the linked **VPC security group**
3. Select the **Inbound rules** tab → click **Edit inbound rules**
4. Add or update your rule:

| Field | Value |
|---|---|
| Type | Custom TCP |
| Port range | Your database port (e.g. `1433` for SQL Server, `5432` for PostgreSQL) |
| Source | Your current public IP in CIDR format — e.g. `xxx.xx.xx.xx/32` |
| Description | Your name or identifier |

5. Click **Save rules**

---

<br>

### Google Cloud SQL

1. Go to the **Google Cloud Console** → navigate to **SQL** → select your instance
2. Select **Connections** → **Networking**
3. Under **Authorised networks**, click **Add network**
4. Add your rule:

| Field | Value |
|---|---|
| Name | Your name or identifier |
| Network | Your current public IP in CIDR format — e.g. `203.xx.xx.xx/32` |

5. Click **Done** → **Save**

---

<br>

## Still Getting Errors?

| Issue | Fix |
|---|---|
| Error persists after updating firewall | Confirm you saved the rule and are using your **public** IP, not a local network IP |
| IP keeps changing | Ask your administrator about a static IP or VPN with a fixed IP |
| No permission to edit firewall rules | Contact your database administrator to add your IP |
| Unsure which port to use | Check with your administrator — common ports are `1433` (SQL Server), `5432` (PostgreSQL), `3306` (MySQL) |

---

<br>

*← [Git Push Troubleshooting](Troubleshooting_Git_Push.md) · [README](../README.md)*