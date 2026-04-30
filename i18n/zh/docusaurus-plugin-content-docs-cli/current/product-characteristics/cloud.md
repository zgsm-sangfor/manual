---
sidebar_position: 6
---
# CoStrict Cloud

**官方云端默认地址：[https://zgsm.sangfor.com/cloud](https://zgsm.sangfor.com/cloud)**

[CoStrict Cloud](https://zgsm.sangfor.com/cloud/workspace) 是一款**AI 驱动的云端编程工作空间**，支持随时随地通过浏览器远程连接本地/私有服务器个人设备，内置对话式 AI 编程、项目文件管理、多会话留存、远程终端协作能力，实现**浏览器无感远程开发、AI 实时编码调试、跨设备项目无缝流转**。

![CoStrict Cloud 演示](../guide/img/quick_start/cs-cloud.gif)

## 快速开始

### 1. 登录账号

**官方云端入口：[https://zgsm.sangfor.com/cloud](https://zgsm.sangfor.com/cloud)**

打开上面默认云端地址进入网页端，先登录平台个人账号；未登录用户点击左侧边栏底部**登录按钮**完成账号登录。

> 重要注意：
> CoStrict CLI 命令行端 与 CoStrict Cloud 网页端**必须登录同一个账号**，账号不一致会导致设备无法在网页端设备列表中正常显示。

### 2. 注册设备

在需要被远程连接的个人电脑/服务器上，先安装 [CoStrict CLI 工具](https://docs.costrict.ai/cli/guide/installation)。

CLI 执行账号登录：

```bash
cs auth login
```

登录完成后，执行设备注册启动命令：

```bash
cs cloud start
```

> 首次执行 `cs cloud start` 会自动从云端拉取依赖插件、运行时组件，耐心等待自动下载安装即可，无需手动干预。

注册成功后，当前设备会自动同步展示在网页端左侧**设备列表**中。

### 3. 创建工作空间

1. 访问默认云端地址：[https://zgsm.sangfor.com/cloud](https://zgsm.sangfor.com/cloud)，进入设备列表；
2. 找到已注册在线设备，点击设备卡片右侧 **「+」按钮**；
3. 选择设备上本地项目目标工作目录，即可完成工作空间创建；
4. 每个工作空间**唯一对应设备上一个独立项目目录**，支持多项目分别创建隔离工作空间。

### 4. 连接工作空间

工作空间状态为**空闲**时，点击工作空间卡片右侧**连接图标**即可一键建立远程连接。

连接成功后可使用核心能力：

- **远程对话编程**：与 AI 助手实时交互，需求提问、代码生成、Bug 调试、逻辑重构；
- **多会话管理**：自由新建、切换、回溯会话，完整保留历史对话上下文；
- **远程项目协作**：浏览器端直接浏览、编辑、运行远程设备代码文件；
- **内置接口文档**：自带 API 接口文档地址，可直接调试服务接口。

---

## 常用运维命令

### 启动云端服务

首次注册/服务停止后，执行启动命令：

```bash
cs cloud start
```

### 重启云端服务

当设备掉线、连接异常、服务卡死时，可执行重启命令：

```bash
cs cloud restart
```

### 正常启动日志示例

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

关键信息说明：

- `device_id`：设备唯一标识；
- `pid`：后台守护进程号；
- `url`：本地服务访问地址；
- `docs`：接口文档地址；
- `logs`：日志文件路径，排查问题核心依据。

---

## 常见问题 FAQ

### Q1：CLI 已启动，但网页端看不到已注册设备？

**A1：**

1. 务必使用默认云端地址访问：[https://zgsm.sangfor.com/cloud](https://zgsm.sangfor.com/cloud)；
2. 检查 `cs auth login` 登录账号 与 网页端登录账号**完全一致**；
3. 执行 `cs cloud restart` 重启服务，重新同步设备列表；
4. 检查本地网络是否能正常访问云端平台，防火墙未拦截端口。

### Q2：首次执行 `cs cloud start` 卡住、下载缓慢？

**A2：**

1. 首次启动会自动拉取云端插件和依赖，属于正常流程；
2. 检查设备网络连通性，可切换网络重试；
3. 不要手动中断进程，等待自动完成初始化。

### Q3：工作空间连接失败、频繁掉线？

**A3：**

1. 先执行 `cs cloud restart` 重启本地守护进程；
2. 查看日志文件：`~/.costrict/cs-cloud/app.log` 排查报错；
3. 确认设备本地防火墙、安全组未拦截服务端口。

### Q4：使用异常、报错、功能不可用怎么排查？

**A4：**

所有异常问题优先通过**日志文件**定位原因，日志路径：

```
~/.costrict/cs-cloud/app.log
```

可查看进程启停、设备认证、网络连接、插件加载等全量日志，快速定位故障点。

### Q5：如何查看本地运行的服务地址和接口文档？

**A5：**

执行 `cs cloud start` 启动成功后，终端会自动输出：

- 本地服务访问地址 `url`
- 接口文档地址 `docs`

直接复制到浏览器即可访问。

---

## 了解更多

- 官方云端默认入口：[https://zgsm.sangfor.com/cloud](https://zgsm.sangfor.com/cloud)
- 立即体验工作空间：[CoStrict Cloud 云端工作空间](https://zgsm.sangfor.com/cloud/workspace)
- 能力扩展：[应用商店 - 技能/子代理/MCP 服务器](https://zgsm.sangfor.com/cloud/store)
- 官方文档&动态：[costrict.ai](https://costrict.ai)
