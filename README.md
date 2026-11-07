<!-- ════════════════════════════════════ HEADER ════════════════════════════════════ -->
<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:000000,40:0f2027,75:203a43,100:00f7ff&height=220&section=header&text=EFE%20TA%C5%9EKIRAN&fontSize=56&fontColor=ffffff&fontAlignY=36&animation=fadeIn&desc=Backend%20%E2%80%A2%20Cloud%20%E2%80%A2%20Networks%20%E2%80%A2%20Systems%20down%20to%20the%20silicon&descSize=17&descAlignY=58" />
</p>

<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=22&duration=2600&pause=700&color=00F7FF&center=true&vCenter=true&width=860&lines=%24+ssh+efe%40prod+--+building+backends+that+stay+up;%24+kubectl+get+pods+%7C+grep+Running;%24+tcpdump+-i+eth0+'tcp+port+443';%24+perf+stat+--+cache-misses+matter;%24+git+push+origin+main+%23+ship+it" />
</p>

<p align="center">
  <img src="https://komarev.com/ghpvc/?username=Tsknefe&label=PROFILE%20VIEWS&color=00f7ff&style=flat-square&labelColor=0d1117" />
  <img src="https://img.shields.io/github/followers/Tsknefe?style=flat-square&label=FOLLOWERS&color=00f7ff&labelColor=0d1117" />
  <img src="https://img.shields.io/github/stars/Tsknefe?style=flat-square&label=STARS&color=00f7ff&labelColor=0d1117" />
  <img src="https://img.shields.io/badge/STATUS-OPEN%20TO%20OPPORTUNITIES-00c853?style=flat-square&labelColor=0d1117" />
  <img src="https://img.shields.io/badge/UPTIME-99.99%25-00f7ff?style=flat-square&labelColor=0d1117" />
</p>

<p align="center">
  <img src="https://skillicons.dev/icons?i=python,cs,dotnet,c,postgres,redis,docker,kubernetes,terraform,aws,azure,gcp,nginx,cloudflare,linux,bash,raspberrypi,arduino,githubactions,git&perline=10&theme=dark" />
</p>

---

## `~ $ neofetch`

```text
  ███████╗████████╗       efe@tsknefe
  ██╔════╝╚══██╔══╝       ──────────────────────────────────────────────────
  █████╗     ██║          Role ........ Backend & Systems Engineer
  ██╔══╝     ██║          Edu ......... B.Sc. Computer Engineering
  ███████╗   ██║          Kernel ...... Linux (x86_64 · aarch64)
  ╚══════╝   ╚═╝          Shell ....... bash · zsh · tmux
                          Langs ....... Python · C# · C · SQL · JavaScript
  ┌───────────────┐       Runtime ..... FastAPI · ASP.NET Core · ABP
  │ ▓▓▓▓▓▓▓▓▓▓▓▓▓ │       Storage ..... PostgreSQL · Redis · SQLite
  │ ▓ systems   ▓ │       Infra ....... Docker · Kubernetes · Terraform
  │ ▓ thinking  ▓ │       CI/CD ....... GitHub Actions
  │ ▓▓▓▓▓▓▓▓▓▓▓▓▓ │       Network ..... TCP/IP · TLS 1.3 · WSS · Nginx · WireGuard
  └───────┬───────┘       Metal ....... CPU caches · memory layout · ARM · MCU
      ════╧════           Motto ....... "Make it work, make it right, make it fast."
```

---

## 🧬 Full-Stack, Literally: From HTTP to Silicon

> I don't stop at the framework boundary. Every layer below the code I write is a layer that can fail, so I learn how it works.

