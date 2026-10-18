# Custom_Stash_Rules

> [!IMPORTANT]
> 由于维护者已不再使用 Stash 作为主力客户端，本项目已停止维护并归档，不再更新或同步 Stash 模板。以下文档和模板仅作历史参考。

本仓库保存面向 Stash 的订阅转换模板。归档前最后一次配置校正以 [`Aethersailor/Custom_OpenClash_Rules`](https://github.com/Aethersailor/Custom_OpenClash_Rules) 为策略基准，单独处理 Stash 的规则资源和策略组兼容性。所有规则远程链接均使用 `cdn.jsdelivr.net`。

## 使用方法

这些 `.ini` 文件是订阅转换模板，不是 Stash 运行配置，不能直接导入 Stash。转换请求需要同时提供订阅地址、`target=stash` 和模板地址：

```text
https://<支持 target=stash 的后端>/sub?target=stash&url=<URL 编码后的订阅地址>&config=<URL 编码后的模板地址>
```

标准版模板地址：

```text
https://cdn.jsdelivr.net/gh/Aethersailor/Custom_Stash_Rules@main/cfg/Custom_Stash.ini
```

完整模板列表见 [`cfg/README.md`](cfg/README.md)。

## 基准与兼容处理

`SOURCE_REVISION` 记录最后一次校正采用的 COCR 提交。全部 9 个模板保留对应 COCR 版本的规则优先级、策略组类型和候选顺序；`Custom_Stash_Mainland.ini` 与标准版内容相同。项目不再自动生成或跨仓库同步模板。

- GeoSite 和 GEOIP 均替换为 MetaCubeX 的显式远程规则文件，避免依赖 Stash 内置数据源中不存在的分类。已移除 COCR 不再使用的 `google-cn`，国内游戏使用 `category-games-cn`。
- 纯域名和 IP 集合使用 Stash 支持的 MRS 格式；含 `DOMAIN-KEYWORD` 或 `DOMAIN-REGEX` 的 GeoSite 分类使用 Classical YAML，保留完整匹配语义。
- 保留 COCR 自定义规则来源中的域名关键词和目标端口规则。`SRC-PORT,41641` 未输出，避免依赖仅较新 Beta 版本才支持的源端口规则。
- 保留 Fallback 策略和原有直连候选。策略组采用当前转换器可输出的 `interval`；不照搬 Clash 的组级测速 URL、超时和容差参数，复杂节点筛选沿用可移植表达式或已有自动组。
- 规则文件仍按配置的间隔从上游更新；仓库归档不代表这些远程规则被冻结。

## 使用边界

- 转换后端必须明确支持 `target=stash`。
- 服务端转换成功和 YAML 结构校验通过，不等于已经完成 Stash 真机验收。
- 使用前仍需检查 Proxy Provider、Rule Provider、DNS 查询、规则命中和代理连通。
