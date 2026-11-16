# Tatsukini-Neon-LiangWen-Status

NEON//SCOPE 插件：仿桌面挂件的 DeepSeek **峰谷价 / 余额状态徽章**。在舞台里放一个模块，显示

- **峰/谷 倒计时**：距离下一次峰谷切换的秒级倒计时；
- **梁文 + 状态字**：末字随状态切换为 **峰 / 谷 / 满 / 停 / 崩 / 活**（仿桌面版优先级）；
- **31 档头像**：随峰谷进度推进（`00` 普通人 → `30` 梁祖）；
- **实时余额**：底部显示按当前模型推算的「未命中 / 命中 / 输出」token 额度。

> 峰谷日历为纯本地计算；余额需在你填的 API Key 下联网查询 `GET /user/balance`。
> 不填 Key 时只走本地峰谷逻辑，底部显示「余量未知」。

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

安装并启用后，模块库里会出现「梁文 状态徽章」，拖到舞台即可。需要 **NEON//SCOPE 1117_2 及以上**
（提供 `context.settings` / `context.net.fetch` / `context.assets` 等插件 API）。

## 设置

配置分两处：敏感项放插件级设置，非敏感项随模块保存在「模块专属」里。

### 插件设置（插件管理器 → 设置）

**只保存在本机**，不会写入 `.NEON` 工程存档，分享工程不会带走密钥。

| 设置 | 说明 |
| --- | --- |
| API Key | 掩码输入；用于查询余额，只存本机 |
| Base URL | 默认 `https://api.deepseek.com` |
| 轮询间隔(秒) | 余额查询频率，默认 60 |
| 超时(秒) | 单次查询超时，默认 12 |

### 模块专属（选中模块后在右侧检视器调整）

随模块保存进 `.NEON` 工程存档，可每个模块各设一套。

| 选项 | 说明 |
| --- | --- |
| 模型 | flash / pro，影响 token 换算单价 |
| 背景图 | 选择本地图片铺满模块背景 |
| 显示头像 | 是否绘制圆形档位头像 |
| 背景压暗 | 背景黑幕不透明度（0–60%） |

## 权限与数据

声明权限：`modules`、`network`、`storage`、`assets`。

- `network`：仅用于 `GET /user/balance` 查询你的账户余额；CORS 失败时自动经宿主本机代理兜底。
- `storage` / `assets`：保存上面的本机设置与背景图。
- 插件不读取或上传你的工程、音频、会话等私有数据，也不会改账单。

token 换算单价（元 / 百万 token，可在桌面版 `config.json` 调整，插件内为内置默认）：

| 模型 | 缓存命中 | 缓存未命中 | 输出 |
| --- | --- | --- | --- |
| flash | 1 | 4 | 16 |
| pro | 4 | 16 | 64 |

## 许可

- 代码：MIT（见 `LICENSE`）。
- 31 张档位图：来自第三方 MIT 项目，详见 `THIRD-PARTY-NOTICES.md`。
- 峰谷日历逻辑移植自 [sukholovskyyy/dsh-liang-price-badge](https://github.com/sukholovskyyy/dsh-liang-price-badge)（MIT）。

## 免责声明

纯属网络恶搞与视觉玩梗，不代表梁文锋、DeepSeek 或任何机构的真实观点。
