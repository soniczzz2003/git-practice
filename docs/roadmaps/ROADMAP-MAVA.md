# Mava Roadmap (4-month plan)

> Based on ROADMAP.md. "Done when", "Project" and level tags mean the same thing here. Week 1 starts Sat 31 Oct 2026. Week 17 ends Fri 26 Feb 2027.
> Budget: 70 h/week (10 h x 7 days). 17 weeks = 1190 hours. ~1164 h solo after the 90-min weekly team session and the 2 h/week teaching cap. Goal: full
> trimmed L2 by week 17, ready to apply for mid-level (platform owner of the shared lab). Amir and Sonic are blocked on your deliverables (see Dependencies).
> Hour estimates are guesses (base hours x 1.1). Log actual hours in the table below and recalibrate at the end of week 4. Extra hours go to depth and
> buffer (see section targets below). Restore cut items as uncut extras: Jenkins (full, not compare), Nexus (full), MongoDB, RabbitMQ, IAM/SSO, OpenTofu.
> Add depth to each L2 section. All of LEVEL 3 in ROADMAP.md is out of scope; cloud concepts reading is stretch only.

## Week by week

| Week | Starts | Focus                                                                   | Target h | Actual h |
| ---- | ------ | ----------------------------------------------------------------------- | -------- | -------- |
| 1    | Oct 31 | Lab, GitLab CE, offline toolkit. Placement audit. Start Linux gaps      | 70       |          |
| 2    | Nov 7  | Linux gaps end. Network                                                 | 70       |          |
| 3    | Nov 14 | Network ends. Docker gaps (private registry live). Reverse proxy starts | 70       |          |
| 4    | Nov 21 | Reverse proxy and TLS. CI/CD starts (Runner, GitLab CI)                 | 70       |          |
| 5    | Nov 28 | CI/CD (Jenkins full now). Monitoring starts                             | 70       |          |
| 6    | Dec 5  | Monitoring ends. Virtualization                                         | 70       |          |
| 7    | Dec 12 | Virtualization ends. L1 checkpoint. Ansible starts                      | 70       |          |
| 8    | Dec 19 | Ansible ends. Kubernetes starts                                         | 70       |          |
| 9    | Dec 26 | Kubernetes                                                              | 70       |          |
| 10   | Jan 2  | Kubernetes. Helm/GitOps starts                                          | 70       |          |
| 11   | Jan 9  | Helm, Kustomize, Argo CD. Terraform starts                              | 70       |          |
| 12   | Jan 16 | Terraform/OpenTofu ends. Observability depth starts                     | 70       |          |
| 13   | Jan 23 | Observability depth                                                     | 70       |          |
| 14   | Jan 30 | Observability ends. Databases                                           | 70       |          |
| 15   | Feb 6  | Databases end. Security starts (+IAM/SSO)                               | 70       |          |
| 16   | Feb 13 | Security ends. Backup and DR                                            | 70       |          |
| 17   | Feb 20 | L2 checkpoint, portfolio write-ups, buffer                              | 70       |          |

Approx section hour targets (pre-recalibration): Lab/Git host/offline toolkit 30; Placement audit 8; Linux gap-fill 40 (cap); Network 90; Docker gap-fill 25; Reverse proxy/TLS 55; CI/CD 90 (Jenkins full); Monitoring 55; Virtualization 55; L1 checkpoint 12; L2 Ansible 75; K8s 190; Helm/Kustomize/GitOps 75; IaC 70 (OpenTofu full); Observability depth 80; Databases 110; Security 65 (IAM/SSO full); Backup & DR 40; L2 checkpoint 16. Sum ≈ 1181 h ≤ 17 × 70 h, remainder is explicit buffer. Recalibrate from logged actual hours at end of week 4.

## Dependencies (other people are blocked on these)

- [ ] End of week 1: Proxmox host, WireGuard access for all three, VM template, GitLab CE as the team Git host (Amir starts Git in week 1, Sonic in week 2)
- [ ] End of week 3: private registry with auth and TLS, internal DNS, offline mirrors working (Amir starts Docker in week 9)
- [ ] End of week 5: GitLab Runner and container registry working, shared 3-tier app repo ready (Amir and Sonic use it from week 9-10)

## Rules

