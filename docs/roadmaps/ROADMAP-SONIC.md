# Sonic Roadmap (4-month plan)

> Based on ROADMAP.md. "Done when", "Project" and level tags mean the same thing here. Week 1 starts Sat 31 Oct 2026. Week 17 ends Fri 26 Feb 2027.
> Budget: 42 h/week (6 h x 7 days). 17 weeks = 714 hours. ~689 h solo after the 90-min weekly team session. Goal: the L1 core plus the start of
> L2 (Automation/Ansible) by week 17, ready to apply for junior and DevOps-support roles. You start from zero, so the plan adds a 35-hour lead-in and uses
> 1.4x the base hours for every section. Those multipliers are guesses. Log actual hours in the table below and recalibrate at the end of week 4.
> Extra hours go to depth and buffer (see section targets below). Protect your hours, and add weekend time before cutting anything else (see the cut
> order at the bottom). WARNING: this plan has little slack. The Virtualization block in week 17 (14 h) is your shock absorber.

## Week by week

| Week | Starts | Focus                                                        | Target h | Actual h |
| ---- | ------ | ------------------------------------------------------------ | -------- | -------- |
| 1    | Oct 31 | Lead-in (of 56 h), on a local VM                             | 42       |          |
| 2    | Nov 7  | Lead-in ends. Join the lab. Git starts                       | 42       |          |
| 3    | Nov 14 | Git ends. Linux starts                                       | 42       |          |
| 4    | Nov 21 | Linux. Week-4 recalibration                                  | 42       |          |
| 5    | Nov 28 | Linux                                                        | 42       |          |
| 6    | Dec 5  | Linux ends. Python starts                                    | 42       |          |
| 7    | Dec 12 | Python ends. Bash starts                                     | 42       |          |
| 8    | Dec 19 | Bash ends. Network starts                                    | 42       |          |
| 9    | Dec 26 | Network                                                      | 42       |          |
| 10   | Jan 2  | Network ends. Docker starts                                  | 42       |          |
| 11   | Jan 9  | Docker                                                       | 42       |          |
| 12   | Jan 16 | Docker ends. Reverse proxy starts                            | 42       |          |
| 13   | Jan 23 | Reverse proxy                                                | 42       |          |
| 14   | Jan 30 | Reverse proxy ends. CI/CD starts                             | 42       |          |
| 15   | Feb 6  | CI/CD                                                        | 42       |          |
| 16   | Feb 13 | CI/CD ends. Monitoring starts. L2 Ansible (start L2)         | 42       |          |
| 17   | Feb 20 | Monitoring ends. Ansible ends. Checkpoint, buffer            | 42       |          |

Keep Sonic's 35 h lead-in (W1-W2). Approx section targets (pre-recalibration): Lead-in 56; Join lab 14; Git 24; Linux 112; Python 48; Bash 48; Network 80 (+VLAN depth); Docker 80; Reverse proxy 48; CI/CD 80; Monitoring 48 (+Zabbix); Ansible 48; checkpoint/stretch/buffer 48. These are guesses; recalibrate from logged actual hours at end of week 4.

## Rules

- You do every "Done when" yourself. Watching someone else do it does not count.
- Pair with Amir on projects during these overlap windows: Linux (weeks 3-5), Docker (10-12), reverse proxy (12-14), CI/CD (14-16). Network is offset
  by about 3 weeks (Amir is ahead), so ask him to teach it back in the weekly session.
- Mava reviews your merge requests but does not teach you one to one. If you are stuck for more than 45 minutes, write down what you tried and ask in
  the group.
- Keep a runbook repo: after every section, write a short English note on what you did and what broke. It doubles as portfolio material.
- One 90-minute team session per week: 30 min live demos, 30 min teach-back, 30 min MR review and planning. It counts toward your 42 hours.
- Write each project README when you finish its project, not at the end.

## Lead-in [W1-W2, 56h]

> Week 1 happens before the shared lab is ready, so use a local VM (for example VirtualBox with Ubuntu LTS) and move to the lab in week 2.

- [ ] Terminal comfort (cd, ls, cat, less, cp, mv, rm, man, --help) [15h]. Done when: you complete 20 small file tasks in the VM with no graphical
      interface.
- [ ] SSH and a text editor (nano first) [5h]. Done when: you log into the VM with an SSH key and edit a config file over SSH.
- [ ] Programming logic: variables, conditionals, loops, functions [10h]. Use the official Python tutorial (docs.python.org). Done when: you write
      FizzBuzz and a function that counts the words in a text file.
