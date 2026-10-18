<a id="ios-testflight-remote-release"></a>

<div align="center">

# iOS TestFlight · 远程内测发布 Skill

**不在电脑旁时，让 Agent 按项目配置推进内测发布。**

发布准备 · Agent 执行 · 版本检查 · 内测交付

[![中文说明](https://img.shields.io/badge/%E8%AF%B4%E6%98%8E-%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87-059669)](#readme-detail-10)
[![项目类型](https://img.shields.io/badge/%E9%A1%B9%E7%9B%AE-Skill-6366f1)](#readme-detail-10)

[✨ 可以交给 Agent 的任务](#readme-detail-10) · [✅ 适用场景](#readme-detail-audience) · [🧩 模块速查](#readme-detail-18) · [🔄 Agent 的执行流程](#readme-detail-8) · [🤖 给 Agent 的任务示例](#readme-detail-12) · [📌 你需要提前准备](#readme-detail-14)

</div>

---

这个 Skill 用来让 Agent 帮你完成 iOS 的 TestFlight Internal 发布，适合你不在电脑旁、但需要快速推送内测版本的场景。

<a id="readme-section-2"></a>

<a id="你可以直接让-agent-做什么"></a>

<a id="readme-detail-10"></a>

## ✨ 可以交给 Agent 的任务

- 自动检查当前项目是否具备发布条件（Xcode、fastlane、lane、项目元数据）
- 一次性收集发布所需材料（避免反复追问）
- 给出建议版本号并等待你确认
- 自动执行构建、上传、Internal Group 分发
- 发布后校验测试者是否可见最新 build

<a id="readme-detail-audience"></a>

## ✅ 适用场景

适合需要由 Agent 协助 TestFlight 内测发布的维护者。

<a id="readme-section-1"></a>

<a id="agent-的执行流程"></a>

<a id="readme-detail-8"></a>

## 🔄 Agent 的执行流程

1. 先预检项目和环境，确认能发布。
2. 自动扫描并补齐材料，缺什么一次性告诉你。
3. 给出版本建议（patch/minor/major），你确认后才正式发布。
4. 执行构建上传和测试组分发。
5. 返回发布结果，并告诉你首装和后续更新的操作方式。

<a id="readme-section-3"></a>

<a id="你怎么对-agent-下指令"></a>

<a id="readme-detail-12"></a>

## 🤖 给 Agent 的任务示例

你可以直接说：

- `帮我发布到 TestFlight internal`
- `我现在不在电脑旁，帮我走远程内测发布`
- `执行 internal_release，发到 Agent Internal Testing`

<a id="readme-section-4"></a>

<a id="你需要提前准备"></a>

<a id="readme-detail-14"></a>

## 📌 你需要提前准备

- iOS 项目可正常本地构建，并且该项目至少有一次通过数据线连接 iPhone 真机成功安装运行（用于确保签名、设备信任与本地发布链路已验证）
- App Store Connect API 凭证：
  - 登录 [App Store Connect](https://appstoreconnect.apple.com/)
  - 进入 `Users and Access`（用户和访问）
  - 打开 `Integrations` → `App Store Connect API`
  - 在页面中复制 `Issuer ID`
  - 在 `Keys` 中创建 API Key，下载一次性 `.p8` 文件（文件名通常为 `AuthKey_<KEY_ID>.p8`，下载后请妥善保存）
- 目标测试者邮箱（可多个）

首次准备可参考：`references/newbie-guide.md`

<a id="readme-section-5"></a>

<a id="进一步阅读"></a>

<a id="readme-detail-16"></a>

## 📚 进一步阅读

- [Agent 使用说明](SKILL.md)

<a id="readme-section-6"></a>

<a id="仓库导航"></a>

<a id="readme-detail-18"></a>

## 🧩 模块速查

按要处理的工作选择入口，先看模块职责，再进入对应文件或目录。

| 模块入口 | 负责什么 | 什么时候看 |
| --- | --- | --- |
| [`SKILL.md`](SKILL.md) | Agent 使用规则与执行入口 | 让 Agent 读取任务规则、所需材料与交付要求 |
| [`examples/`](examples/) | 可参考的输入与调用示例 | 用现有样例核对输入格式和调用方式 |
| [`references/`](references/) | 技能规则与输入输出合同 | 核对输入约定、操作细节与适用边界 |
| [`scripts/`](scripts/) | 开发与维护脚本 | 查找构建、验证或维护的现有命令 |