- You do every "Done when" yourself. Testing out means you passed the check, not that you assume you would.
- Failed audit items consume the gap-fill budgets (Linux 40 h, Docker 25 h). If failures exceed those, take hours from the buffer, then use the cut
  order at the bottom.
- Teaching is capped at 2 h/week. Review Amir's and Sonic's merge requests and unblock them. Do not do one-to-one lessons or their checks.
- One 90-minute team session per week: 30 min live demos, 30 min teach-back, 30 min MR review and planning. It counts toward your 70 hours.
- Mava delivers before Amir (Docker W9) and Sonic (Docker W10) consume the shared registry and 3-tier app repo.
- Write each project README when you finish its project, not at the end.

## 0. Lab, Git Host & Offline Toolkit [W1, 30h, build first]

- [ ] Hardware: one machine, 8+ cores, 32 GB RAM (16 GB bare minimum), 500 GB+ SSD, virtualization enabled in BIOS. Done when: nested virtualization
      works.
- [ ] Hypervisor: Proxmox, or KVM/libvirt on Ubuntu. Done when: you can create, snapshot, clone and destroy a VM from both CLI and web UI.
- [ ] Base VM template (Ubuntu LTS, cloud-init, SSH keys only). Done when: a cloned VM is reachable by SSH within 2 minutes.
- [ ] WireGuard access for all three of you. Done when: every member can SSH into a lab VM from home.
- [ ] Git host: GitLab CE (users, groups, protected main, MR required). Done when: Amir and Sonic can open and merge an MR in the team notes repo.
- [ ] Offline toolkit: local apt mirror/cache, pull-through registry or Harbor proxy, Nexus for pip/npm/Maven, archive of ISOs, packages and Helm
      charts. Done when: a lab VM with no direct internet can still install packages and pull images through your own mirrors.
- [ ] Offline documentation (man pages, tldr, kubectl explain, offline docsets). Done when: you can look up syntax with the internet off.
- [ ] Project: the whole lab is documented in a repo and can be rebuilt from scratch.

## Placement Audit [W1, 8h]

> Pass = tick and skip. Fail = schedule it inside the Linux or Docker gap-fill budget.

- [ ] Git. Done when: full cycle without notes, a real conflict resolved, 5 commits squashed with interactive rebase, an MR opened and reviewed.
- [ ] Bash. Done when: scripts take and validate arguments, top 10 IPs extracted from a large log, shellcheck reports zero warnings, a backup script
      runs from a systemd timer.
- [ ] Python basics. Done when: a 100-line script without copy-pasting, a CLI calling an API (requests, argparse), a health-check script sending to a
      chat webhook.
- [ ] Docker basics. Done when: you containerize an app you didn't write, data survives a rebuild, a Compose stack starts with one command, image is
      small and non-root.
- [ ] Linux basics. Done when: you pass the Linux lines below (failures become the gap-fill list).

## LEVEL 1

- [ ] 2.  Linux gap-fill [W1-W2, 40h cap, only failed items]
  - [ ] Filesystem, permissions, ACLs, umask. Done when: you can fix permission problems without trial and error.
  - [ ] Users, groups, sudo. Done when: you can create a restricted admin user from scratch.
  - [ ] Processes & signals. Done when: you can find and stop a runaway process and explain load average.
  - [ ] Package management (apt, dnf) + local repos/mirrors. Done when: you built and used a local mirror.
  - [ ] systemd & services. Done when: you wrote a unit file with restart policy and read its journal.
  - [ ] Cron & timers. Done when: a systemd timer runs a job and logs its output.
  - [ ] Disk, LVM & mounts. Done when: you extend an LVM volume online and recover from a broken fstab.
  - [ ] Performance tuning & patching. Done when: you diagnose high CPU, memory or IO with top/vmstat/iostat.
  - [ ] Ubuntu/Debian first, then Rocky/Alma. Done when: the same task works on both families.
  - [ ] SSH & keys. Done when: key-only login, ssh config, jump host and port forwarding all work.
  - [ ] Project: harden and document a fresh server (users, SSH, firewall, unattended updates).