```text
┌───────────────────────────────────────────────────────────────────────────┐
│ L7  APPLICATION    FastAPI · ASP.NET Core · ABP · REST · WebSockets       │
├───────────────────────────────────────────────────────────────────────────┤
│ L6  DOMAIN         DDD aggregates · invariants · domain events · UoW      │
├───────────────────────────────────────────────────────────────────────────┤
│ L5  DATA           PostgreSQL (MVCC, indexes, isolation) · Redis (cache)  │
├───────────────────────────────────────────────────────────────────────────┤
│ L4  PLATFORM       Docker · Kubernetes · Terraform · GitHub Actions       │
├───────────────────────────────────────────────────────────────────────────┤
│ L3  NETWORK        DNS · TCP/IP · TLS 1.3 · HTTP/2 · Nginx · WireGuard    │
├───────────────────────────────────────────────────────────────────────────┤
│ L2  OS             Linux · processes · syscalls · epoll · file systems    │
├───────────────────────────────────────────────────────────────────────────┤
│ L1  HARDWARE       x86_64 / ARM · Raspberry Pi · Arduino · GPIO · UART    │
├───────────────────────────────────────────────────────────────────────────┤
│ L0  SILICON        L1/L2/L3 caches · branch prediction · memory hierarchy │
└───────────────────────────────────────────────────────────────────────────┘
```

---

## ⚡ Anatomy of a Request

What actually happens between a user's click and a row in the database:

```text
  [ client ]
      │
      │ ① DNS ........... resolver ──► authoritative NS ──► A / AAAA record
      │ ② TCP ........... SYN ──► SYN/ACK ──► ACK                   (1 RTT)
      │ ③ TLS 1.3 ....... ClientHello ──► ServerHello + cert ──► keys (1 RTT)
      ▼
┌─────────────┐    ┌──────────────────┐    ┌──────────────────────────────┐
│  CDN / WAF  │───►│  Nginx (L7 LB)   │───►│  API  ·  FastAPI / .NET      │
│ DDoS · TLS  │    │ rate-limit · gzip│    │ auth ─► validate ─► handler  │
└─────────────┘    └──────────────────┘    └──────────────┬───────────────┘
                                                          │
                              ┌─────── cache hit ◄────────┤
                              │                           │ cache miss
                     ┌────────┴────────┐        ┌─────────▼──────────┐
                     │  Redis  (O(1))  │        │ PostgreSQL primary │
                     │  TTL · pub/sub  │        │  BEGIN … COMMIT    │
                     └─────────────────┘        └─────────┬──────────┘
                                                          │ WAL streaming
                                                ┌─────────▼──────────┐
                                                │  read replica(s)   │
                                                └────────────────────┘
```

---

## ☁️ Cloud & Network Topology

```text
                              ╔════════════════════╗
                              ║      INTERNET      ║
                              ╚═════════╤══════════╝
                                        │  HTTPS · WSS
                              ┌─────────▼──────────┐
                              │  Cloudflare Edge   │  TLS termination
                              │  CDN · WAF · DNS   │  DDoS mitigation
                              └─────────┬──────────┘
 ┌──────────────────────────────────────┼──────────────────────────────────┐
 │ VPC  10.0.0.0/16                     │                                  │
 │                          ┌───────────▼────────────┐                     │
 │ public  10.0.1.0/24      │   Nginx Ingress / LB   │                     │
 │                          └─────┬────────────┬─────┘                     │
 │ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─│─ ─ ─ ─ ─ ─ │ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ │
 │ private 10.0.2.0/24      ┌─────▼────┐  ┌────▼─────┐   ┌──────────────┐  │
 │  (Kubernetes)            │ api-pod  │  │ api-pod  │   │ worker-pods  │  │
 │                          │replica 1 │  │replica 2 │   │  async jobs  │  │
 │                          └─────┬────┘  └────┬─────┘   └──────┬───────┘  │
 │ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─│─ ─ ─ ─ ─ ─ │ ─ ─ ─ ─ ─ ─ ─ ─│─ ─ ─ ─ ─ │
 │ data    10.0.3.0/24      ┌─────▼────────────▼─────┐   ┌──────▼────────┐ │
 │  (no public route)       │  PostgreSQL + replica  │   │ Redis cluster │ │
 │                          └────────────────────────┘   └───────────────┘ │
 └─────────────────────────────────────────────────────────────────────────┘
          ▲
          │  WireGuard tunnel  (UDP 51820 · Curve25519 · ChaCha20)
 ┌────────┴────────────────────────────┐
 │  HOMELAB                            │
 │  Raspberry Pi ── monitoring · CI    │
 │  Arduino ─────── sensors via UART   │
 └─────────────────────────────────────┘
```