- [ ] How computers and the internet work, at a high level [5h]. Done when: you can explain what a process, a file, an IP address and a DNS name are
      in your own words.

## 0. Join the Shared Lab [W2, 14h]

- [ ] WireGuard access to the lab (Mava builds it). Done when: you can SSH into a lab VM from home.
- [ ] Offline documentation (man pages, tldr, offline docsets). Done when: you can look up syntax with the internet off.
- [ ] Use the shared mirrors. Done when: a lab VM installs a package and pulls an image through the mirrors only.

## LEVEL 1 core

- [ ] 1.  Git [W2-W3, 24h]
  - [ ] Core commands (init, add, commit, push, pull). Done when: you can do a full cycle without notes.
  - [ ] Branching, merging, conflict resolution. Done when: you resolve a real conflict in a teammate's repo.
  - [ ] Rebase. Done when: you squash 5 commits with interactive rebase.
  - [ ] Merge request / code review workflow (GitLab-style). Done when: you opened and reviewed an MR with comments.
  - [ ] .gitignore & Markdown. Done when: your READMEs render cleanly.
  - [ ] Project: team notes repo with protected main and MR-only changes.
- [ ] 2.  Linux (LPIC roadmap) [W3-W6, 112h]
  - [ ] Filesystem, permissions, ACLs, umask. Done when: you can fix permission problems without trial and error.
  - [ ] Users, groups, sudo. Done when: you can create a restricted admin user from scratch.
  - [ ] Processes & signals. Done when: you can find and stop a runaway process and explain load average.
  - [ ] Package management (apt) + local repos/mirrors. Done when: you built and used a local mirror.
  - [ ] systemd & services. Done when: you wrote a unit file with restart policy and read its journal.
  - [ ] Cron & timers. Done when: a systemd timer runs a job and logs its output.
  - [ ] Disk, LVM & mounts. Done when: you extend an LVM volume online and recover from a broken fstab.
  - [ ] Performance tuning & patching. Done when: you diagnose high CPU, memory or IO with top/vmstat/iostat. (STRETCH: first things to cut)
  - [ ] Ubuntu/Debian first, then Rocky/Alma. Done when: the same task works on both families.
  - [ ] YAML / JSON / TOML (jq, yq). Done when: you can validate and transform all three.
  - [ ] SSH & keys. Done when: key-only login, ssh config, jump host and port forwarding all work.
  - [ ] Project: harden and document a fresh server (users, SSH, firewall, unattended updates).
- [ ] 3.  Python basics [W6-W7, 48h] (moved before Bash for you)
  - [ ] Syntax, data structures, files, modules. Done when: you can write a 100-line script without copy-pasting.
  - [ ] Automation (requests, subprocess, argparse). Done when: you built a CLI that calls an API and prints a report.
  - [ ] Project: health-check script for N servers that sends results to a chat webhook.
- [ ] 4.  Bash (shell scripting) [W7-W8, 48h]
  - [ ] Variables, conditionals, loops, functions. Done when: scripts take arguments and validate them.
  - [ ] Pipes, redirection, text processing (grep, sed, awk, jq). Done when: you extract the top 10 IPs from a large log.
  - [ ] Error handling & best practices (set -euo pipefail, trap, shellcheck). Done when: shellcheck reports zero warnings.
  - [ ] Project: backup script with rotation, logging and exit codes, run by a systemd timer.
- [ ] 5.  Network (Network+ roadmap) [W8-W10, 80h]
  - [ ] OSI & TCP/IP. Done when: you can explain what happens from typing a URL to the page loading.
  - [ ] IP addressing & subnetting. Done when: you split a /24 into 4 subnets by hand in 5 minutes.
  - [ ] DNS (BIND or CoreDNS). Done when: you run an internal zone and debug it with dig.
  - [ ] HTTP / HTTPS. Done when: you read curl -v output and know the common status codes.
  - [ ] TLS & certificates with an internal CA. Done when: you issue a cert from your own CA and a client trusts it.
  - [ ] DHCP, NAT, routing (VLANs: concept only). Done when: a router VM connects two subnets with NAT.
  - [ ] VLAN depth. Done when: you configure trunking and inter-VLAN routing across switches. (STRETCH: first things to cut)
  - [ ] Firewalls (nftables, iptables, ufw). Done when: you have a default-deny ruleset with logging.
  - [ ] VPN (WireGuard). Done when: a client tunnel works.
  - [ ] Troubleshooting (ping, traceroute, curl, dig, ss, tcpdump). Done when: you isolate DNS vs routing vs firewall vs app in a "site is down"
        drill.
  - [ ] Project: two-subnet network with router, DHCP, internal DNS, firewall and WireGuard, with a diagram.