- [ ] 3.  Network (Network+ roadmap) [W2-W3, 90h]
  - [ ] OSI & TCP/IP. Done when: you can explain what happens from typing a URL to the page loading.
  - [ ] IP addressing & subnetting. Done when: you split a /24 into 4 subnets by hand in 5 minutes.
  - [ ] DNS (BIND or CoreDNS). Done when: you run an internal zone and debug it with dig.
  - [ ] HTTP / HTTPS. Done when: you read curl -v output and know the common status codes.
  - [ ] TLS & certificates with an internal CA. Done when: you issue a cert from your own CA and a client trusts it.
  - [ ] DHCP, NAT, routing, VLANs. Done when: a router VM connects two subnets with NAT.
  - [ ] Firewalls (nftables, iptables, ufw). Done when: you have a default-deny ruleset with logging.
  - [ ] VPN (WireGuard). Done when: a client tunnel works (already built in the lab).
  - [ ] Troubleshooting (ping, traceroute, curl, dig, ss, tcpdump). Done when: you isolate DNS vs routing vs firewall vs app in a "site is down"
        drill.
  - [ ] Project: two-subnet network with router, DHCP, internal DNS, firewall and WireGuard, with a diagram.
- [ ] 6.  Docker gap-fill [W3, 25h]
  - [ ] Private registry (Registry, Harbor, GitLab Registry). Done when: push/pull works with auth and TLS.
  - [ ] Docker Hub is blocked: pull-through mirrors, skopeo/crane, docker save/load. Done when: you move an image to an isolated host in three
        different ways.
  - [ ] Image scanning (Trivy). Done when: a scan fails a build on high-severity findings.
  - [ ] Project: your FastAPI + Postgres backend runs from Compose with its image in the private registry. This is the shared app Amir and Sonic build
        on.
- [ ] 7.  Reverse Proxy & TLS [W3-W4, 55h]
  - [ ] Reverse vs forward proxy. Done when: you can explain both with a diagram.
  - [ ] Nginx. Done when: vhosts, TLS, rate limiting, upstreams and logs are configured.
  - [ ] HAProxy. Done when: an L7 load balancer with health checks and stats page works.
  - [ ] TLS termination (public ACME where reachable, internal CA otherwise). Done when: certificates renew automatically.
  - [ ] Load balancing algorithms & health checks. Done when: you can explain and test round-robin vs least-conn.
  - [ ] Keepalived / VRRP (extra, not in ROADMAP.md). Done when: a virtual IP fails over in under 5 seconds when you kill the primary.
  - [ ] Project: put the 3-tier app behind HAProxy + Nginx with TLS and 2 replicas, and survive killing one.
- [ ] 8.  CI/CD [W4-W5, 90h]
  - [ ] Pipeline concepts (build, test, deploy). Done when: you can draw a pipeline for any app.
  - [ ] Self-hosted GitLab CE + Runner (Docker executor). Done when: a merge triggers build, test, image push and deploy to a lab VM.
  - [ ] GitLab CI depth (rules, artifacts, cache, environments, protected variables, templates). Done when: no copy-pasted jobs remain.
  - [ ] Nexus (full, not compare). Done when: pip/npm/Maven dependencies resolve through your proxy repository.
  - [ ] Jenkins (full, not compare). Done when: the same pipeline is rebuilt as a Jenkinsfile.
  - [ ] Project: pipeline that builds, scans with Trivy, pushes to your registry, deploys, and rolls back on failure.
- [ ] 9.  Monitoring Basics [W5-W6, 55h]
  - [ ] Prometheus, node_exporter, PromQL basics. Done when: you query CPU, memory and disk per host.
  - [ ] Grafana dashboards. Done when: a dashboard shows the lab's health at a glance.
  - [ ] Zabbix. Done when: host, template, trigger and alert all work.
  - [ ] Logging basics (journald, rsyslog, logrotate, structured logs). Done when: logs rotate and ship to one place.
  - [ ] Project: dashboard plus 3 alerts (disk over 85%, service down, high latency) on the lab.
- [ ] 10. Virtualization & Hardware [W6-W7, 55h]
  - [ ] VMware vSphere/ESXi concepts (snapshots, HA, vMotion, resource pools). Done when: you can explain each; hands-on if you can get a host,
        otherwise practice the equivalents in Proxmox.
  - [ ] Proxmox/KVM: clustering, storage, live migration, backups. Done when: you live-migrate a VM between nodes.
  - [ ] Storage basics (NFS, iSCSI, RAID, Ceph overview). Done when: a VM runs from shared storage.
  - [ ] Hardware basics (IPMI/iDRAC, RAID, datacenter basics). Done when: you can read a server spec sheet and explain it.
  - [ ] Project: 2-node nested Proxmox cluster with shared storage, one live migration and one restore from backup.