<table>
  <tr>
    <th width="33%">☁️ Cloud</th>
    <th width="33%">🌐 Network</th>
    <th width="33%">🔩 Hardware</th>
  </tr>
  <tr valign="top">
    <td>
      ▸ Containerized services: Docker ➜ Kubernetes<br/>
      ▸ Infrastructure as Code with Terraform<br/>
      ▸ Private subnets, secrets, least privilege<br/>
      ▸ CI/CD pipelines on GitHub Actions<br/>
      ▸ Horizontal scaling & health checks
    </td>
    <td>
      ▸ TCP/IP, DNS, subnetting & routing<br/>
      ▸ TLS 1.3, certificates, HTTPS everywhere<br/>
      ▸ Reverse proxy, load balancing, rate limiting<br/>
      ▸ WebSocket connections at scale<br/>
      ▸ Site-to-site VPN with WireGuard
    </td>
    <td>
      ▸ Cache-friendly data layouts<br/>
      ▸ Profiling CPU, memory & I/O bottlenecks<br/>
      ▸ Raspberry Pi edge nodes & homelab<br/>
      ▸ Embedded C on microcontrollers<br/>
      ▸ GPIO, UART, I²C, SPI
    </td>
  </tr>
</table>

---

## ⚙️ Tech Arsenal

