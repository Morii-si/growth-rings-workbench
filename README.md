# Growth Rings

沉淀每一轮研究，接续每一次判断。

这是已完成界面设计的纯前端研究工作台 Demo。以泡泡玛特为案例，支持 V1 初始研究、V2 全年业绩、V3 半年报新材料、未来待跟进，以及历史讨论和本轮批注。

## 运行与部署

Node.js 20.19+（20.x）或 22.12+，建议 Node.js 24。

```sh
npm ci
npm run dev
```

开发服务默认端口 5173，也支持 `PORT` 环境变量。

平台若用自定义域名反向代理开发服务，并出现 Vite 的 “Blocked request” 提示，可设置 `__VITE_ADDITIONAL_SERVER_ALLOWED_HOSTS` 为该预览域名；不要把任意主机都加入允许列表。正式静态部署 `dist/` 不需要此配置。

```sh
npm test
npm run build
npm run preview
```

部署 `dist/` 目录。构建只发生在开发环境；部署产物仅 HTML、CSS、JavaScript、Logo，不需要 Node 服务端、数据库、API Key 或后端接口。根目录已有 `index.html`，原始源码也可由标准静态 HTTP 服务直接托管。请不要使用 `file://` 双击原始入口，ES module 需要 HTTP(S)。

相对资源路径支持根目录或子目录部署。阶段链接为 `?view=rail&version=1`、`version=2`、`version=3`、`version=future`，推荐首次打开 V1。

## 功能边界

- 研究数据、历史对话和资料摘录预先放在前端文件中。
- 选中文字批注、批注编辑/移除、成批发送和跟进计划可在浏览器中操作。
- “一起发送”保存前端演示批次，显示“已模拟发送”；没有真实 AI API 请求或自动生成回复。
- “更新判断”功能已从 Demo 移除，不要恢复其入口。
- 跟进提醒只检查预置披露；没有后台定时监控、推送或实时数据服务。
- 用户输入保存在当前网址的 localStorage，刷新可恢复。换网址、换浏览器或清除存储后不会自动迁移。JSON 导出是备份，当前没有导入界面。
- 公告是港交所 HTTPS PDF 外链，联网后在新窗口打开；不会随代码下载，也不能承诺离线打开。IP 研究参考资料入口显示内置摘录，未包含原始 PPT 全文。

## 平台预览要求

独立 HTTPS 页面可完整运行。若使用 iframe，请允许脚本、同源存储、打开新窗口及文件下载（常见 sandbox 权限为 `allow-scripts allow-same-origin allow-popups allow-downloads`；PDF 新窗口可能还需 `allow-popups-to-escape-sandbox`）。权限由平台控制，源码无法绕过。

尚未在 REDcowork 真正导入并发布；已完成独立静态环境和 iframe 条件测试，不能以本地通过代替平台验收。

系统字体会随操作系统略有差别。Logo 已随仓库提供；页面不依赖远程字体、CDN 或运行时 npm 网络请求。

## 导入 REDcowork

见 [REDcowork 导入提示词](RED_COWORK_IMPORT.md)。保留现有源码、布局和数据，直接启动或构建，不要根据产品描述重新生成页面。
