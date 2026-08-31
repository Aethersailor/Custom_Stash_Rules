# Custom_Stash_Rules

本仓库保存面向 Stash 的订阅转换模板。模板由
[`Aethersailor/Custom_OpenClash_Rules`](https://github.com/Aethersailor/Custom_OpenClash_Rules)
中的 `py/generate_stash_configs.py` 自动生成，不在本仓库中手工维护。

## 使用方法

这些 `.ini` 文件是订阅转换模板，不是 Stash 运行配置，不能直接导入 Stash。转换请求需要同时提供订阅地址、`target=stash` 和模板地址：

```text
https://<支持 target=stash 的后端>/sub?target=stash&url=<URL 编码后的订阅地址>&config=<URL 编码后的模板地址>
```

标准版模板地址：

```text
https://raw.githubusercontent.com/Aethersailor/Custom_Stash_Rules/main/cfg/Custom_Stash.ini
```

jsDelivr 地址：

```text
https://cdn.jsdelivr.net/gh/Aethersailor/Custom_Stash_Rules@main/cfg/Custom_Stash.ini
```

完整模板列表见 [`cfg/README.md`](cfg/README.md)。

## 自动生成

`SOURCE_REVISION` 记录每批模板对应的 `Custom_OpenClash_Rules` 提交。源仓库完成规则和兼容文件生成后，会通知本仓库检出该提交并重新生成 `cfg/Custom_Stash*.ini`。

不要直接修改生成文件。需要调整规则、策略组或 Stash 兼容逻辑时，请在源仓库修改对应的 Clash 模板或生成器。

## 使用边界

- 转换后端必须明确支持 `target=stash`。
- 服务端转换成功和 YAML 结构校验通过，不等于已经完成 Stash 真机验收。
- 使用前仍需检查 Proxy Provider、Rule Provider、DNS 查询、规则命中和代理连通。
