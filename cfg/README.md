# Stash 订阅转换模板

本目录保存以 COCR 为基准、经过 Stash 兼容处理的订阅转换模板。项目已停止维护，不再自动生成或同步这些文件。模板只用于支持 `target=stash` 的订阅转换后端，不能直接导入 Stash。

全部 GeoSite 和 GEOIP 使用显式远程规则文件；规则链接统一通过 `cdn.jsdelivr.net` 获取。纯域名和 IP 使用 MRS，含关键词或正则的分类保留 Classical YAML。Fallback 版本保留其自动故障转移语义。

| 版本 | 模板 | 定位 |
| --- | --- | --- |
| 标准版 | [`Custom_Stash.ini`](https://cdn.jsdelivr.net/gh/Aethersailor/Custom_Stash_Rules@eef194e57e1505a6c2635000f8f7e00d4ecf5d82/cfg/Custom_Stash.ini) | 日常分流与复杂度均衡 |
| 标准故障转移版 | [`Custom_Stash_Fallback.ini`](https://cdn.jsdelivr.net/gh/Aethersailor/Custom_Stash_Rules@eef194e57e1505a6c2635000f8f7e00d4ecf5d82/cfg/Custom_Stash_Fallback.ini) | 标准版分流结构，主要业务组自动故障转移 |
| 轻量版 | [`Custom_Stash_Lite.ini`](https://cdn.jsdelivr.net/gh/Aethersailor/Custom_Stash_Rules@eef194e57e1505a6c2635000f8f7e00d4ecf5d82/cfg/Custom_Stash_Lite.ini) | 策略组较少，结构简洁 |
| 轻量故障转移版 | [`Custom_Stash_Lite_Fallback.ini`](https://cdn.jsdelivr.net/gh/Aethersailor/Custom_Stash_Rules@eef194e57e1505a6c2635000f8f7e00d4ecf5d82/cfg/Custom_Stash_Lite_Fallback.ini) | 轻量结构与自动故障转移结合 |
| 极简 GFW 版 | [`Custom_Stash_GFW.ini`](https://cdn.jsdelivr.net/gh/Aethersailor/Custom_Stash_Rules@eef194e57e1505a6c2635000f8f7e00d4ecf5d82/cfg/Custom_Stash_GFW.ini) | 主要处理 GFW 相关流量，其余流量默认直连 |
| 极简 GFW 故障转移版 | [`Custom_Stash_GFW_Fallback.ini`](https://cdn.jsdelivr.net/gh/Aethersailor/Custom_Stash_Rules@eef194e57e1505a6c2635000f8f7e00d4ecf5d82/cfg/Custom_Stash_GFW_Fallback.ini) | 极简分流与自动故障转移结合 |
| 重度分流版 | [`Custom_Stash_Full.ini`](https://cdn.jsdelivr.net/gh/Aethersailor/Custom_Stash_Rules@eef194e57e1505a6c2635000f8f7e00d4ecf5d82/cfg/Custom_Stash_Full.ini) | 业务、地区和节点用途分组更丰富 |
| 重度分流故障转移版 | [`Custom_Stash_Full_Fallback.ini`](https://cdn.jsdelivr.net/gh/Aethersailor/Custom_Stash_Rules@eef194e57e1505a6c2635000f8f7e00d4ecf5d82/cfg/Custom_Stash_Full_Fallback.ini) | 重度分流结构与自动故障转移结合 |
| Mainland 兼容文件 | [`Custom_Stash_Mainland.ini`](https://cdn.jsdelivr.net/gh/Aethersailor/Custom_Stash_Rules@eef194e57e1505a6c2635000f8f7e00d4ecf5d82/cfg/Custom_Stash_Mainland.ini) | 内容与标准版相同，仅保留兼容文件名 |

表中的模板下载链接固定到本次校正提交。规则远程资源保持上游更新。

调用示例：

```text
https://<支持 target=stash 的后端>/sub?target=stash&url=<URL 编码后的订阅地址>&config=https%3A%2F%2Fcdn.jsdelivr.net%2Fgh%2FAethersailor%2FCustom_Stash_Rules%40eef194e57e1505a6c2635000f8f7e00d4ecf5d82%2Fcfg%2FCustom_Stash.ini
```

后端需要支持 Stash 的 MRS、Classical Rule Provider 和对应的 `no-resolve` 选项。现有订阅需要重新转换并在 Stash 中更新配置；兼容处理边界见仓库首页。