- [ ] L1 Checkpoint [W7, 12h]
  - [ ] Portfolio repo contains all L1 projects with README and diagram
  - [ ] 2 mock interviews (Linux, networking, "site is down" scenario), run in the team session

## LEVEL 2 (trimmed, uncut extras restored)

- [ ] 11. Automation [W7-W8, 75h]
  - [ ] Ansible (inventory, playbooks, roles, handlers, Jinja2 templates). Done when: a role configures a server from blank.
  - [ ] Idempotency & check mode. Done when: a second run reports 0 changed.
  - [ ] Ansible Vault. Done when: secrets are encrypted in the repo.
  - [ ] Intermediate Python (pytest, packaging, logging, API clients). Done when: your CLI has tests.
  - [ ] Ansible depth. Done when: you maintain a multi-role repo with separate environments and reusable roles. (depth, cut if behind)
  - [ ] Project: roles that turn a blank VM into a hardened web server with Nginx and node_exporter.
- [ ] 12. Kubernetes on-prem [W8-W11, 190h]
  - [ ] Docker Swarm basics (seen in 2 postings, 4h). Done when: a 3-node Swarm runs a replicated service with a rolling update.
  - [ ] Architecture & core objects (Pod, Deployment, Service). Done when: you can explain every component in a running cluster.
  - [ ] Bootstrapping (kubeadm, then Kubespray). Done when: Kubespray builds the same cluster from a playbook.
  - [ ] Running without public registries (containerd mirrors, private registry pull secrets, mirrored registry.k8s.io images). Done when: cluster
        nodes have no direct internet and everything still starts.
  - [ ] CNI (Calico, Cilium) & NetworkPolicy. Done when: a policy blocks traffic between namespaces and you prove it.
  - [ ] ConfigMaps & Secrets. Done when: config changes without rebuilding images.
  - [ ] Ingress (Nginx Ingress) + MetalLB. Done when: services get external IPs and TLS on bare metal.
  - [ ] Persistent volumes & StatefulSets (Longhorn, Rook-Ceph or NFS). Done when: a database pod survives rescheduling with data intact.
  - [ ] RBAC & namespaces. Done when: a user can only touch their own namespace.
  - [ ] Probes, limits, autoscaling (HPA). Done when: load test scales pods up and back down.
  - [ ] Cluster operations (upgrades, etcd backup/restore, drain). Done when: you restore a cluster from an etcd snapshot.
  - [ ] Kubernetes troubleshooting. Done when: you fix CrashLoopBackOff, ImagePullBackOff, Pending and DNS failures in under 10 minutes each.
  - [ ] K8s depth. Done when: you run a multi-node HA control plane and debug a control-plane failure. (depth, cut if behind)
  - [ ] Project: the 3-tier app on your cluster with Ingress + TLS, persistent DB, HPA, NetworkPolicies, and a surviving node drain.
- [ ] 13. Helm, Kustomize & GitOps [W10-W11, 75h]
  - [ ] Helm (writing your own chart, using mirrored charts/images). Done when: you install a mirrored third-party chart offline.
  - [ ] Kustomize overlays. Done when: dev and staging differ only by overlay.
  - [ ] Git internals. Done when: you can explain objects, refs and the reflog.
  - [ ] Argo CD. Done when: apps auto-sync from Git, self-heal, and roll back by reverting a commit.
  - [ ] Project: Argo CD deploys dev/staging overlays from GitLab, and your pipeline updates the image tag.
- [ ] 14. IaC [W11-W12, 70h]
  - [ ] Terraform: providers, resources, variables, outputs. Done when: you create and destroy lab VMs from code.
  - [ ] State & remote backends (GitLab-managed state or MinIO S3). Done when: two people can safely apply in turn.
  - [ ] Modules. Done when: one module is reused for 3 different VMs.
  - [ ] Offline provider/binary mirrors (CLI config filesystem or network mirror). Done when: `init` works on a host with no registry access.
  - [ ] OpenTofu (full, not compare). Done when: the same config applies under both.
  - [ ] Practice targets: Proxmox or vSphere provider, plus Hetzner or an Iranian cloud if you can access one.
  - [ ] Project: one command builds the VMs, Ansible configures them, Kubespray installs Kubernetes.
