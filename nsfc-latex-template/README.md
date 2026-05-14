# NSFC 报告正文 LaTeX 模板（2026 版）

国家自然科学基金（NSFC）申请书 **报告正文** 的 LaTeX 模板，按基金委 2026 年最新格式要求改造，结构覆盖（一）立项依据 →（五）年度计划 + 研究基础与工作条件全部章节。

> 我用这套模板在 2026 年提交了面上申请。如果对你有帮助，欢迎 Star 或 Fork。

## 特色

- **一键编译**：`lualatex → bibtex → lualatex × 2`，与 Word 模板字号字距一致
- **章节骨架完整**：五大块 + 研究基础四小项，全部预置好"提纲提示语"
- **常用宏齐全**：`\myEmph{}` 加重、`\me{}` 标注申请人、`\citess{}` 上标引用、`\todo{}` 占位
- **上标引用**：`\citess{key}` 自动生成形如 [1] 的上标，便于阅读
- **参考文献紧凑**：自定义 `thebibliography` 环境，行距压紧节省版面

## 快速开始

```bash
git clone https://github.com/lian-xue721/nsfc-2026-latex-template.git
cd nsfc-2026-latex-template

# 编译（推荐 LuaLaTeX，对中文+楷体支持最稳）
lualatex main
bibtex   main
lualatex main
lualatex main
```

也可以用 XeLaTeX：把 `main.tex` 第一行改为 `%!TEX program = xelatex` 即可。

## 文件结构

```
nsfc-2026-latex-template/
├── main.tex            # 主文档（按基金委 2026 提纲）
├── nsfc.sty            # 样式文件（页面尺寸、字体、章节格式）
├── nsfc.bst            # GB/T 7714 风格的 bibtex 样式
├── references.bib      # 参考文献示例
├── figures/            # 图片目录
├── README.md
├── LICENSE             # MIT
└── .gitignore
```

## 字体说明

模板默认使用 **Fandol** 字体系列（CTeX 自带，无需额外安装）：
- 正文：`fandol` 字族
- 提纲提示语：`FandolKai-Regular`（楷体）
- 西文：`Latin Modern Roman`

如果系统已安装方正/founder 字体，可在 `main.tex` 顶部把 `fontset=fandol` 改为 `fontset=founder`，外观更接近基金委 Word 模板。

## 写作建议

每一节顶部都留了 `\todo{...}` 占位 + 注释行（以 `%` 开头），写作时按提示填空即可：

- **立项依据**：政策文件 + 国际前沿 + 切入点，三段式
- **关键科学问题**：建议 2-3 个，每个对应一个子课题
- **研究方案**：先放总体框架图，再分子课题展开
- **创新点**：用 `\myEmph{特色一：}` 加重标题，4-6 条为宜

## 常用宏速查

| 宏命令 | 用途 |
|---|---|
| `\myEmph{...}` | 深蓝色加粗，用于强调论点 |
| `\me{...}` | 黑体，用于在作者列表中标注申请人 |
| `\first` / `\cor` | 一作 / 通讯作者上标 |
| `\citess{key}` | 上标形式引用 |
| `\myCite{key}` | 标注"我们的工作" |
| `\todo{...}` | 红色占位符 |
| `\NsfcNote{...}` | 基金委提纲提示语（楷体+蓝色） |
| `\ContentDes{...}` | 大段标题（如"（一）立项依据"） |

## 已知问题

- 在 macOS 上若使用 MacTeX，首次编译可能报 Fandol 字体警告，再编译一次即可消失
- 部分 Linux 发行版需安装 `texlive-lang-chinese` 包
- `nsfc.bst` 对中文条目要求 `language = {chinese}` 字段（参见 `references.bib` 示例）

## License

MIT — 自由使用、修改、分发。如有改进欢迎提 PR。

## 致谢

样式基于 IEEE CVPR 模板改造，参考了网络上多位前辈分享的 NSFC LaTeX 版本。感谢所有公开模板的同行。
