# 开源创新思维 · 第七周作业

软件许可测试报告：使用 Trivy 0.76.1 对 Apache Dubbo 3.3.6 源码树进行许可证扫描。

## 作业信息

| 项目 | 内容 |
| --- | --- |
| 学号 | f25011308 |
| 姓名 | 陆文雨 |
| 班级 | f250117 |
| 开源项目 | Apache Dubbo 3.3.6 |
| 测试工具 | Trivy 0.76.1（`--scanners license --license-full`） |
| 报告文件 | `f25011308-陆文雨-Apache Dubbo-软件许可测试报告.docx` |

## 报告要点

- 扫描 4,758 个文件，输出 3,981 条文件级许可证记录，Java 覆盖率 99.97%。
- 识别出 Apache-2.0、MIT、BSD-3-Clause 三类许可证，未发现 GPL/AGPL/SSPL 等强 copyleft。
- 主要风险：`ProtoTypeMap.java` 的 BSD-3-Clause 仅有名称引用、缺少全文，工具亦漏检。
- 运行时依赖中还有 CDDL/EPL 各 6 项，需随分发附许可证与通知，并用 SBOM 补足依赖视角。

## 复现命令

```powershell
trivy fs --scanners license --license-full --offline-scan --skip-files "**/pom.xml" `
  --format json --output output/trivy_dubbo.json data/dubbo-src/apache-dubbo-3.3.6-src
```

报告全文见同名 `.docx` 文件。
