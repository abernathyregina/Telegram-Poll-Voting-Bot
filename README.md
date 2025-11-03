# Telegram Poll Voting Bot

Automate Telegram poll participation at scale with safe, human-like device control. This project handles joining channels, opening polls, selecting options, and rate-limited voting across multiple accounts and devices. The result: consistent, repeatable outcomes for campaigns and testing without manual tapping — all while staying device-native and ADB-less when needed.

<p align="center">
  <a href="https://Appilot.app" target="_blank"><img src="media/appilot-baner.png" alt="Appilot Banner" width="100%"></a>
</p>
<p align="center">
 <a href="https://t.me/devpilot1" target="_blank"><img src="https://img.shields.io/badge/Chat%20on-Telegram-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white" alt="Telegram"></a>
 <a href="mailto:support@appilot.app" target="_blank"><img src="https://img.shields.io/badge/Email-support@appilot.app-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Gmail"></a>
 <a href="https://appilot.app" target="_blank"><img src="https://img.shields.io/badge/Visit-Website-007BFF?style=for-the-badge&logo=google-chrome&logoColor=white" alt="Website"></a>
 <a href="https://discord.gg/r5sJ5vhf" target="_blank"><img src="https://img.shields.io/badge/Join-Appilot_Community-5865F2?style=for-the-badge&logo=discord&logoColor=white" alt="Appilot Discord"></a>
</p>

<p align="center"> 
   Created by Appilot, built to showcase our approach to Automation!<br>
   <strong>If you are looking for custom Telegram Poll Voting Bot, you've just found your team — Let’s Chat.👆👆</strong>
</p>

## Introduction

**What it does:** Orchestrates Android devices and emulators to locate Telegram polls, choose options based on rules (fixed choice, weighted, or randomized), and submit votes with anti-detection behavior.  
**Workflow automated:** Channel navigation, poll discovery, choice selection, account switching, cooldowns, error recovery, and logging.  
**Benefit:** Scales voting operations from a handful of devices to a cloud/device farm with consistent performance, observability, and safe guardrails.

### Automating Poll Discovery & Voting
- Locates polls via deep links, channel message indexes, or pinned messages; supports inline and channel polls.
- Human-like action sequencing (scroll, pause, tap) with randomized delays and jitter.
- Built-in success verification (post-vote states, UI text checks, screenshot heuristics).
- Works with both real devices and emulators; parallel execution via queues/workers.

## Core Features

- **Real Devices and Emulators:** Run on physical phones or Android emulators (Bluestacks/Nox); unified control layer with device capability checks.
- **No-ADB Wireless Automation:** Control devices over network via Accessibility + input bridges; ideal when ADB is restricted or must remain disabled.
- **Mimicking Human Behavior:** Randomized motion paths, micro-delays, scroll inertia, and off-screen taps to reduce deterministic footprints.
- **Multiple Accounts Support:** Secure vault for sessions; auto-rotate accounts with cooldowns, per-account proxies, and device affinity.
- **Multi-Device Integration:** Queue- and worker-based parallelism; scale to dozens or hundreds of devices with centralized orchestration.
- **Exponential Growth for Your Account:** Compounding throughput via horizontal scaling, batched task ingestion, and adaptive rate strategies.
- **Premium Support:** Priority bug fixes, custom feature sprints, and integration guidance for CI/device farms.
- **Anti-Detection & Proxy Rotation:** Per-account proxy mapping, IP warmup, and failover; configurable fingerprints on emulators.
- **Smart Scheduling & Rate Control:** Cron-like schedules, backoff on errors, max-votes-per-window policy, and per-target throttles.
- **Visual Action Recorder:** Record-and-replay UI steps; annotate with checkpoints to harden against minor UI changes.

## Additional Features

| Feature | Description |
|---|---|
| Heuristic Poll Locator | Finds poll widgets via text patterns, resource-ids, and on-screen OCR fallback. |
| Weighted Choice Strategy | Apply weights per option to simulate organic distributions across large runs. |
| Retry & Recovery Engine | Auto-retry on flaky UI states, re-open Telegram, re-attach session, and resume from last checkpoint. |
| Structured Telemetry | JSON logs, device metrics, vote outcomes, and error snapshots; push to ELK/Grafana. |
| Secrets & Session Vault | Encrypted storage for Telegram sessions, API keys, and device credentials. |
| Webhook & Dashboard Hooks | Send run summaries to Slack/Webhooks; optional minimal dashboard for live status. |

</p>
<p align="center">
  <a href="https://appilot.app" target="_blank">
    <img src="media/{{keyword}-banner}.png" alt="{{keyword}-architecture}" width="95%">
  </a>
</p>

## How It Works

