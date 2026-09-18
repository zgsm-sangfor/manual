---
title: CoStrict API 接入使用说明
sidebar_label: API 接入
---

# CoStrict API 接入使用说明

本文介绍如何在 CoStrict 插件和 CoStrict CLI（以下简称 CSC）中配置自己的模型 API，完成首次调用，并管理 API Key。

## 1. 名词释义

**服务商**是向你提供 API 服务、签发 API Key 的平台。

**模型**是实际回答问题和执行任务的模型；

**接口协议**则决定 CoStrict 以什么方式向平台发送请求。常见的接口协议类型有OpenAI 兼容接口、Anthropic兼容接口、Google Gemini API等。

配置时，请使用同一服务对应的协议、Base URL、API Key 和模型 ID。一个服务商可能提供多种协议，每种协议对应的地址可能不同。

### 常见提供商

CoStrict 支持主流模型提供商的API接口，你可以接入智谱、Kimi、DeepSeek等官方API，也可以通过大模型服务平台（阿里百炼、硅基流动、方舟 Agent Plan等）由公司管理员统一配置后，使用各类大模型。

## 2. 开始前需要准备什么

1. 已安装 CoStrict VS Code 插件或 CSC。尚未安装，可查看 [CoStrict 下载页](https://costrict.ai/download) 或 [CSC 快速开始](https://docs.costrict.ai/csc/quickstart)。
2. 注册模型 API 服务商的账号，以及有效的 **API Key。**
3. 获取服务商提供的接口协议、Base URL 和模型 ID。
4. 可用的 API 额度或有效订阅，以及目标模型的访问权限。是否需要实名认证、充值或开通权限，以服务商要求为准。
5. 能访问该 API 地址的网络环境。

如果 API 来自公司统一网关，请向管理员获取完整配置，不要用模型原厂的地址替换公司网关地址。

可以先整理下面四项，再打开 CoStrict：

| 配置项 | 应填写什么 |
| --- | --- |
| 接口协议 | 服务商文档明确注明的 OpenAI 兼容、Anthropic 兼容或 Gemini API |
| Base URL | 对应协议的 API 基础地址，不是服务商首页或控制台网址 |
| API Key | 同一平台签发、对该接口有效的密钥 |
| 模型 ID | 服务商允许当前账号调用的准确模型标识 |

不确定协议时，可直接向服务商询问：“我要接入 CoStrict，请提供接口协议、Base URL、模型 ID，并确认这枚 API Key 或套餐是否允许用于该工具。”不要在公开咨询中附上真实 Key。

## 3. 如何获取 API Key

以下仅列举部分常见提供商及模型的API Key方式。

| 提供商 | 常见模型 | 兼容接口类型 | API Key 获取方式 |
| --- | --- | --- | --- |
| 智谱 | GLM-5.3、GLM-5.3-Flash | OpenAI 兼容、Anthropic 兼容 | GLM Coding Plan [https://docs.bigmodel.cn/cn/coding-plan/quick-start](https://docs.bigmodel.cn/cn/coding-plan/quick-start) |
| DeepSeek | DeepSeek-V4.1-Flash、DeepSeek V4 Pro | OpenAI 兼容、Anthropic 兼容 | [API 接入说明](https://api-docs.deepseek.com/zh-cn/) |
| Kimi（月之暗面） | Kimi K3、Kimi K2.7 Code | OpenAI 兼容、Anthropic 兼容 | [API 快速开始](https://platform.kimi.com/docs/guide/start-using-kimi-api) |

### 通用流程

1. 进入服务商官方开放平台，注册并登录账号。
2. 根据平台要求完成账号验证、项目创建或服务开通。
3. 打开 API Key 或密钥管理页面，创建用于 CoStrict 的密钥。
4. 复制 Key，保存在可信的密码管理器中；配置 CoStrict 时再粘贴到 API Key 输入框。
5. 在该服务的接入文档中确认协议、Base URL 和模型 ID。

部分平台只在创建时展示完整 Key。若之后无法查看，请按平台规则创建新 Key，不要把聊天账号密码当作 API Key。

<video src="/videos/api-vscode-zh.mp4" width="100%" controls preload="metadata" playsInline></video>

<video src="/videos/api-csc-zh.mp4" width="100%" controls preload="metadata" playsInline></video>

## 4. 在 CoStrict VS Code 插件中配置

这里配置分两种情况：首次注册和非首次登陆。他们的配置入口不一样。

#### 首次注册

1. 首次注册的用户安装好插件后，先点击左侧工具栏的CoStrict图标。
2. 然后登陆面板选择使用其他提供商
3. 接着在供应商列表里找到要接入的提供商，并完善配置信息
4. 填好后，点击登陆即可开始体验CoStrict。

![](/img/api-integration/zh/plugin-first-use.webp)

#### 非首次登陆

下面以 OpenAI 兼容接口为例。

1. 打开 VS Code，进入 CoStrict 面板。
2. 打开 CoStrict 的“设置”，进入“提供商”。
3. 在“配置文件”区域新建一组配置，例如“个人 API”。已有配置需要修改时，也可选择对应配置。
4. 将“API 提供商”设为 `OpenAI Compatible`。如果出现切换服务商的提示，阅读后确认。
   ![](/img/api-integration/zh/plugin-create-profile.webp)
5. 填写“OpenAI 基础 URL”和“API 密钥”。这里的字段名表示兼容接口，Key 应填写实际服务商签发的 Key。
6. 在“模型”中选择目标模型；若列表没有目标模型，在模型选择器中输入准确模型 ID，并选择使用该自定义模型的选项。
7. 如需设置上下文窗口、最大输出 Token 数、图像支持等参数，按模型官方规格填写。
8. 点击“保存”。返回对话面板，确认使用刚才的配置和目标模型，再新建任务验证。
   ![](/img/api-integration/zh/plugin-provider-settings.webp)

模型列表能够加载，或者“保存”没有报错，只说明完成了部分配置检查，还需要实际发起一次对话。

如果使用 Anthropic 或 Google Gemini，选择对应提供商，并按其官方文档填写 Key、模型和必要的自定义地址。不要把 OpenAI 兼容地址填写到另一种协议的配置中。

## 5. 在 CSC 中配置

以下命令在终端中使用。

1. 进入准备使用的项目目录，启动 CSC：

   ```
   csc
   ```

2. 在 CSC 的输入框中输入：

   ```
   /login
   ```
   ![](/img/api-integration/zh/csc-select-protocol.webp)
3. 选择与服务商文档一致的协议：`OpenAI 兼容`、`Anthropic 兼容` 或 `Gemini API`。
   ![](/img/api-integration/zh/csc-provider-settings.webp)
4. 按顺序填写 Base URL、API Key，以及 Haiku、Sonnet、Opus 三个模型配置项。
5. 每填完一项按 Enter 进入下一项；在最后一项按 Enter 保存。

6. 输入 `/model`，确认当前使用的目标模型，再发送测试消息。
   ![](/img/api-integration/zh/csc-select-model.webp)

### 模型映射怎么填

这里的三个名称是 CSC 中的模型映射位置。接入第三方服务时，应填写该服务商提供的实际模型 ID，不需要购买三个不同厂商的模型。

如果目前只使用一个模型，可以在三个位置填写同一个有效模型 ID。以后需要分配不同模型时，再分别修改。例如准备使用的模型 ID 为 `YOUR_MODEL_ID`，三个位置都填写该 ID；不要原样填写这个占位词。

模型 ID、额度和能力以服务商为准。Gemini 配置要求三个模型位置都填写。

出现配置保存成功提示后，仍需完成下一节的实际调用验证。

## 6. 如何验证接入成功

### 第一步：验证基本对话

确认当前配置和模型后，新建对话，发送：

```
请只回复“连接成功”，不要读取文件或执行命令。
```

能够正常收到回复，且没有鉴权、权限或额度错误，说明本次基本模型调用成功。

### 第二步：验证项目读取

在不包含敏感信息的演示项目中放入一份简单的 `README.md`，再发送：

```
请读取当前项目的 README.md，用两句话概括内容，不要修改文件或执行命令。
```

如出现读取授权提示，确认目标文件后允许读取。检查是否实际完成文件读取、回答是否与文件内容一致，以及有无工具调用报错。

基本对话成功但文件读取失败，需要继续检查模型工具调用兼容性或本地权限；这时还不能判断 Agent 使用已配置完成。

如果服务商提供调用记录，可结合请求时间和模型信息核对本次调用。记录可能延迟显示；不要依靠模型回答“我是什么模型”来判断实际调用来源。

## 7. API Key 的保存与安全

### VS Code 插件

插件的 API 配置通过 VS Code 的 SecretStorage（密钥存储）保存。请在插件配置界面管理 Key，不要将真实 Key 写进项目代码或提交到 Git 仓库。

### CoStrict CLI

在 CSC 4.2.38 中，通过上述 `/login` 表单填写的第三方 Key，会写入用户级 `settings.json` 的 `env` 配置中，以可读文本保存。这与 CoStrict 账号登录凭据的存储不是同一条路径。

默认位置为：

| 系统 | 用户配置文件 |
| --- | --- |
| macOS | `~/.costrict/settings.json` |
| Windows | `%USERPROFILE%\.costrict\settings.json` |

如果设置了自定义配置目录，实际位置会变化。不要公开上传该文件或将其作为普通项目文件分享。

### 安全注意事项

- Key 仅粘贴到对应配置输入框，不发送到聊天消息、群聊、Issue 或公开文档。
- 录屏、截图和提交日志前，遮挡整枚 Key，包括可能显示的前缀。检查配置导出文件，不能假定导出会自动移除密钥。
- 将 Key 交给谁，就可能允许谁使用对应账号的 API 额度。服务商支持时，为不同用途创建独立 Key，并设置必要的权限和额度限制。
- Base URL 应来自可信服务商或公司管理员。把 Key 配到不可信地址，可能导致密钥泄露。
- 使用第三方模型处理代码或文档前，确认这些内容允许发送给对应服务商。
- 怀疑 Key 泄露时，立即到签发平台撤销旧 Key，再创建新 Key。仅在 CoStrict 中删除配置不能使泄露的 Key 失效。

## 8. 修改、更换与停用 API Key

### 修改配置或更换 Key

VS Code 插件：进入“设置 → 提供商”，选中对应配置，替换 API Key，点击“保存”；返回对话面板，确认使用该配置并新建任务验证。

CSC：重新输入 `/login`，选择相应协议，填写新的 Key；如更换服务商，同时更新 Base URL 和全部模型映射。保存后使用 `/model` 确认模型，再新建对话验证。

正常轮换 Key 时，先创建并验证新 Key，再到服务商后台撤销旧 Key。若旧 Key 已泄露，应优先撤销旧 Key。

### 暂时不使用这组配置

结束正在执行的任务，再切换到另一组有效配置，或关闭当前工具。这样不会撤销服务商端的 Key，也不代表本地旧 Key 已被清除。

### 让旧 Key 彻底失效

1. 登录签发该 Key 的服务商平台。
2. 在密钥管理页面找到对应 Key，按平台提供的撤销、禁用或删除操作使其失效。
3. 清理 CoStrict 中不再使用的旧配置；如果其他工具也使用这枚 Key，需要同步更新。

VS Code 插件可在“设置 → 提供商”选中不再使用的配置，再使用“删除配置文件”。插件不允许删除唯一剩余的配置；可先配置有效的替代项，再删除旧配置。

CSC 4.2.38 不应通过“清空 Key 输入框后保存”来删除旧 Key，也不能把 `/logout` 视作清除所有第三方 Key。需要清理本地保存值时，退出 CSC，在用户级 `settings.json` 的 `env` 对象中只移除对应的旧 Key 项，保留其他配置和正确的 JSON 格式：

| 本文配置方式 | 对应 Key 项 |
| --- | --- |
| OpenAI 兼容 | `OPENAI_API_KEY` |
| Anthropic 兼容 | `ANTHROPIC_AUTH_TOKEN` |
| Gemini API | `GEMINI_API_KEY` |

若此前还在系统环境变量、终端启动配置或其他配置来源中手动设置过同一枚 Key，也需要清理对应值，再重新打开终端。不要删除整个配置目录。不熟悉 JSON 编辑时，请先在服务商后台撤销 Key，再联系管理员协助清理本地值。

## 9. 常见问题与报错

不同服务商对错误码的定义可能不同。以下用于初步排查，请同时阅读报错正文和该服务商的错误说明。

| 现象或报错 | 常见原因 | 建议处理 |
| --- | --- | --- |
| `401`、Authentication failed、Invalid API Key | Key 错误、已失效，或 Key 与接口不匹配 | 重新复制有效 Key，检查首尾空格及签发平台；确认协议和地址；保存后新建对话重试 |
| `403`、Permission denied | 无模型或项目权限，账号或网络访问策略受限 | 核对模型权限、项目权限及访问限制；由服务商或公司管理员确认 |
| `402`、Insufficient balance、额度不足 | 余额不足或相应服务额度不可用 | 查看当前 Key 所属账号和服务的余额、额度或订阅状态；不要仅凭错误码判断应购买哪个套餐 |
| `404`、Model not found | 地址路径或模型 ID 错误，也可能无该模型权限 | 核对基础地址和准确模型 ID；不要将控制台网址或完整 `/chat/completions` 请求地址直接当作本文的 Base URL |
| `400`、`422`、Invalid parameters | 协议不匹配、参数不受支持、模型能力配置不符 | 按报错字段检查；核对最大输出、图像、推理等配置与模型规格；仍失败时提交脱敏报错 |
| `429`、Rate limit | 请求过快、并发过高；部分平台也用该码表示额度限制 | 阅读错误正文；限流时降低频率、结束重复任务并稍后重试；额度问题到服务商后台核对 |
| `500`、`502`、`503`、服务繁忙 | 服务商或中间网关暂时异常 | 稍后重试，查看服务商状态；持续出现时向服务商提供请求 ID 和时间 |
| Timeout、Connection error、DNS 或证书错误 | 网络、代理、地址解析或证书配置问题 | 确认 API 地址和本机网络；公司网络请联系管理员，不要通过关闭证书校验解决 |
| Context length exceeded、输入过长 | 当前对话超出模型上下文限制 | 新建对话，减少附带文件和输入内容，并核对模型上下文配置 |
| 模型列表为空，但 Key 看起来正确 | 服务未开放模型列表接口、权限不足或地址错误 | 核对官方模型 ID；插件可尝试填写自定义模型；仍需实际发消息验证 |
| 能聊天，但读取文件或其他工具操作失败 | 模型工具调用不兼容，或本地权限未允许 | 查看具体失败步骤；确认文件读取授权；用简单演示项目复测并提交脱敏错误 |
| 更换 Key 后仍使用旧配置 | 修改未保存、当前使用了另一组配置、已有进程或其他配置来源仍保留旧值 | 确认已保存和当前配置；新建对话；CSC 退出后重新启动，检查此前手动设置的配置来源 |
| 配置保存失败 | 配置文件格式、文件权限或 VS Code 密钥存储异常 | 保留错误信息；CSC 检查用户配置 JSON 格式和写入权限；不要通过删除整个配置目录处理 |

## 10. 联系方式

CoStrict 插件配置或使用问题，可通过以下已有官方入口反馈：

- 插件“设置 → 关于 CoStrict”中的问题反馈及联系入口。
- 添加小助手。

  ![CoStrict 小助手二维码](/img/api-integration/support-wechat.webp)

Key 开通、套餐、扣费、模型权限或服务商故障，请联系签发 Key 的平台；公司内部网关问题联系管理员。

反馈时提供：操作系统、VS Code 和插件版本或 CSC 版本、服务商名称、服务类型（普通 API 或订阅）、协议、模型 ID、出错时间、操作步骤、脱敏报错，以及服务商返回的请求 ID（如有）。公开反馈时也应遮挡公司内部域名、账号信息和项目内容，不要发送 API Key。