- [ ] 15. Observability Depth [W12-W14, 80h]
  - [ ] ELK / Elasticsearch operations (index lifecycle, shard sizing). Done when: logs from all lab hosts are searchable centrally.
  - [ ] Alertmanager (routing, silences, inhibition). Done when: alerts reach the right person with the right severity.
  - [ ] Sentry (self-hosted). Done when: app exceptions show up with stack traces.
  - [ ] Custom exporters. Done when: you expose a metric from your own script.
  - [ ] SLI / SLO / error budgets. Done when: you defined an SLO and a dashboard for it.
  - [ ] On-call practice (runbooks, escalation, postmortems). Done when: you run a game day and write the postmortem.
  - [ ] Observability depth. Done when: you operate a multi-cluster logging stack and tune retention/index lifecycle. (depth, cut if behind)
  - [ ] Project: central logging, metrics and alerts for the Kubernetes lab, with an SLO dashboard.
- [ ] 16. Databases & Queues [W14-W15, 110h]
  - [ ] SQL basics (audit only). Done when: joins, indexes and EXPLAIN make sense to you.
  - [ ] PostgreSQL (backups, WAL, streaming replication, tuning). Done when: you restore to a point in time.
  - [ ] MySQL / MariaDB / Galera. Done when: a Galera cluster survives a node loss.
  - [ ] Redis (persistence, Sentinel/Cluster). Done when: failover works under a kill test.
  - [ ] MongoDB replica set. Done when: a primary election happens and the app recovers.
  - [ ] RabbitMQ (clustering, queues, monitoring). Done when: a queue survives a node restart without message loss.
  - [ ] Databases depth. Done when: you tune PostgreSQL for a production-like read/write workload and document the settings. (depth, cut if behind)
  - [ ] Project: HA Postgres with a failover test and a point-in-time restore, fully monitored.
- [ ] 17. Security [W15-W16, 65h]
  - [ ] Linux hardening (CIS-style, Lynis). Done when: every lab VM scores above your agreed baseline.
  - [ ] Firewall policy & segmentation. Done when: each tier only talks to what it must.
  - [ ] Container security (non-root, read-only FS, seccomp, Trivy gate in CI). Done when: the gate blocks a vulnerable image.
  - [ ] Secrets management (SOPS, Sealed Secrets). Done when: no plaintext secrets exist in any repo.
  - [ ] PKI (internal CA, rotation). Done when: you rotate an expiring cert without downtime.
  - [ ] IAM on-prem (LDAP, FreeIPA, Keycloak). Done when: GitLab and Grafana log in through one SSO.
  - [ ] Security depth. Done when: you run Lynis/CIS benchmarks across the lab and remediate findings. (depth, cut if behind)
  - [ ] Project: security review of the whole lab with a written findings list and fixes.
- [ ] 18. Backup & Disaster Recovery [W16, 40h]
  - [ ] Backup strategies (3-2-1, Borg/Restic, Velero, DB dumps). Done when: every stateful component has a tested restore.
  - [ ] RPO / RTO & DR planning. Done when: you have a written plan with measured numbers.
  - [ ] Project: destroy the Kubernetes lab and rebuild it from Git + backups, recording the RTO.
- [ ] L2 Checkpoint [W16-W17, 16h]
  - [ ] Portfolio has all L2 projects, each with a short English write-up
  - [ ] Mock interviews on Kubernetes troubleshooting, CI/CD design and "design an on-prem platform"
  - [ ] Apply for mid-level roles using the lab as your evidence

## Not in the 4-month plan

- Loki, Flux, Kafka, InfluxDB, supply chain security (SBOM, signing), Vault, Cisco/GNS3
- All of LEVEL 3 in ROADMAP.md (architecture, SRE, advanced platform, cloud concepts). Cloud concepts reading is stretch only; L3 is out of scope.

## If you fall behind, cut in this order

1. Uncut extras (Jenkins/Nexus full, MongoDB, RabbitMQ, IAM/SSO, OpenTofu)
2. Observability depth
3. Databases MongoDB/RabbitMQ
4. Security IAM/SSO
5. K8s depth

Do not silently skip "Done when" checks; tell the group in the next session.
