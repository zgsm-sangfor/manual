---
sidebar_position: 6
---
# CoStrict Cloud

**Official Cloud URL: [https://zgsm.sangfor.com/cloud](https://zgsm.sangfor.com/cloud)**

[CoStrict Cloud](https://zgsm.sangfor.com/cloud/workspace) is an **AI-powered cloud programming workspace** that lets you remotely connect to your personal devices (local or private servers) from any browser. It features conversational AI programming, project file management, multi-session persistence, and remote terminal collaboration — enabling **seamless browser-based remote development, real-time AI coding and debugging, and cross-device project continuity**.

## Quick Start

### 1. Sign In

**Official Cloud Entry: [https://zgsm.sangfor.com/cloud](https://zgsm.sangfor.com/cloud)**

Open the official cloud URL above to enter the web portal, then sign in to your personal account. If you are not signed in, click the **Sign In** button at the bottom of the left sidebar.

> **Important:**
> The CoStrict CLI command-line tool and the CoStrict Cloud web portal **must be signed in with the same account**. If the accounts do not match, the device will not appear in the web portal's device list.

### 2. Register a Device

On the personal computer or server you want to connect to remotely, first install the [CoStrict CLI tool](https://docs.costrict.ai/cli/guide/installation).

Sign in via CLI:

```bash
cs auth login
```

After signing in, run the device registration and startup command:

```bash
cs cloud start
```

> The first time you run `cs cloud start`, it will automatically pull dependency plugins and runtime components from the cloud. Please be patient while the automatic download and installation completes — no manual intervention is required.

Once registered, the device will automatically sync and appear in the **device list** in the left sidebar of the web portal.

### 3. Create a Workspace

1. Visit the default cloud URL: [https://zgsm.sangfor.com/cloud](https://zgsm.sangfor.com/cloud) and open the device list.
2. Find the registered online device and click the **"+" button** on the right side of the device card.
3. Select the target project directory on the device to create the workspace.
4. Each workspace **uniquely maps to an independent project directory** on the device. Multiple projects can be managed via separate, isolated workspaces.

### 4. Connect to a Workspace

When a workspace is in the **idle** state, click the **connect icon** on the right side of the workspace card to establish a remote connection.

Once connected, you can use the following core capabilities:

- **Remote Conversational Programming** — Interact with the AI assistant in real time for requirements, code generation, bug debugging, and logic refactoring.
- **Multi-Session Management** — Freely create, switch between, and revisit sessions with full conversation history preserved.
- **Remote Project Collaboration** — Browse, edit, and run code files on the remote device directly from the browser.
- **Built-in API Documentation** — The service comes with API documentation that can be accessed directly for debugging.

---

## Common Operations

### Start the Cloud Service

After first-time registration or if the service has stopped, run the start command:

```bash
cs cloud start
```

### Restart the Cloud Service

If the device goes offline, connection becomes abnormal, or the service hangs, run the restart command:

```bash
cs cloud restart
```

### Normal Startup Log Example

```
➜  share cs cloud start
  ✓ Device registered
  device_id: 21484ad96b82e1468cba65be0e55a666df1aba78834ffdeee19404a5e72b0ce9
  ✓ Device token validated
  → Starting daemon...
  ✓ cs-cloud started
  pid: 16571
  mode: cloud
  url: http://127.0.0.1:56973
  docs: http://127.0.0.1:56973/api/v1/docs
  logs: /User/user/.costrict/cs-cloud/app.log
```

Key information explained:

- `device_id`: Unique device identifier.
- `pid`: Background daemon process ID.
- `url`: Local service access address.
- `docs`: API documentation address.
- `logs`: Log file path, the key reference for troubleshooting.

---

## FAQ

### Q1: The CLI is running, but the device is not visible on the web portal?

**A1:**

1. Make sure you are accessing the default cloud URL: [https://zgsm.sangfor.com/cloud](https://zgsm.sangfor.com/cloud).
2. Verify that the account used for `cs auth login` is **exactly the same** as the web portal account.
3. Run `cs cloud restart` to restart the service and re-sync the device list.
4. Check whether the local network can access the cloud platform normally and that the firewall is not blocking the port.

### Q2: The first `cs cloud start` hangs or downloads slowly?

**A2:**

1. The first startup will automatically pull cloud plugins and dependencies. This is normal behavior.
2. Check the device's network connectivity and try switching networks if needed.
3. Do not manually interrupt the process; wait for the automatic initialization to complete.

### Q3: Workspace connection fails or drops frequently?

**A3:**

1. First, run `cs cloud restart` to restart the local daemon.
2. Check the log file at `~/.costrict/cs-cloud/app.log` for error messages.
3. Confirm that the local firewall or security group is not blocking the service port.

### Q4: How to troubleshoot errors, exceptions, or unavailable features?

**A4:**

For all exceptions, prioritize locating the cause via the **log file**. The log path is:

```
~/.costrict/cs-cloud/app.log
```

You can view full logs covering process start/stop, device authentication, network connections, and plugin loading to quickly identify the root cause.

### Q5: How do I view the local service address and API documentation?

**A5:**

After running `cs cloud start` successfully, the terminal will automatically output:

- Local service access address `url`
- API documentation address `docs`

Copy these directly into your browser to access them.

---

## Learn More

- Official Cloud Entry: [https://zgsm.sangfor.com/cloud](https://zgsm.sangfor.com/cloud)
- Try the Workspace Now: [CoStrict Cloud Workspace](https://zgsm.sangfor.com/cloud/workspace)
- Capability Extensions: [App Store — Skills / Sub-agents / MCP Servers](https://zgsm.sangfor.com/cloud/store)
- Official Docs & Updates: [costrict.ai](https://costrict.ai)
