# v1.2 交付验证记录

日期：2026-09-15。验证对象是产品文档、接口契约、参考代码与验收材料，不是已经完成的出卷应用。

## 实际执行结果

| 检查 | 本轮结果 | 范围与限制 |
|---|---|---|
| 本地单元测试 | 53 项通过 | 原有 41 项 + 新增 12 项验收材料检查；无真实模型调用 |
| 契约一致性 | 5 份 JSON Schema、内部引用、20 个核心操作及 YAML 解析通过 | 未运行完整 OpenAPI 规范认证或真实 API 服务 |
| 验收材料 | 19 类最小 + 28 类完整用例、3 个学段输入配置校验通过 | 用例规程，不是已实现或已执行的端到端自动化 |
| 内容同步 | Word、HTML、Markdown 中均包含新增五章和 47 个用例编号 | 单独交付 DOCX/HTML 与 ZIP 内副本一致 |
| Word 排版 | 42 页渲染并逐页目视检查；文本越出页面边界 0 处 | 使用容器内 LibreOffice；不代表真实试卷渲染管线 |
| Word 内部导航 | 88 个内部链接目标存在 | 文档目录导航检查 |
| HTML | 1440×1000、390×844 视口；87 个锚点目标存在；5 个快速入口可点击；无页面 JS 错误或整体横向溢出 | 在 Chromium 的 about:blank 上加载文件内容；运行环境阻止 file:// 导航，未把本地双击打开当成本次测试结论 |

运行环境：Python 3.13.5。产品建议部署使用 Python 3.12；本次离线附件测试环境不是该生产兼容性验收。第三方资料沿用原稿引用，本轮没有重新开展外部研究。

## 可复现的离线命令

```bash
python -m pip install -r requirements-test.txt
python -m unittest discover -s tests -v
python verify_bundle.py
python verify_acceptance_assets.py
```

实际输出见 `tests/local_test_report.txt`、`tests/bundle_validation_report.txt`、`tests/acceptance_assets_validation_report.txt`、`tests/html_smoke_report.json` 和 `tests/document_consistency_report.json`。

## 未执行，不能据此宣称通过

未克隆、安装或启动 Hermes；未调用 DeepSeek；未实现完整前后端、实际 Adapter、专用学科检查器和试卷 PDF/DOCX 生产导出；未执行真实数据库迁移、权限/注入/故障恢复集成测试、并发压测、真实质量或费用统计。

G-MIN 与 G-FULL 均为 `NOT_RUN`。所有验收规程默认 `NOT_RUN`，报告中的真实 model_id、run_id、耗时、费用、通过率、执行人及签名均待实际运行填写。53 项离线测试不能替代 47 类真实验收用例，更不能证明出题准确率。

## 打包纪律

仅交付文档、模板、参考代码和文本/JSON 验证记录；不打包字体文件、API Key、临时渲染图/PDF、浏览器数据或 Python 缓存。`MANIFEST.sha256` 覆盖除其自身外全部包内文件。ZIP 完成后执行 CRC 与逐文件 SHA-256 校对。
