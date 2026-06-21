# WordPress Multisite — Multi-Domain CMS

A single WordPress Multisite instance serving four independent domains from one Docker container. Each domain maintains separate content, themes, and configuration while sharing a common codebase and database backend.

## Problem

Running four separate WordPress installations means four sets of containers, four databases, four update cycles, and four times the maintenance surface. None of these sites need that kind of isolation — they need independent content and branding, not independent infrastructure.

## Architecture

- One WordPress Multisite installation (domain-mapped, not subdomain) running in a single Docker container
- MariaDB backend shared across all four sites, with WordPress's native multisite tables handling the separation
- Cloudflare Tunnel providing external access — one public hostname per domain, no open inbound ports, no reverse proxy layer in front

## Stack

Docker · WordPress · MariaDB · Cloudflare Tunnel

## Outcome

Four live production sites running on one containerized instance, with zero-downtime routing and SSL handled per domain through the tunnel.

## Notes

This repo documents the architecture pattern, not the live production configuration. Domain names, tunnel hostnames, and credentials in `docker-compose.yml` and `.env.example` are placeholders — copy `.env.example` to `.env` and fill in real values before deploying.
