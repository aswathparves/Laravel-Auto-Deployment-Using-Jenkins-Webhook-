# Laravel Application with Apache Load Balancer and CI/CD

This project demonstrates deploying a Laravel application across two frontend servers, with an Apache reverse proxy load balancer and CI/CD pipeline using Jenkins and GitHub webhook.

[![Laravel](https://img.shields.io/badge/Laravel-v8+-red)](https://laravel.com)  
[![Apache](https://img.shields.io/badge/Apache-HTTP--Server-blue)](https://httpd.apache.org)  
[![Jenkins](https://img.shields.io/badge/Jenkins-CI/CD-yellow)](https://www.jenkins.io)  
[![GitHub](https://img.shields.io/badge/GitHub-Webhook-black)](https://docs.github.com/en/webhooks)
[![AWS](https://img.shields.io/badge/AWS-EC2-orange)](https://aws.amazon.com/ec2/)

---

## Project Overview

- Two Laravel frontend servers:
  - FE1: `54.176.172.183:9091`
  - FE2: `54.176.56.42:9092`
- Apache reverse proxy server (load balancer): `54.176.139.180`
- Jenkins CI/CD pipeline automatically deploys code on both frontends when changes are pushed to GitHub.

Requests to the proxy server (`54.176.139.180`) are distributed in a round-robin fashion to FE1 and FE2.

---

## Architecture

```mermaid
graph TD
    A[GitHub Repo] -->|Webhook| B[Jenkins]
    B --> C1[FE1: Laravel :9091]
    B --> C2[FE2: Laravel :9092]
    D[Apache Load Balancer :80] -->|Round Robin| C1
    D -->|Round Robin| C2



---
### Rendered Diagram Description:
- **GitHub Repo** triggers **Jenkins** via a webhook.
- **Jenkins** deploys to both FE1 and FE2.
- FE1 and FE2 are both Laravel apps running on different ports.
- The **Apache Load Balancer** (on port 80) distributes requests to FE1 and FE2 in round-robin fashion.
                
---

## Tech Stack

- Laravel 8+
- Apache HTTP Server (frontend & proxy)
- PHP 8
- SQLite (file-based, persistent)
- Jenkins (pipeline)
- GitHub (source & webhook)

---

## Features

- Reverse proxy using Apache `mod_proxy_balancer`.
- Load balancing between two Laravel servers in round-robin.
- Persistent SQLite database pre-seeded with migrations and data.
- CI/CD pipeline with Jenkins deploying to both FE1 and FE2 automatically.

---
> Copyright (C) 2022 Muhammad Habib Fery.  
**[⬆ back to top](#laravel-travel-app-platform)**

[Frontend Features]:#frontend-features
[Admin Panel Features]:#admin-panel-features
[Requirements]:#requirements
[Install]:#install
[How to setting]:#how-to-setting
[DB Structure]:#database-structure
[License]:#license
