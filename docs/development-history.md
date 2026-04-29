# Development History

This repository preserves the filtered source commit history for the DeviceKit framework, reference app, simulator, and local launcher paths. The commit hashes below are the rewritten standalone-repository hashes, so they are directly visible in this repository with `git log`.

| Item | Value |
|---|---|
| Imported filtered commits | 110 commits |
| Source paths imported | `ava-devicekit/`, `simulator/`, `scripts/run-devicekit-local.sh` |
| Standalone repository | `JupiterXiaoxiaoYu/ava-devicekit` |

## Work Areas

| Area | Scope represented by the source commits |
|---|---|
| Framework runtime | App/session contract, manifest loading, HTTP and WebSocket gateways, ACK/outbox delivery, persistent runtime state, app-scoped runtime config |
| Provider system | Runtime-selectable ASR, LLM, TTS, market stream, chain adapter, execution provider, health reporting, and custom provider class loading |
| Firmware and simulator | Device protocol, firmware compatibility gateway, board SDK boundary, Scratch Arcade port, LVGL simulator, screenshot regression coverage |
| Ava Box reference app | Solana feed/search/spotlight, watchlist, signals, portfolio, paper and proxy execution, order history, limit order flow, kline refresh, numeric display policy |
| Control plane | Admin console, projects/apps/devices/customers/service plans, app-scoped users and devices, provider/service config, diagnostics, usage, OTA publishing |
| C-end flow | Customer wallet-signature login, purchase demo, activation cards/codes, device binding, customer portal layout |
| Developer experience | Userland templates, app templates, board/adaptor/provider scaffolds, DePIN/payment/oracle/signer examples, builder docs |

## Filtered Commit Worklog

### 2026-04-10

- `16d4bbb` first commit
- `57f4944` Fix spotlight live kline behavior and sync simulator/server
- `fce34ea` Refine FEED layout and update screenshot baselines
- `ba45d79` Add MiSans font support and refine feed layout
- `991d432` Stabilize AVE trading flows and simulator tests

### 2026-04-11

- `6d1437a` feat: refine spotlight top100 details
- `5ffa96b` refactor: polish feed overlay and harness support
- `085ddc2` feat: add Explorer signals and watchlist UI
- `477f645` fix: render spotlight watchlist star correctly
- `c07c03f` feat: split explorer and browse screens
- `326e806` fix: restore simulator verify target
- `3c7ff80` Remove browse compatibility routing
- `3fd4bcf` Remove dead feed browse logic

### 2026-04-12

- `bc8eba8` Add portfolio activity detail subview
- `940eb45` Polish AVE trade confirm and simulator flow

### 2026-04-13

- `68108a1` Revert simulator TinyTTF font loading
- `bc5c026` Fix simulator minimal verify harness
- `2bce308` Add AVE monorepo README navigation
- `f0cd72d` Rename product docs to Ava Box
- `bc364cc` Polish Ava Box branding

### 2026-04-27

- `1a84016` Add clean Ava DeviceKit framework
- `a292df6` Add clean DeviceKit shared UI runtime
- `db0375f` Document previous-runtime capability decisions
- `6afe5fc` Add standalone DeviceKit gateway flow
- `de6fab2` Split Ava Box app skills
- `b1b9513` Add manifest-driven DeviceKit runtime
- `646efe5` Add DeviceKit firmware compatibility runtime
- `dd2992a` Remove previous-runtime assistant branding from DeviceKit
- `1ab3d89` Complete DeviceKit framework boundaries
- `b802723` Add DeviceKit userland developer surface
- `957f99e` Complete DeviceKit provider and app boundaries
- `367fd1d` Make AI providers runtime selectable
- `92639ca` Close DeviceKit runtime integration gaps
- `fecd88f` Add production runtime manager and board SDK
- `dab02a8` Add custodial proxy wallet execution
- `ec16103` Migrate Ava Box UI runtime to DeviceKit
- `0f86321` Use real DeviceKit startup path by default
- `e6b712a` Keep gateway connected when TTS fails
- `06c1876` Add AliBL TTS runtime provider
- `7f6ca1a` Fix spotlight kline interval refresh
- `48644ea` Cover Ava Box UI key actions

