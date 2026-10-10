<%*
const ids = app.vault.getMarkdownFiles()
  .filter(f => f.path.startsWith("Problem Hands/hands/"))
  .map(f => Number(app.metadataCache.getFileCache(f)?.frontmatter?.id) || 0);
const nextId = Math.max(0, ...ids) + 1;
const title = (await tp.system.prompt("牌例标题（如：HFA #3 / 13 3NT）")) || "未命名";
const safe = title.replace(/[#^\[\]|\\/:*?"<>]/g, " ").replace(/\s+/g, " ").trim();
await tp.file.move(`Problem Hands/hands/${String(nextId).padStart(3, "0")} ${safe}`);
-%>
---
id: <% nextId %>
title: "<% title %>"
aliases:
  - "<% title %>"
date: <% tp.date.now("YYYY-MM-DD") %>
event:
platform: BBO
issue: []
topics: []
importance: 中
done: false
summary:
hardy: []
cover:
---

<!-- 粘贴牌图；把第一张图的链接填到 cover，例如 "[[xxx.png]]" -->
<!-- hardy 填 README 中对应章节，例如 "[[hardy-2o1-vault/README#花色争叫|花色争叫]]" -->

