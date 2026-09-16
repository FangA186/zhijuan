# 知卷 · 产品与开发交接包 v1.2

**小学、初中、高中；第一版不接题库；DeepSeek 官方 API + Hermes 唯一 Agent 框架；不引入 LangChain、LangGraph。**

本包是详细设计、接口契约、Skills 模板、参考规则和验收规程，**不是可运行应用框架**。没有包含或安装 Hermes 官方源码；Adapter 仍为协议声明，没有连接真实 DeepSeek。文档 HTML 是阅读版，不是网页工作台工程。

## v1.2 新增内容

主文档新增第 24—28 章：M0—M3 阶段、最小验收 G-MIN、完整验收 G-FULL、用户可见效果、工程交付清单和证据签收。原有 01—23 章及 DeepSeek + Hermes 技术选型保留。

`acceptance/` 新增 19 类最小用例（12 成功 + 7 失败）、28 类完整用例，均为 **NOT_RUN**；另有三学段 5 题 20 分输入、能力登记、报告和证据模板、交付核对表与演示脚本。用例不是自动化 E2E 实现，也不是验收已通过的记录。

## 建议阅读顺序

先读 `docs/07_MVP阶段_验收链路_交付效果.md` 和 `acceptance/README.md`，明确交付与验收；再按 01 产品、02 架构、03 接口、04 测试运维、06 DeepSeek/Hermes 接入指南组织开发。完整 Word、HTML、Markdown 在 `deliverables/`。

## MVP 交付的判定

| 阶段 | 未来交付要求 | 不能混淆的边界 |
| --- | --- | --- |
| M0 准备 | 首发能力、参数和工程责任批准 | 当前文档齐全不代表所有准备已签署 |
| M1 骨架 | 真前后端、Worker、固定 Hermes、真实调用；三学段各一题 | 只给 Protocol、静态 HTML 或数据库 Compose 不算可运行 |
| M2 最小闭环 | 三学段生成、盲解、基础检查、编辑、保存、草稿 PDF/JSON；G-MIN | 仅限授权验证，不是正式发布资格 |
| M3 完整 MVP | 首发能力、审批发布、DOCX、安全恢复、质量与运维；G-FULL | 不承诺全学科自动证明正确 |

## 包内已有材料

`contracts/`：5 份 JSON Schema + OpenAPI 核心接口约定；`skills/`：5 份待实机验证模板；`database/`：SQL 草案；`configs/`：无密钥配置示例；`examples/`：离线契约数据；`reference_code/`：发布门禁、运行策略与 Adapter 协议；`infra/`：仅本地数据库／消息队列示例；`acceptance/`：本轮新增验收材料；`tests/`：离线参考测试和真实执行日志。

## 运行离线参考测试

建议部署 Python 3.12；本次实际离线运行环境记录在 VALIDATION.md。安装 requirements-test.txt 后，在包根目录运行：

```bash
python -m unittest discover -s tests -v
python verify_bundle.py
python verify_acceptance_assets.py
```

这些命令只检查参考规则、契约与验收材料；不会启动应用、Hermes、DeepSeek、数据库迁移或真实出卷。新用例的 NOT_RUN 不会因离线脚本通过而变成 PASS。

## 当前交付边界

`acceptance/current-delivery-status.json` 明确记录无应用／无 Hermes 源码／无 live 调用。未来工程需提供可复现固定 Hermes 来源与运行实现，并逐阶段留证；本轮不为未执行用例填写成绩、费用或签字。

`VALIDATION.md` 记录本轮实际离线与文档检查范围。`CHANGELOG.md` 保留历史与本轮变更；`MANIFEST.sha256` 用于核对当前包文件。参考代码不替代生产鉴权、事务、隔离和模型质量评估。
# zhijuan
