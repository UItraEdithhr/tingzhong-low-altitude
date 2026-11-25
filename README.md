# 挺中航空 · 低空综合保障系统

一体化低空保障演示工程，包含设备端、飞控后端、管理平台、通讯态势、地面站、PWA 与原生 Android 飞手端。

当前原生 Android 版本：**v2.15.1（versionCode 35）**。

## 下载完整工程

- 发布页面：[v2.15.1 · 低空综合保障系统完整源码](https://github.com/UItraEdithhr/tingzhong-low-altitude/releases/tag/v2.15.1)
- 完整源码 ZIP：[直接下载](https://github.com/UItraEdithhr/tingzhong-low-altitude/releases/download/v2.15.1/tingzhong-low-altitude-source-v2.15.1.zip)

源码 ZIP 包含完整合并工程、文档、资源、验证脚本与 Android v2.15.1 调试 APK。仓库已公开，查看和下载无需登录；修改仓库需要相应权限。

> 本仓库用于研发、联调与演示，不代表真实飞行认证、生产部署或 ATC 放行能力。

## 工程组成

- `android/`：原生 Kotlin / Jetpack Compose 飞手端。
- `flight/`：FastAPI 飞控、航道规划、Agent 与 MCP。
- `platform/`：一体化管理平台门户。
- `device/`：地面站、机位、传感器与 DSM 资源。
- `comms/`：通讯与态势页面。
- `pilot-app/`：C 端 PWA 与旧版 Android 打包工程。
- `shared/`：跨系统统一接口契约。
- `_remote_demo/`：远程演示、真实 POST 守护与验证脚本（不含运行凭据）。
- `_validation/`：飞行记录、简报与结构化输出验证脚本和结果。
- `docs/merge/`：新旧工程合并清单与决策记录。
- `dist/`：最新 Android 调试安装包。

## 当前功能摘要

- 动态起降程序、候选航道、风场鲁棒分析与规则／大模型候选推荐。
- 多设备态势去重、地面站与门户数据联动。
- 原生 Android 三语界面、Agent 对话、主动提醒、语音输入和悬浮球。
- 飞前检查、飞行准备记录、历史筛选、摘要导出和离线补传。
- 弱网自动重连、五分钟快照过期保护。
- 告警处理备注、二次确认、复核状态与飞行记录处理历史。
- Agent 飞行前简报与记录复盘，结构化输出、长度与语言校验、合法证据路径。
- 公网真实 POST 健康探测、故障分类、最后成功时间与保守隧道恢复。
- 只读 MCP 工具接入。

## 验证状态

- Android：**81 项 JVM 测试通过**。
- 后端：**173 项自动化测试通过**。
- 守护与真实 POST 探测：**7 项测试通过**。
- 飞行记录及处理历史：本机与公网接口验证通过，重复同步保持幂等。
- 结构化简报：本机 Kimi `k3-agent` 实测通过，91 个英文单词、证据字段合法、未触发重试或回退。
- v2.15.1 APK：v2 调试签名验证通过。
- 未进行真机安装与界面验收；真实飞行、生产认证及多人生产权限体系未验证。

## 配置与安全

所有真实密钥只放在本机环境变量或未跟踪的运行配置中，包括 `KIMI_API_KEY`、`DEEPSEEK_API_KEY`、`WEATHER_API_KEY`／`WEATHERAPI_KEY`、`SMTP_*`／`PILOT_SMTP_*` 和 `REMOTE_ACCESS_TOKEN`。

数据库、日志、手机设置、隧道状态、访问令牌、构建缓存和语音缓存均不纳入版本控制。详见 `SECURITY.md`。

## 许可说明

本仓库已公开，未新增统一的开源许可证。公开分发前，请确认各子项目、地图资源、字体、图标和第三方依赖各自的许可要求。
