# 🛠️ Cloud-Native & DevOps Infrastructure Lab

An ultra-lean, high-efficiency DevOps & Kubernetes local engineering sandbox. Built, hardened, and maintained entirely on bare-metal architecture using strict resource-optimisation and declarative infrastructure patterns.

## 🎛️ Architecture Overview

  [ GitHub Webhook ] ──( via ngrok )──> [ Jenkins (Win 11 Host) ]
                                                   │
                                            ( Pipeline Execution )
                                                   ▼
  [ Windows 11 File Mounts ] <───────> [ WSL2 Kernel v2.7.3 (Stable) ]
  ( Physical C:, D:, E: Drives )                    │
                                            ( systemd / cgroups v2 )
                                                   ▼
                                       [ Standalone Docker Engine ]
                                                   │
                                             ( containerd )
                                                   ▼
                                       [ KinD Multi-Node Cluster ]
                                        ( Kubernetes v1.35 Nodes )
                                                   │
                                       [ Portainer Business Edition ]
                                        ( State & Pod Observability )

## 🚀 Hardening & Optimisation Highlights
* Zero-Wrapper Performance: Bypassed Docker Desktop overhead by running a native standalone Docker engine inside WSL2 managed directly by systemd (cgroups v2).
* Kernel & Runtime Version Locking: Hardened against environment drift and upstream hypervisor bugs (e.g., WSL 2.7.8 I/O regression) by pinning WSL to v2.7.3 and executing `apt-mark hold` on core `docker` and `containerd` packages.
* Defensive Resource Management: Optimized a strict 12GB RAM layout by running swap-free, capping `systemd-journald` at 200MB, and enforcing custom json-file log rotation rules to protect host SSD life.
* Automated CI/CD Integration: Configured an event-driven `ngrok` pipeline forwarding public GitHub repository webhooks to an automated host-level Jenkins engine for instant KinD deployment cycles.

## 🌐 Enterprise & Cloud Architecture Projects
* HA Kubernetes The Hard Way (GCP): Bootstrapped a Highly Available production-grade control plane completely from scratch on Google Cloud Platform. Manually engineered the PKI infrastructure, bootstrap certificates, network routing, api-server load balancing, and data-encryption layers without configuration abstraction tools.

Enterprise Blueprint Translation: Mapping 15+ years of core enterprise ITSM logic (BMC Remedy Developer/Admin) into clean, immutable, declarative Infrastructure-as-Code (IaC) architectures.

📫 Status: Dual South African & British Citizen | Available for UK, EU, and SA Contract & Permanent roles (No sponsorship required).