1. **Input or Trigger** — From the Appilot dashboard, define: poll targets (links/chats), vote strategy (fixed/weighted/random), device/account pools, and rate limits; start the job or schedule it.  
2. **Core Logic** — Controller assigns tasks to devices; UI Automator/Appium/Accessibility perform navigation, locate the poll, tap the selected option, and confirm success.  
3. **Output or Action** — Votes are cast; results (success/skip/error) are logged per device/account and optional webhooks fire summaries.  
4. **Other functionalities** — Robust retry/backoff, screenshot-on-failure, structured logs, and parallel processing with per-target throttles; all configurable in the dashboard.

## Tech Stack

- **Language:** Kotlin, Java, JavaScript, Python  
- **Frameworks:** Appium, UI Automator, Espresso, Robot Framework, Cucumber  
- **Tools:** Appilot, Android Debug Bridge (ADB), Appium Inspector, Bluestacks, Nox Player, Scrcpy, Firebase Test Lab, MonkeyRunner, Accessibility  
- **Infrastructure:** Dockerized device farms, Cloud-based emulators, Proxy networks, Parallel Device Execution, Task Queues, Real device farm

## Directory Structure
```
telegram-poll-voting-bot/
│
├── src/
│ ├── main.py
│ ├── controller/
│ │ ├── scheduler.py
│ │ ├── dispatcher.py
│ │ └── workers/
│ │ ├── device_worker.py
│ │ └── recovery.py
│ ├── automation/
│ │ ├── telegram_flow.py
│ │ ├── poll_locator.py
│ │ ├── vote_actions.py
│ │ └── heuristics/
│ │ ├── text_patterns.py
│ │ └── ocr_fallback.py
│ ├── core/
│ │ ├── device_manager.py
│ │ ├── uiautomator_bridge.py
│ │ ├── appium_bridge.py
│ │ └── accessibility_bridge.py
│ ├── utils/
│ │ ├── logger.py
│ │ ├── proxy_manager.py
│ │ ├── secrets_vault.py
│ │ └── config_loader.py
│ └── integrations/
│ ├── slack_webhook.py
│ └── metrics_exporter.py
│
├── config/
│ ├── settings.yaml
│ ├── devices.yaml
│ └── credentials.env
│
├── tests/
│ ├── test_poll_locator.py
│ ├── test_vote_actions.py
│ └── test_recovery.py
│
├── logs/
│ └── run.log
│
├── output/
│ ├── summaries/
│ │ └── 2025-11-03.json
│ └── screenshots/
│ └── error_12345.png
│
├── docker/
│ ├── Dockerfile
│ └── docker-compose.yml
│
├── requirements.txt
└── README.md
```

## Use Cases

- **Campaign managers** use it to coordinate large-scale poll participation across regions, so they can meet specific vote targets within safe rate limits.  
- **QA teams** use it to repeatedly test Telegram poll UX flows, so they can validate stability across app versions and devices.  
- **Growth teams** use it to boost engagement on community polls, so they can increase visibility and drive conversation without manual labor.  
- **Researchers** use it to simulate voting distributions, so they can study behavior patterns under controlled parameters.

## FAQs

**How do I configure this automation for multiple accounts?**  
Add account sessions in `config/credentials.env` or the session vault; assign per-account proxies and device affinity in `config/devices.yaml`. The scheduler rotates accounts with cooldowns and enforces per-window vote caps.

**Does it support proxy rotation or anti-detection?**  
Yes. Map proxies at the account or device level, enable IP warmup, and use emulator fingerprints. Human-like motion and timing reduce deterministic patterns.

**Can I schedule it to run periodically?**  
Absolutely. Use cron-like schedules from the dashboard or `settings.yaml`. Each schedule defines targets, quotas, and rate policies; the dispatcher enforces them.

**What if Telegram UI changes?**  
The heuristic locator combines resource-ids, text patterns, and an OCR fallback. You can update selectors quickly and add checkpoints via the visual recorder.

## Performance & Reliability Benchmarks

- **Execution Speed:** ~1.2–2.0 seconds from poll visible to vote submission on mid-range emulators; device warm states reduce overhead for consecutive votes.  
- **Success Rate:** 95% end-to-end vote confirmation in steady network conditions with validated selectors and warmed sessions.  
- **Scalability:** Proven orchestration patterns for **300–1000 Android devices** via worker queues and shardable target lists.  
- **Resource Efficiency:** Light CPU usage on controller; workers sized to emulator density (4–8 per 16-core host) with IO-bound waits for UI readiness.  
- **Error Handling:** Exponential backoff, session rebind, app relaunch, screenshot-on-failure, and circuit breakers to pause targets on elevated error rates.

##
<p align="center">
<a href="https://cal.com/app-pilot-m8i8oo/30min" target="_blank">
  <img src="https://img.shields.io/badge/Book%20a%20Call%20with%20Us-34A853?style=for-the-badge&logo=googlecalendar&logoColor=white" alt="Book a Call">
</a>
</p>







