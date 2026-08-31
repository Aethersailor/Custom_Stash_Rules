# Stash 订阅转换模板

本目录中的文件由 `Custom_OpenClash_Rules` 自动生成。模板只用于支持 `target=stash` 的订阅转换后端，不要直接导入 Stash，也不要手工修改。

| 版本 | 模板 | 定位 |
| --- | --- | --- |
| 标准版 | [`Custom_Stash.ini`](Custom_Stash.ini) | 日常分流与复杂度均衡 |
| 标准故障转移版 | [`Custom_Stash_Fallback.ini`](Custom_Stash_Fallback.ini) | 标准版分流结构，主要业务组自动故障转移 |
| 轻量版 | [`Custom_Stash_Lite.ini`](Custom_Stash_Lite.ini) | 策略组较少，结构简洁 |
| 轻量故障转移版 | [`Custom_Stash_Lite_Fallback.ini`](Custom_Stash_Lite_Fallback.ini) | 轻量结构与自动故障转移结合 |
| 极简 GFW 版 | [`Custom_Stash_GFW.ini`](Custom_Stash_GFW.ini) | 主要处理 GFW 相关流量，其余流量默认直连 |
| 极简 GFW 故障转移版 | [`Custom_Stash_GFW_Fallback.ini`](Custom_Stash_GFW_Fallback.ini) | 极简分流与自动故障转移结合 |
| 重度分流版 | [`Custom_Stash_Full.ini`](Custom_Stash_Full.ini) | 业务、地区和节点用途分组更丰富 |
| 重度分流故障转移版 | [`Custom_Stash_Full_Fallback.ini`](Custom_Stash_Full_Fallback.ini) | 重度分流结构与自动故障转移结合 |
| Mainland 兼容文件 | [`Custom_Stash_Mainland.ini`](Custom_Stash_Mainland.ini) | 内容与标准版相同，仅保留兼容文件名 |

调用示例：

```text
https://test-api.asailor.org/sub?target=stash&url=<URL 编码后的订阅地址>&config=https%3A%2F%2Fraw.githubusercontent.com%2FAethersailor%2FCustom_Stash_Rules%2Fmain%2Fcfg%2FCustom_Stash.ini
```

`test-api.asailor.org` 用于开发版本和模板的端到端验证，不提供生产可用性承诺。使用其他后端前，请确认该后端明确支持 `target=stash`。
