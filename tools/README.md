# Tools — Practical Reference Guides

Hands-on command references, configuration patterns, and best practices for the tools a software engineer uses daily.

## Docker & Docker Compose

| Resource | Topics |
|------|--------|
| [Overview](./docker/README.md) | Architecture, lifecycle, ecosystem, when to containerize |
| [Commands & Fundamentals](./docker/01-commands-fundamentals.md) | Image/container lifecycle, exec, logs, inspect, system cleanup |
| [Dockerfile Best Practices](./docker/02-dockerfile-best-practices.md) | Multi-stage builds, layer caching, base images, ARG/ENV, `.dockerignore` |
| [Docker Compose](./docker/03-docker-compose.md) | Service definitions, profiles, overrides, depends_on, healthchecks |
| [Networking & Volumes](./docker/04-networking-volumes.md) | Bridge/host/overlay networks, DNS, named volumes, bind mounts, tmpfs |
| [Security & Production](./docker/05-security-production.md) | Non-root, secrets, resource limits, image scanning, production checklist |
| [Debugging & Troubleshooting](./docker/06-debugging-troubleshooting.md) | Connectivity tests, log analysis, netshoot, compose diagnostics |

## Git

| Resource | Topics |
|------|--------|
| [Overview](./git/README.md) | Object model, three-area workflow, distributed architecture |
| [Commands & Fundamentals](./git/01-commands-fundamentals.md) | Init, add, commit, push, pull, log, diff, tags, cleanup |
| [Branching Strategies](./git/02-branching-strategies.md) | GitHub Flow, Gitflow, Trunk-Based, merge vs rebase vs squash |
| [Commit Conventions](./git/03-commit-conventions.md) | Conventional Commits, message rules, PR best practices, code review |
| [Advanced Workflows](./git/04-advanced-workflows.md) | Interactive rebase, stash, cherry-pick, worktree, submodules |
| [Hooks & Configuration](./git/05-hooks-configuration.md) | Pre-commit framework, native hooks, .gitignore, aliases, global config |
| [Troubleshooting & Recovery](./git/06-troubleshooting-recovery.md) | Undo, reset, reflog, bisect, conflict resolution |

## Linux Terminal

| Resource | Topics |
|------|--------|
| [Overview](./linux-terminal/README.md) | Essential Linux terminal commands for daily user tasks |
| [Navigation & File Operations](./linux-terminal/01-navigation-files.md) | `pwd`, `ls`, `cd`, `mkdir`, `cp`, `mv`, `rm`, `cat`, `less` |
| [Search & Text Processing](./linux-terminal/02-search-text-processing.md) | `find`, `grep`, `rg`, `sort`, `uniq`, `wc`, basic pipelines |
| [Processes & System Monitoring](./linux-terminal/03-processes-system-monitoring.md) | `ps`, `top`, `kill`, `systemctl`, `journalctl`, `free`, `df` |
| [Network Basics](./linux-terminal/04-network-ssh-downloads.md) | `ip`, `ping`, `curl`, `wget`, `ssh`, `scp`, basic connectivity checks |
