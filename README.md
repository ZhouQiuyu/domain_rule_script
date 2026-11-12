# Loon 自定义分流规则集 (domain_rule_script)

本项目用于集中管理个人 Loon 自定义分流规则，并在 Loon 中通过 `[Remote Rule]` 实现云端自动拉取与同步。

---

## 规则文件与策略组映射

| 规则文件 | 说明 | 对应策略组建议 | Raw 订阅地址 |
| :--- | :--- | :--- | :--- |
| `rules/AI_Relay.list` | 所有用过的 AI 中转站、上游网关及核心 AI 平台 | `AI节点` | `https://raw.githubusercontent.com/ZhouQiuyu/domain_rule_script/main/rules/AI_Relay.list` |
| `rules/Custom_US.list` | 个人未分类与特定代理服务（Figma、R星、虚拟卡等） | `美国节点` | `https://raw.githubusercontent.com/ZhouQiuyu/domain_rule_script/main/rules/Custom_US.list` |
| `rules/Custom_Direct.list` | 个人直连、Tailscale 专网与内网网段 | `DIRECT` | `https://raw.githubusercontent.com/ZhouQiuyu/domain_rule_script/main/rules/Custom_Direct.list` |
| `rules/Bybit.list` | Bybit 交易所主站、CDN、App 及 API 网关域名 | `台湾节点` / `日本节点` / `韩国节点` | `https://raw.githubusercontent.com/ZhouQiuyu/domain_rule_script/main/rules/Bybit.list` |

---

## 在 Loon 配置文件中的添加方式

将以下内容加入到 Loon 配置文件的 `[Remote Rule]` 区域的最顶部（确保个人优先匹配）：

```ini
[Remote Rule]
https://raw.githubusercontent.com/ZhouQiuyu/domain_rule_script/main/rules/AI_Relay.list, policy=AI节点, tag=AI中转站, enabled=true
https://raw.githubusercontent.com/ZhouQiuyu/domain_rule_script/main/rules/Custom_US.list, policy=美国节点, tag=个人未分类代理, enabled=true
https://raw.githubusercontent.com/ZhouQiuyu/domain_rule_script/main/rules/Custom_Direct.list, policy=DIRECT, tag=个人直连与内网, enabled=true
https://raw.githubusercontent.com/ZhouQiuyu/domain_rule_script/main/rules/Bybit.list, policy=台湾节点, tag=Bybit, enabled=true
```
