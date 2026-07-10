---
sidebar_position: 1
---
# CoStrict Cloud User Manual

CoStrict Cloud is an AI-powered cloud programming workspace that integrates with the CoStrict CLI (csc) command-line tool. It supports remote connection to local/private server devices via browser, with built-in conversational AI programming, file management, multi-session persistence, and remote terminal collaboration — enabling seamless remote development, real-time AI coding and debugging, and cross-device project continuity.

This section covers csc command-line cloud operations and the corresponding web-based workflows. If you haven't installed csc yet, please refer to the [CSC Installation Guide](/cloud/csc-installation).

## 1. Sign In

**Sign-in URL: [https://zgsm.sangfor.com/cloud](https://zgsm.sangfor.com/cloud)**

Open the cloud URL above and sign in to your personal account via the top-right corner.

![Sign-in page](./img/image1.webp)

> **Important:** The csc CLI and CoStrict Cloud web portal must be signed in with the same account. Mismatched accounts will prevent devices from appearing in the web portal's device list.

After signing in, you'll notice there are no devices yet, so proceed to register and start the service.

![Device list](./img/image2.webp)

## 2. Device Registration (CLI)

On the computer/server you want to connect to remotely, make sure the csc tool is installed. If not, refer to the beginning of this guide.

Open a terminal and run the csc login command:

![Login command](./img/image3.webp) ![Login interface](./img/image4.webp)

A login window will pop up — make sure to use the same account as in Step 1.

If the device fails to connect or goes offline, use `csc cloud doctor` for self-diagnostics, and `csc cloud restart` to attempt a service restart.

## 3. Create a Workspace (Web)

After registering the device, return to Cloud. Both options 1 and 2 in the image below allow you to create a workspace on the current device.

To register additional devices, select option 3 to return to the device registration guide and repeat the same commands on the new device.

![Create workspace](./img/image5.webp)

Select option 1 or 2 to open the creation dialog, then choose a local project directory on the device to complete workspace creation.

![Select project directory](./img/image6.webp)

Each workspace is uniquely bound to an independent project directory, supporting isolated workspaces for multiple projects.

## 4. Connect to a Workspace

When the workspace status is **Idle**, click the connect icon on the right side of the card to establish a remote connection. Once connected, you can use the following core capabilities:

- **Remote Conversational Programming** — Real-time AI interaction for code generation, bug debugging, and logic refactoring
- **Multi-Session Management** — Create, switch, and revisit sessions with full conversation history preserved
- **Remote Project Collaboration** — Browse, edit, and run code on remote devices directly from the browser
- **Built-in API Documentation** — Local API docs included, supporting online API debugging

## 5. Cloud Skill Favorites & Distribution

**Favoriting skills via the web portal:**

1. Visit the Skill Store: [https://zgsm.sangfor.com/cloud/store](https://zgsm.sangfor.com/cloud/store)
2. Browse and filter desired skills, sub-agents, and custom commands
3. Click the favorite button on a skill card to save it to your cloud collection

![Skill store](./img/image7.webp)

For more tutorials, refer to: [Knowledge Hub Subscription Guide: From Web Subscription to csc Auto-Sync](/cloud/hub-subscription)

---

## Cloud FAQ

### Q1: CLI is running, but the registered device doesn't appear in the web portal?

- Always use the official cloud URL: [CoStrict Cloud](https://zgsm.sangfor.com/cloud)
- Verify that the `csc auth login` account matches the web portal account exactly
- Run `csc cloud restart` to restart the service and re-sync the device list
- Check local network connectivity and confirm the firewall isn't blocking service ports
- Run `csc cloud doctor` for diagnostics

### Q2: First-time `csc cloud start` hangs or downloads slowly?

- The first launch needs to pull cloud plugins and dependencies — this is normal initialization
- Check device network status; if the network is unstable, try switching networks and retrying
- Do not interrupt the process manually — wait for automatic deployment to complete

### Q3: Workspace connection fails or drops frequently?

- Run `csc cloud restart` to restart the local daemon process
- Run `csc cloud doctor` for diagnostics
- Check local firewall and security group settings, and allow service ports

### Q4: How to troubleshoot cloud functionality errors?

All cloud exceptions should first be diagnosed via logs. The unified log path is `~/.costrict/cs-cloud/app.log`, which records process start/stop, device authentication, network connections, and plugin loading logs.

### Q5: How to view the local cloud service address and API documentation?

After `csc cloud start` succeeds, the terminal automatically outputs the local service URL and API documentation address — copy and paste them into a browser for access and debugging.

---

## Technical Support

Scan the QR code to add the CoStrict operations assistant for assistance.

![Operations assistant](./img/image8.webp)
