---
type: bot-memory
memory_type: memory-topic
bot: dawnynoibot
created: 2026-06-12
updated: 2026-06-12
tags:
  - bot-memory
  - dawnynoibot
  - infrastructure
  - ssh
  - tailscale
---

# Infrastructure Access

- SSH access target: `100.93.110.89` through Tailscale.
- Tailscale device name: `tablet-bctpavji` (`100.93.110.89`), shown as a Windows device in Tailscale status on 2026-06-17.
- Basic method: connect with `ssh <user>@100.93.110.89` from a machine on the same Tailscale network.
- On the Mac currently running Hermes, Tailscale's App Store CLI is available at `/Applications/Tailscale.app/Contents/MacOS/Tailscale`; `tailscale ssh` is unavailable in this build, so use regular `ssh`.
- Test on 2026-06-12: TCP port `22` is reachable (`nc -vz -G 8 100.93.110.89 22` succeeded), and SSH host key was accepted into `known_hosts`.
- Test on 2026-06-12 from this Hermes session: non-interactive key login was not accepted for `Maripae`, `maripae`, `bda`, or `ubuntu` using the local `~/.ssh/id_ed25519_mac` key. Remote command execution will need the correct SSH username, password, or an authorized public key on the target host.
- Once credentials are confirmed, use a non-interactive test command before making changes:

```bash
ssh -o BatchMode=yes -o ConnectTimeout=10 <user>@100.93.110.89 'hostname && whoami && pwd'
```
