# Tatsukini-Neon-LiangWen-Status

NEON//SCOPE 插件：DeepSeek **峰谷价状态徽章**。在舞台里放一个模块，实时显示当前是
**梁文峰**（高峰价）还是**梁文谷**（空闲价）、距离下一次切换的秒级倒计时，以及随进度
推进的 31 档头像（`00` 普通人 → `30` 梁祖）。

> 纯本地计算：不联网、不需要 API Key、不读会话、不改账单。它只告诉你什么时候跑最便宜。

## 时段规则

取自 [DeepSeek 官方定价页](https://api-docs.deepseek.com/zh-cn/quick_start/pricing)：
北京时间周一至周五（不含法定节假日）**09:00–12:00、14:00–18:00** 为高峰，其余时段
（含周末、法定节假日全天）为空闲。时区固定按北京时间（UTC+8）。

## 安装

在 NEON//SCOPE 桌面版 / 浏览器版的插件管理器（Plugins 页）里，选择「从 GitHub 安装」，
填入：

```text
Tatsukini/Tatsukini-Neon-LiangWen-Status
```

安装并启用后，模块库里会出现「梁文峰/谷 状态」，拖到舞台即可。

## 选项

| 选项 | 说明 |
| --- | --- |
| 显示头像 | 是否绘制圆形档位头像 |
| 背景压暗 | 模块背景黑幕不透明度（0–60%） |

## 许可

- 代码：MIT（见 `LICENSE`）。
- 31 张档位图：来自第三方 MIT 项目，详见 `THIRD-PARTY-NOTICES.md`。
- 峰谷日历逻辑移植自 [sukholovskyyy/dsh-liang-price-badge](https://github.com/sukholovskyyy/dsh-liang-price-badge)（MIT）。

## 免责声明

纯属网络恶搞与视觉玩梗，不代表梁文锋、DeepSeek 或任何机构的真实观点。
