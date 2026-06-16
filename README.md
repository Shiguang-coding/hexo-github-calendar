# hexo-github-calendar

在 Hexo 博客中显示 GitHub 贡献度热力图的插件。

![image-20260616163049977](https://img.shiguang666.eu.org/file/1781598658400_20260616163050866.webp)

基于 [Barry-Flynn/hexo-github-calendar](https://github.com/Barry-Flynn/hexo-github-calendar) 修复，原项目 fork 自 [Zfour/hexo-github-calendar](https://github.com/Zfour/hexo-github-calendar)。

## 相对上游的改动

> 最后更新：2026-06-16

1. **修复 Retina 高分屏月份标签偏移**：`hexo_githubcalendar.js` 中月份标签定位使用了 `github_calendar_c.width`（Retina 缩放后的值），改为使用原始 `width` 变量
2. **修复 Tooltip 坐标错位**：`getMousePos` 函数中坐标转换使用了 `canvas.width / rect.width`，改为直接使用 CSS 像素坐标
3. **同步修复 `githubcalendar.js`**：独立版本的 tooltip 坐标同样已修复

## 安装

### npm 安装（推荐）

```bash
npm i @shiguang-coding/hexo-github-calendar --save
```

### 从 GitHub 直接安装

```bash
npm i github:Shiguang-coding/hexo-github-calendar --save
```

### cnpm 安装

```bash
cnpm i @shiguang-coding/hexo-github-calendar --save
```

## 配置

在 Hexo 项目根目录的 `_config.yml` 中添加（注意是 Hexo 配置文件，不是主题配置文件）：

```yaml
githubcalendar:
  enable: true
  enable_page: /
  user: 你的GitHub用户名
  layout:
    type: id
    name: recent-posts
    index: 0
  githubcalendar_html: '<div class="recent-post-item" style="width:100%;height:auto;padding:10px;"><div id="github_loading" style="width:10%;height:100%;margin:0 auto;display: block"><svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"  viewBox="0 0 50 50" style="enable-background:new 0 0 50 50" xml:space="preserve"><path fill="#d0d0d0" d="M25.251,6.461c-10.318,0-18.683,8.365-18.683,18.683h4.068c0-8.071,6.543-14.615,14.615-14.615V6.461z" transform="rotate(275.098 25 25)"><animateTransform attributeType="xml" attributeName="transform" type="rotate" from="0 25 25" to="360 25 25" dur="0.6s" repeatCount="indefinite"></animateTransform></path></svg></div><div id="github_container"></div></div>'
  pc_minheight: 280px
  mobile_minheight: 0px
  color: "['#ebedf0', '#a2f7af', '#6ce480', '#54ad63', '#469252', '#31753c', '#1f5f2a', '#13531f', '#084111', '#032b09', '#000000']"
  api: 你的自建API地址
  calendar_js: /js/hexo_githubcalendar.js
  plus_style: ""
```

> **推荐使用本地 JS 文件**：将 `hexo_githubcalendar.js` 下载到主题 `source/js/` 目录下，重装 npm 包不会覆盖。

## 本地预览

```bash
hexo clean && hexo g && hexo s
```

## 配套后端 API

前端插件需要配合后端 API 使用。推荐自建 API：

- [Shiguang-coding/python_github_calendar_api](https://github.com/Shiguang-coding/python_github_calendar_api)（已修复 Python 3.12 兼容性和 GitHub 爬虫问题）

## 演化链路

[Zfour/hexo-github-calendar](https://github.com/Zfour/hexo-github-calendar) → [Barry-Flynn/hexo-github-calendar](https://github.com/Barry-Flynn/hexo-github-calendar) → [Shiguang-coding/hexo-github-calendar](https://github.com/Shiguang-coding/hexo-github-calendar)

## License

MIT