### 2026-04-28

- `998ae97` Harden Ava Box screen context contracts
- `7d8e1f7` Add generic screen input context contracts
- `773007d` Route voice watchlist commands
- `e745232` Fix DashScope Qwen3 LLM fallback
- `67dd2ab` Route token introductions to LLM fallback
- `c9000d9` Use qwen3.5 flash as default LLM
- `b531c32` Handle firmware trade confirmations
- `781cd1c` Harden protocol and provider extension points
- `c8b14ac` Enable live L1S spotlight kline updates
- `236b1f6` Standardize numeric display notation
- `1c17ae5` Refine Solana table numeric layout
- `5c58eea` Widen Solana token symbol column
- `4d33302` Add headlines to browse signal rows
- `a5b7f50` Restore signal activity details
- `c9fc7f0` Compact signal buy sell badges
- `4309eef` Show scrolling signal token addresses
- `24e9e7e` Persist trade mode and restore Top100 data
- `4edb059` Hide paper source tags in portfolio rows
- `e55628d` Show paper account funds in portfolio
- `da4b275` Fix result success payload for confirms
- `9616ced` Restore paper trade estimates and portfolio values
- `af37f21` Fix paper sell estimates and accounting
- `7d9081a` Return to portfolio after paper sells
- `5a335c7` Show native SOL first in portfolio
- `7fed8c4` Make portfolio Y return to trending
- `6d134e9` Prevent native SOL duplicate portfolio rows
- `9a49d15` Restore portfolio avg and sell cash fallback
- `9675816` Fix paper sell cash and balance checks
- `da04ff1` Split open orders from order history
- `45850f0` Fill paper limit orders from market prices
- `bead197` Show order type in history rows
- `a246a5c` Restore spotlight back navigation source
- `08bfebb` Harden DeviceKit runtime persistence
- `f7712ff` Queue outbound device messages across gateways
- `453ec88` Add framework runtime contracts and reliable delivery
- `7af2f71` Complete DeviceKit framework runtime services
- `0793cfe` Report auto chain adapter health
- `544f4ef` Complete DeviceKit developer infra
- `bf3e50d` Finish DeviceKit infrastructure hardening
- `e332938` Upgrade DeviceKit admin console
- `e134abe` Add DeviceKit control plane MVP
- `a304f26` Add C-end hardware ops controls
- `c95b872` Add hardware service usage and entitlement controls
- `9cfc6ab` Redesign DeviceKit operator dashboard
- `b720523` Polish operator dashboard navigation
- `1df64e8` Fix dashboard sidebar and scroll styling
- `06acb49` Fix provider config loading in dashboard
- `7435eec` Clarify provider form fields
- `3ca1551` Add DeviceKit architecture builder guide
- `75ac942` Refine DeviceKit compatibility wording
- `8fd9aa1` Add Solana DePIN reference templates
- `933a8a1` Complete DeviceKit infra contracts
- `3e74179` Close DeviceKit app user onboarding loop

### 2026-04-29

- `eebaef0` Add DeviceKit onboarding checklist
- `128d85e` Update DeviceKit onboarding docs
- `f1a93ee` Add DeviceKit customer portal
- `4da9cc8` Add wallet-signed customer activation flow
- `4930c27` Simplify customer wallet activation page
- `682a92e` Clarify onboarding entrypoints
- `815706c` Harden device provisioning project selection
- `7f3c21f` Model app-linked hardware operations
- `ca45546` Add customer hardware purchase demo
- `ded4fb4` Move customer checkout before activation panel
- `22319de` Document customer purchase portal layout
- `c787861` Toggle customer wallet actions by connection state
- `d034f2f` Fix customer checkout product presets
- `ccd4563` Delete devices from fleet inventory
- `a09c31e` Add DeviceKit local runtime launcher
- `b41e055` Add app-scoped DeviceKit configuration flow