- [ ] 6.  Docker [W10-W12, 80h]
  - [ ] Images, containers, Dockerfile. Done when: you containerize an app you didn't write.
  - [ ] Volumes & networking. Done when: data survives a container rebuild.
  - [ ] Docker Compose. Done when: a multi-service stack starts with one command.
  - [ ] Multi-stage builds & image best practices. Done when: image is small, non-root, with a .dockerignore.
  - [ ] Private registry (Registry, Harbor, GitLab Registry). Done when: push/pull works with auth and TLS.
  - [ ] Docker Hub is blocked: pull-through mirrors, skopeo/crane, docker save/load. Done when: you move an image to an isolated host in three
        different ways.
  - [ ] Image scanning (Trivy). Done when: a scan fails a build on high-severity findings.
  - [ ] Project: 3-tier app (web, API, DB) in Compose with images from your own registry. Use Mava's back end and Amir's React front end, and write
        the Compose file yourself.
- [ ] 7.  Reverse Proxy & TLS [W12-W14, 48h]
  - [ ] Reverse vs forward proxy. Done when: you can explain both with a diagram.
  - [ ] Nginx. Done when: vhosts, TLS, rate limiting, upstreams and logs are configured.
  - [ ] HAProxy. Done when: an L7 load balancer with health checks and stats page works.
  - [ ] TLS termination (public ACME where reachable, internal CA otherwise). Done when: certificates renew automatically.
  - [ ] Load balancing algorithms & health checks. Done when: you can explain and test round-robin vs least-conn.
  - [ ] Project: put the Docker 3-tier app behind HAProxy + Nginx with TLS and 2 replicas, and survive killing one.
- [ ] 8.  CI/CD [W14-W16, 80h]
  - [ ] Pipeline concepts (build, test, deploy). Done when: you can draw a pipeline for any app.
  - [ ] Self-hosted GitLab CE + Runner (Docker executor), already built by Mava. Done when: a merge triggers build, test, image push and deploy to a
        lab VM.
  - [ ] GitLab CI depth (rules, artifacts, cache, environments, protected variables, templates). Done when: no copy-pasted jobs remain.
  - [ ] Project: pipeline that builds, scans with Trivy, pushes to your registry, deploys, and rolls back on failure.
- [ ] 9.  Monitoring Basics [W16-W17, 48h]
  - [ ] Prometheus, node_exporter, PromQL basics. Done when: you query CPU, memory and disk per host.
  - [ ] Grafana dashboards. Done when: a dashboard shows the lab's health at a glance.
  - [ ] Zabbix. Done when: host, template, trigger and alert all work.
  - [ ] Logging basics (journald, rsyslog, logrotate, structured logs). Done when: logs rotate and ship to one place.
  - [ ] Project: dashboard plus 3 alerts (disk over 85%, service down, high latency) on the lab.
- [ ] 10. L2: Automation (Ansible) [W16-W17, 48h]
  - [ ] Ansible (inventory, playbooks, roles, handlers, Jinja2 templates). Done when: a role configures a server from blank.
  - [ ] Idempotency & check mode. Done when: a second run reports 0 changed.
  - [ ] Ansible Vault. Done when: secrets are encrypted in the repo.
  - [ ] Intermediate Python (pytest, packaging, logging, API clients). Done when: your CLI has tests.
  - [ ] Project: roles that turn a blank VM into a hardened web server with Nginx and node_exporter.
- [ ] L1 Checkpoint + Virtualization stretch + buffer [W17, 48h]
  - [ ] Portfolio repo contains all L1 projects with README and diagram (write each README when you finish its project, not at the end)
  - [ ] 2 mock interviews (Linux, networking, "site is down" scenario), run in the team session
  - [ ] Virtualization [W17, 14h, STRETCH: first thing to cut]
    - [ ] VMware vSphere/ESXi concepts (snapshots, HA, vMotion, resource pools). Done when: you can explain each.
    - [ ] Proxmox/KVM as a user of Mava's lab: live-migrate a VM, restore from backup. Done when: you did both.

## After week 17

Continue with ROADMAP.md. First finish what was skipped here (OpenVPN, Cisco/GNS3, hardware basics, storage), then start LEVEL 2 at section 11.

## If you fall behind

Add weekend hours first. If that is not possible, cut in this order:

1. Virtualization (the stretch block, 14 h)
2. Linux perf tuning depth
3. Network VLAN depth
4. Monitoring Zabbix
5. CI/CD depth

Tell the group in the next session. Do not silently skip "Done when" checks.