<table>
  <tr>
    <td><b>🧠 Languages</b></td>
    <td>
      <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" />
      <img src="https://img.shields.io/badge/C%23-512BD4?style=for-the-badge&logo=csharp&logoColor=white" />
      <img src="https://img.shields.io/badge/C-A8B9CC?style=for-the-badge&logo=c&logoColor=black" />
      <img src="https://img.shields.io/badge/SQL-336791?style=for-the-badge&logo=postgresql&logoColor=white" />
      <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" />
      <img src="https://img.shields.io/badge/Bash-4EAA25?style=for-the-badge&logo=gnubash&logoColor=white" />
    </td>
  </tr>
  <tr>
    <td><b>🛰️ Backend</b></td>
    <td>
      <img src="https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white" />
      <img src="https://img.shields.io/badge/ASP.NET%20Core-512BD4?style=for-the-badge&logo=dotnet&logoColor=white" />
      <img src="https://img.shields.io/badge/ABP%20Framework-E8202A?style=for-the-badge" />
      <img src="https://img.shields.io/badge/Entity%20Framework-512BD4?style=for-the-badge&logo=dotnet&logoColor=white" />
    </td>
  </tr>
  <tr>
    <td><b>🗄️ Data</b></td>
    <td>
      <img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white" />
      <img src="https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white" />
      <img src="https://img.shields.io/badge/SQLite-003B57?style=for-the-badge&logo=sqlite&logoColor=white" />
      <img src="https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white" />
      <img src="https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white" />
    </td>
  </tr>
  <tr>
    <td><b>☁️ Cloud & Infra</b></td>
    <td>
      <img src="https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazonwebservices&logoColor=white" />
      <img src="https://img.shields.io/badge/Azure-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white" />
      <img src="https://img.shields.io/badge/GCP-4285F4?style=for-the-badge&logo=googlecloud&logoColor=white" />
      <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white" />
      <img src="https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white" />
      <img src="https://img.shields.io/badge/Terraform-844FBA?style=for-the-badge&logo=terraform&logoColor=white" />
      <img src="https://img.shields.io/badge/GitHub%20Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white" />
    </td>
  </tr>
  <tr>
    <td><b>🌐 Networking</b></td>
    <td>
      <img src="https://img.shields.io/badge/TCP%2FIP-0d1117?style=for-the-badge" />
      <img src="https://img.shields.io/badge/TLS%201.3-0d1117?style=for-the-badge&logo=letsencrypt&logoColor=white" />
      <img src="https://img.shields.io/badge/WebSockets-0d1117?style=for-the-badge&logo=socketdotio&logoColor=white" />
      <img src="https://img.shields.io/badge/Nginx-009639?style=for-the-badge&logo=nginx&logoColor=white" />
      <img src="https://img.shields.io/badge/Cloudflare-F38020?style=for-the-badge&logo=cloudflare&logoColor=white" />
      <img src="https://img.shields.io/badge/WireGuard-88171A?style=for-the-badge&logo=wireguard&logoColor=white" />
      <img src="https://img.shields.io/badge/Wireshark-1679A7?style=for-the-badge&logo=wireshark&logoColor=white" />
    </td>
  </tr>
  <tr>
    <td><b>🔩 Hardware</b></td>
    <td>
      <img src="https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black" />
      <img src="https://img.shields.io/badge/Raspberry%20Pi-A22846?style=for-the-badge&logo=raspberrypi&logoColor=white" />
      <img src="https://img.shields.io/badge/Arduino-00878F?style=for-the-badge&logo=arduino&logoColor=white" />
      <img src="https://img.shields.io/badge/ARM-0091BD?style=for-the-badge&logo=arm&logoColor=white" />
      <img src="https://img.shields.io/badge/Homelab-0d1117?style=for-the-badge&logo=proxmox&logoColor=E57000" />
    </td>
  </tr>
  <tr>
    <td><b>📐 Architecture</b></td>
    <td>
      <img src="https://img.shields.io/badge/DDD-0d1117?style=for-the-badge" />
      <img src="https://img.shields.io/badge/Clean%20Architecture-0d1117?style=for-the-badge" />
      <img src="https://img.shields.io/badge/Event--Driven-0d1117?style=for-the-badge" />
      <img src="https://img.shields.io/badge/Microservices-0d1117?style=for-the-badge" />
      <img src="https://img.shields.io/badge/REST-0d1117?style=for-the-badge" />
    </td>
  </tr>
</table>

---

## 🚀 Featured Projects

### 🏦 BankApiABP — Production-Style Banking Backend

<p>
  <img src="https://img.shields.io/badge/C%23-512BD4?style=flat-square&logo=csharp&logoColor=white" />
  <img src="https://img.shields.io/badge/.NET-512BD4?style=flat-square&logo=dotnet&logoColor=white" />
  <img src="https://img.shields.io/badge/ABP-E8202A?style=flat-square" />
  <img src="https://img.shields.io/badge/DDD-0d1117?style=flat-square" />
  <img src="https://img.shields.io/badge/EF%20Core-512BD4?style=flat-square" />
</p>

Banking backend built on **ABP Framework** with strict **Domain-Driven Design** boundaries, where correctness under concurrency matters more than anything else.

```text
 LAYERED ARCHITECTURE                       MONEY TRANSFER FLOW
 ────────────────────                       ───────────────────
 ┌──────────────────────────┐               POST /api/transfers
 │ HttpApi     controllers  │                    │
 ├──────────────────────────┤                    ▼
 │ Application  app services│◄── DTOs      [ Permission check ]
 ├──────────────────────────┤                    │
 │ Domain      aggregates   │◄── rules     [ Unit of Work: BEGIN ]
 │             invariants   │                    │
 │             domain events│               load Account A, Account B
 ├──────────────────────────┤                    │
 │ EF Core     repositories │               A.Withdraw()  B.Deposit()
 │             migrations   │               (invariants: balance ≥ 0)
 └────────────┬─────────────┘                    │
              ▼                             concurrency stamp check
        ┌───────────┐                       ├── conflict ─► rollback
        │PostgreSQL │                       └── ok ───────► COMMIT
        └───────────┘                                         │
                                                  structured log + audit
```

