---
sidebar_position: 1
---
import image1 from './img/image1.webp';
import image2 from './img/image2.webp';
import image3 from './img/image3.webp';
import image4 from './img/image4.webp';
import image5 from './img/image5.webp';
import image6 from './img/image6.webp';
import image7 from './img/image7.webp';
import image8 from './img/image8.webp';

# CoStrict Cloud 使用手册

CoStrict Cloud 是 AI 驱动的云端编程工作空间，适配 CoStrict CLI（csc）命令行工具，支持通过浏览器远程连接本地/私有服务器设备，内置对话式AI编程、文件管理、多会话留存、远程终端协作能力，实现无感远程开发、AI实时编码调试、跨设备项目无缝流转。

本节介绍 csc 命令行云端专属操作及网页端配套使用流程。如未安装 csc 请参考 [CSC安装手册](/cloud/csc-installation)。

## 1. 登录账号

**登录入口：[https://zgsm.sangfor.com/cloud](https://zgsm.sangfor.com/cloud)**

打开云端地址进入首页，右上角完成个人账号登录。

<img src={image1} alt="登录页面" width="750" />

> **重要注意**：csc 命令行端与 CoStrict Cloud 网页端必须登录同一个账号，账号不一致会导致设备无法在网页端设备列表正常展示。

登录好后会发现我们没有设备，所以需要执行注册，启动服务。

<img src={image2} alt="设备列表" width="750" />

## 2. 设备注册（命令行操作）

在需要被远程连接的电脑/服务器上，确保已安装 csc 工具，未安装请参考本手册开头。

然后打开终端执行 csc 登录命令：

<img src={image3} alt="登录命令" width="500" /> <img src={image4} alt="登录界面" width="600" />

执行后会弹出登录界面，注意和第一步登录云端账号需一致。

设备连接失败、离线等，可优先使用 `csc cloud doctor` 命令进行自检，并使用 `csc cloud restart` 命令尝试重启服务。

## 3. 创建工作空间（网页端操作）

设备注册好后回到 Cloud，如图 1、2 都可以在当前设备上创建工作空间。

如果想多设备注册，可选择 3，返回刚才注册设备指引页，重复在新设备上操作相同命令即可。

<img src={image5} alt="创建工作空间" width="750" />

选择 1、2，会打开创建弹窗，选中设备内本地项目目录，完成工作空间创建。

<img src={image6} alt="选择项目目录" width="500" />

每个工作空间唯一绑定一个独立项目目录，支持多项目创建隔离工作空间。

## 4. 连接工作空间

工作空间状态为空闲时，点击卡片右侧连接图标即可一键远程连接，连接成功后可使用核心能力：

- **远程对话编程**：AI实时交互，实现代码生成、Bug调试、逻辑重构
- **多会话管理**：新建、切换、回溯会话，永久保留对话上下文
- **远程项目协作**：浏览器端直接浏览、编辑、运行远程设备代码
- **内置接口文档**：自带本地API文档地址，支持接口在线调试

## 5. 云端技能收藏下发

**网页端收藏技能：**

1. 访问技能商店地址：[https://zgsm.sangfor.com/cloud/store](https://zgsm.sangfor.com/cloud/store)
2. 浏览筛选所需技能、子智能体、自定义命令
3. 点击技能卡片收藏按钮，完成云端收藏

<img src={image7} alt="技能商店" width="750" />

更多操作教程参考下方文档：[知识中心订阅教程：从网页订阅到 csc 自动同步](/cloud/hub-subscription)

---

## Cloud 云端功能 FAQ

### Q1：CLI 已启动，但网页端看不到已注册设备？

- 务必使用官方云端地址访问：[CoStrict Cloud](https://zgsm.sangfor.com/cloud)
- 核对 `csc auth login` 登录账号与网页端账号完全一致
- 执行 `csc cloud restart` 重启服务，重新同步设备列表
- 检查本地网络连通性，确认防火墙未拦截服务端口
- 运行 `csc cloud doctor` 进行检测

### Q2：首次执行 csc cloud start 卡住、下载缓慢？

- 首次启动需拉取云端插件和依赖，属于正常初始化流程
- 检测设备网络状态，网络波动可切换网络重试
- 禁止手动中断进程，等待自动完成初始化部署

### Q3：工作空间连接失败、频繁掉线？

- 执行 `csc cloud restart` 重启本地守护进程
- 运行 `csc cloud doctor` 进行检测
- 检查本地防火墙、安全组，放行服务占用端口

### Q4：云端功能使用异常、报错如何排查？

所有云端异常优先通过日志定位问题，统一日志路径：`~/.costrict/cs-cloud/app.log`，可查看进程启停、设备认证、网络连接、插件加载全量运行日志。

### Q5：如何查看本地云端服务地址和接口文档？

执行 `csc cloud start` 启动成功后，终端自动输出本地服务访问地址（url）、接口文档地址（docs），直接复制至浏览器即可访问调试。

---

## 技术支持

扫码添加 CoStrict 运营小助手-蔻蔻，统一解答。

<img src={image8} alt="运营小助手" width="200" />
