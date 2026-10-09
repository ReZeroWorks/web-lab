# Web Lab

> ReZeroWorks 统一的公开 Web 成品部署仓库。

**Web Lab 不是业务源码仓库。**

各项目在独立的 Private Repository 中开发、测试和维护；完成验证后，仅将可公开访问的静态构建产物发布到本仓库。

## 🌐 Online

- Web Lab：`https://rezeroworks.github.io/web-lab/`
- GitHub Pages：`main / (root)`

## 📦 Projects

| Project | Description | Source | Online |
| --- | --- | --- | --- |
| [大明仕途录](./ming-career/) | 明代科举、官职迁转与政务抉择模拟游戏 | `ReZeroWorks/ming-career-mini` 🔒 | `/ming-career/` |

## 🧭 Repository Responsibilities

```text
Private repositories                    Public Web Lab

ming-career-mini  ── build / verify ──▶ web-lab/ming-career/
project-b         ── build / verify ──▶ web-lab/project-b/
project-c         ── build / verify ──▶ web-lab/project-c/
```

### Private project repository

负责：

- 业务源码
- 原始图片 / 设计素材
- 剧情和数据源
- 测试代码
- 构建脚本
- 技术文档
- Git 开发历史
- 可复现的构建过程

### `web-lab`

只负责：

- HTML / CSS / JavaScript 静态成品
- 浏览器实际运行所需资源
- 项目入口
- GitHub Pages 托管

## 📁 Directory Convention

每个项目必须拥有独立的一级目录：

```text
web-lab/
├── index.html
├── README.md
├── .nojekyll
│
├── ming-career/
│   ├── index.html
│   └── ...
│
├── project-b/
│   ├── index.html
│   └── ...
│
└── project-c/
    ├── index.html
    └── ...
```

目录名要求：

- 使用 lowercase kebab-case。
- 使用稳定的产品名，而不是临时版本名。
- 不在目录名中添加 `-web`、`-dist`、`-build`。
- 版本升级默认覆盖同一项目目录，保持外部 URL 稳定。

例如：

```text
✅ /ming-career/
✅ /chess-arena/
✅ /novel-lab/

❌ /ming-career-v5/
❌ /ming-career-web/
❌ /myNewGame/
```

## 🚀 Publishing Workflow

标准发布流程：

```text
1. 在 Private Repository 开发
              ↓
2. 完成功能与内容 Review
              ↓
3. 执行自动化测试 / 浏览器测试
              ↓
4. 生成 production 静态构建
              ↓
5. 检查移动端、资源路径、存档与核心流程
              ↓
6. 将构建产物同步到 web-lab/<project>/
              ↓
7. 核对 Public 文件与本地构建产物一致
              ↓
8. 使用固定 URL 交付
```

**不要直接在 Web Lab 中开发业务功能。**

线上发现问题时，应优先：

```text
Private Source
→ 修复
→ 测试
→ 重新构建
→ 发布
```

而不是长期直接修改构建产物。

## 🔒 Public / Private Boundary

本仓库是 Public。

因此提交前默认认为：

> **任何进入 `web-lab` 的内容，任何人都可以读取。**

禁止提交：

- API Key / Token
- 密码和账号凭据
- Private Repository 的敏感配置
- 私有设计资料
- 未计划公开的数据
- 用户隐私数据
- 服务端 Secret
- 仅供开发使用的内部文档

纯前端 JavaScript 即使经过压缩，也不能视为秘密。

## 💾 User Data

Web Lab 项目默认是静态站点。

如项目使用 `localStorage` / `IndexedDB`：

- 数据只属于当前浏览器环境。
- 不同设备、不同浏览器默认互不共享。
- 不应假设存在账号或云同步。
- 修改存档 Schema 时必须考虑旧版本迁移。
- 不允许把用户存档硬编码进 Public 构建。

如果未来需要真正的账号、数据库或跨设备同步，应由对应项目单独设计后端，而不是让 Web Lab 承担该职责。

## 📱 Web Quality Baseline

公开项目至少应验证：

- Desktop Chrome / Safari 基础可用
- 手机浏览器可滚动，不裁剪关键操作
- 320px 窄屏无横向溢出
- 微信 WebView 等内置浏览器有合理降级
- 按钮具有明确点击反馈
- 连续点击不会重复提交/重复结算
- 页面刷新后状态符合项目设计
- 静态资源路径在 GitHub Pages 子目录下正确
- JavaScript 启动失败时不出现无信息黑屏
- 新版本避免被旧静态资源缓存污染

## 🔗 URL Stability

项目公开后，应尽量保持 URL 长期稳定。

例如：

```text
https://rezeroworks.github.io/web-lab/ming-career/
```

后续 V6、V7……默认仍发布到：

```text
/ming-career/
```

版本属于项目内部概念，不应迫使外部用户更换链接。

---

Built and maintained under **ReZeroWorks**.
