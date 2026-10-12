# Self-Hosted Infrastructure Project: Secure Linux & Docker Infrastructure

A Docker-based home lab on Ubuntu Server that I designed, built, secured, and documented from scratch. It hosts seven self-hosted services behind a reverse proxy with internal DNS, and exposes **zero inbound ports** to the internet.

Every lab includes the commands I used, how I tested it, what broke, and how I fixed it.

---

## Architecture

<img width="2007" height="1668" alt="Network and service architecture diagram" src="https://github.com/user-attachments/assets/ce3ede43-4fb6-4f11-9d61-6ad49e331079" />

**Traffic flow:**
- **Internal:** Client → Pi-hole (DNS) → Nginx Proxy Manager (HTTPS) → service container, resolved by container name on a shared Docker network
- **External:** Internet → Cloudflare → outbound-only `cloudflared` tunnel → Uptime Kuma (the only publicly reachable service)

---

## Security Highlights

| Control | Implementation |
|---|---|
| **No open inbound ports** | Remote access uses a Cloudflare Tunnel. The server makes an outbound connection, so nothing is exposed on my home firewall. |
| **Minimal public exposure** | Only Uptime Kuma is reachable from the internet. Vaultwarden, Immich, Pi-hole, and File Browser stay on the internal network. |
| **Key-only SSH** | Ed25519 keys required. Password and keyboard-interactive auth disabled, root login disabled. |
| **Dedicated AI-agent account** | Created a separate `claude` account with its own SSH key, so an AI assistant can work on the server without using my admin credentials. |
| **HTTPS everywhere internally** | Nginx Proxy Manager terminates TLS for internal services through private DNS records on my own domain. |
| **Secrets kept out of Git** | Credentials live in `.env` files that are never committed. Tunnel IDs, domains, and ports are redacted in the docs. |

---

## Tech Stack

**Platform:** Ubuntu Server · Docker · Docker Compose
**Networking:** Pi-hole (DNS) · Nginx Proxy Manager (reverse proxy / TLS) · Cloudflare Tunnel
**Services:** Vaultwarden (passwords) · Immich (photos) · File Browser (files) · Uptime Kuma (monitoring)

---

## Labs

### Infrastructure
| Lab | What I did |
|---|---|
| [Server Administration](docs/administration.md) | Core Linux admin commands and server setup |
| [Docker](docs/Docker.md) | Installed Docker Engine and Compose from the official apt repository |
| [Nginx](docs/Nginx.md) | First reverse-proxy setup with Docker Compose |
| [Nginx Proxy Manager](docs/Nginx%20Proxy%20Manager.md) | Shared Docker network, proxy hosts, HTTPS certificates, private DNS |
| [Pi-hole](docs/Pi-hole.md) | Network-wide DNS and ad blocking |
| [Remote Access](docs/Remote%20Access.md) | Cloudflare Tunnel with no open ports |

### Security
| Lab | What I did |
|---|---|
| [SSH Hardening](docs/security/SSH%20Hardening.md) | Key-only authentication, disabled password and root login |
| [Locked-Down Access for Claude](docs/claude/Locked%20down%20access.md) | Separate account and SSH key for an AI agent |

### Applications
| Lab | What I did |
|---|---|
| [Vaultwarden](docs/vaultwarden.md) | Self-hosted password manager, self-signed TLS through Caddy's internal CA |
| [Immich](docs/Immich.md) | Self-hosted photo storage |
| [File Browser](docs/filebrowser.md) | Web-based file access |
| [Uptime Kuma](docs/Uptime-kuma.md) | Service monitoring and alerts |

### Configuration Files
Docker Compose configs (sensitive values redacted): [Cloudflared](docs/yaml/cloudflared.md) · [Pi-hole](docs/yaml/Pihole.md) · [Nginx Proxy Manager](docs/yaml/nginx_proxy.md) · [Vaultwarden](docs/yaml/vaultwarden.md) · [Immich](docs/yaml/immich.md) · [File Browser](docs/yaml/filebrowser.md) · [Uptime Kuma](docs/yaml/kuma.md)

---

## Troubleshooting Highlights

**SSH still accepted passwords after I disabled them.**
I set `PasswordAuthentication no` in `/etc/ssh/sshd_config`, but password login still worked. The config file said that `/etc/ssh/sshd_config.d/*.conf` takes precedence, so I put the hardening settings there, restarted sshd, and confirmed password auth was refused.
*Lesson: know your config load order before you assume a setting is active.*

**Cloudflare Tunnel failed to connect.**
The VM couldn't resolve the tunnel endpoints because Pi-hole, my DNS server, was down. Once Pi-hole was back up, a typo in the CNAME target (`<tunnel-id>.cfargotunnel.com`) and mismatched hostnames between DNS and the proxy were the remaining causes.
*Lesson: map your dependencies. When DNS goes down, everything that depends on it fails too.*

**502 Bad Gateway from Nginx Proxy Manager.**
The proxy host pointed at the host-mapped port (8082) instead of the container's internal port (80). On a shared Docker network, the proxy reaches containers by **container name and internal port**.
*Lesson: host port mappings and container ports are different layers.*

**Browser rejected Vaultwarden's certificate.**
Vaultwarden requires HTTPS. Caddy issued a certificate from its internal CA, but the browser didn't trust it until I imported Caddy's root certificate into Windows' Trusted Root Certification Authorities.
*Lesson: a TLS certificate is only as trusted as the CA that signed it.*

---

## Roadmap

- [ ] Put Cloudflare Access (identity-based auth) in front of Uptime Kuma
- [ ] Document the `claude` account's privilege boundaries (sudo, groups, `AllowUsers`)
- [ ] Add a host firewall (UFW) and fail2ban
- [ ] Pin container image versions instead of `:latest`
- [ ] Automate and test Vaultwarden backups
- [ ] Move configs to real `docker-compose.yml` files with `.env.example` templates
- [ ] Add secret scanning (gitleaks) as a pre-commit check

---

## Skills Demonstrated

Linux server administration · Docker & container networking · DNS (A/CNAME records, private zones) · Reverse proxies & TLS · Zero-trust remote access · SSH hardening · Least-privilege access design · Systematic troubleshooting · Technical documentation