- **Modular domain services** with clear aggregate boundaries
- **Transaction management** via Unit of Work, so operations are all-or-nothing
- **Concurrency handling** that prevents lost updates on balances
- **Permission system** with role-based authorization
- **Structured logging** for full traceability

➡️ [`View repository`](https://github.com/Tsknefe/BankApiABP)

---

### 🧵 String Art Generator — Computer Vision Pipeline

<p>
  <img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/Computer%20Vision-5C3EE8?style=flat-square&logo=opencv&logoColor=white" />
  <img src="https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white" />
</p>

Turns any image into a **step-by-step nail sequence** for physical string art.

```text
  ┌─────────┐   ┌───────────┐   ┌────────────┐   ┌──────────────────┐   ┌──────────────┐
  │  image  │──►│ grayscale │──►│ circular   │──►│ greedy line      │──►│ nail sequence│
  │  input  │   │ + contrast│   │ crop + N   │   │ selection: pick  │   │ 0→117→42→... │
  └─────────┘   └───────────┘   │ nails ring │   │ darkest chord,   │   └──────────────┘
                                └────────────┘   │ subtract, repeat │
                                                 └──────────────────┘
```

➡️ [`Browse repositories`](https://github.com/Tsknefe?tab=repositories)

---

## 🛠️ Engineering Principles

<details>
<summary><b>▸ click to expand</b></summary>
<br/>

| # | Principle | In practice |
|:-:|---|---|
| 01 | **Correctness first** | Invariants live in the domain, not in controllers |
| 02 | **Idempotency** | Retries must never double-apply a write |
| 03 | **Explicit state** | State is persisted and auditable, never inferred |
| 04 | **Fail loudly** | Structured logs and clear error paths, no silent fallbacks |
| 05 | **Know the layer below** | Understand the network, OS and hardware your code runs on |
| 06 | **Measure, don't guess** | Profile before optimizing: CPU, memory, I/O, network |
| 07 | **Least privilege** | Private subnets, scoped tokens, minimal permissions |

</details>

---

## 📊 GitHub Telemetry

<p align="center">
  <img height="165" src="https://github-readme-stats.vercel.app/api?username=Tsknefe&show_icons=true&theme=tokyonight&hide_border=true&count_private=true&include_all_commits=true" />
  <img height="165" src="https://github-readme-stats.vercel.app/api/top-langs/?username=Tsknefe&layout=compact&theme=tokyonight&hide_border=true&langs_count=8" />
</p>

<p align="center">
  <img src="https://streak-stats.demolab.com/?user=Tsknefe&theme=tokyonight&hide_border=true" />
</p>

<p align="center">
  <img src="https://github-readme-activity-graph.vercel.app/graph?username=Tsknefe&theme=tokyo-night&hide_border=true&area=true" />
</p>

---

## 📡 Open a Connection

```text
$ nc -v efe.taskiran 443
Connection to efe.taskiran 443 port [tcp/https] succeeded!
```

<p align="center">
  <a href="https://github.com/Tsknefe"><img src="https://img.shields.io/badge/GitHub-0d1117?style=for-the-badge&logo=github&logoColor=white" /></a>
  <!-- 🔗 Replace with your LinkedIn profile URL -->
  <a href="https://www.linkedin.com/in/efe-ta%C5%9Fk%C4%B1ran-9378ba25b/"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" /></a>
  <!-- 🔗 Replace with your email -->
  <a href="mailto:taskiranefe5@gmail.com"><img src="https://img.shields.io/badge/Email-00f7ff?style=for-the-badge&logo=gmail&logoColor=0d1117" /></a>
</p>

<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:00f7ff,25:203a43,60:0f2027,100:000000&height=120&section=footer" />
</p>
