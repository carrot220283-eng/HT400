# 400 Tricks You Can Do · 中文卡片知识库

Howard Thurston《400 Tricks You Can Do》的中文卡片库，供魔术社团知识库（Dify 等 RAG）使用。
**一次提问只返回一张卡**：中文名 + 英文原名 + 元数据 + 效果 + 方法步骤 + 提示 + 原页截图。

- 原书：258 页扫描件，正文 21–255 页，26 章、387 个魔术（原书标注约 400 个，个别编号被 OCR 丢失）
- 卡片：387 张，编号 = 章缩写 + 章内序号（如 `BT-001` = BALL TRICKS 第 1 个）
- 图：615 张原页裁图（跨页魔术给两张），灰度 JPEG，宽 1000px

## 目录结构

```
img/            615 张裁图（bt-001-1.jpg、bt-001-2.jpg …）
cards/          387 个 .md（知识库导入用）+ 387 个 .html（浏览器直接看）
txt/            26 个 .txt，按章打包，卡片之间用 <<<KBCARD>>> 分隔（Dify 导入用）
cards.json      全部卡片的结构化数据
index.json      精简索引（标题/章/页/道具/难度/时长/场合）
```

## 两种用法

### A. 导入 Dify（推荐，只需传 26 个文件）

1. 知识库 → 导入已有文本 → 上传 `txt/c01.txt` … `txt/c26.txt`（26 个）
2. 分段：**通用分段**，分隔符 `<<<KBCARD>>>`，最大分段长度 `4000`，重叠 `0`
   → 结果应为 **387 个分段，每个分段正好是一张卡**
3. 索引：高质量，嵌入模型 `BAAI/bge-m3`
4. 检索：混合检索，TopK `1`，阈值关闭

> 分隔符只出现一次一卡之间，正文里不会出现，所以每段不会被切断。分段模式建后不可改。

### B. 浏览器直接看

打开 `cards/bt-001.html` 这类文件即可（图片用相对路径 `../img/`），适合手机/电脑直接翻阅，也可以直接部署成 GitHub Pages。

## 卡片字段（cards.json）

```json
{
  "id": "BT-001", "no": 1,
  "chapter": "BALL TRICKS", "chapter_cn": "球类魔术",
  "trick_no": 1, "title_en": "THE APPEARING BALL", "title_cn": "浮现的球",
  "pages": [21, 22],
  "props": ["木球（内嵌小钉）", "一英寸细线", "戒指"],
  "difficulty": "入门", "duration": "1 分钟", "setting": "桌面",
  "needs_assistant": "否",
  "effect_cn": "……", "method_cn": ["步骤 1", "步骤 2"], "note_cn": "……",
  "text_en": "英文原文（OCR，校对用）",
  "images": ["bt-001-1.jpg", "bt-001-2.jpg"]
}
```

## 说明

- 英文原文由 PDF 内嵌 OCR 层重建（原 OCR 逐词写入且带倾斜，已按基线重新聚类），个别单词仍有识别错误（如 `ringer`→`finger`、`ana`→`and`）。
- 中文译文由 7 名翻译并行完成，技术术语（palm/pass/force/palm…）、人名、书名、商品名保留英文。
- 少数卡片 `note_cn` 注明「原文此处不全」，表示原书该处在 OCR 中残缺，未凭想象补写。
