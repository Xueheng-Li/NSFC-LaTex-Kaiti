# 🎯 国家自然科学基金LaTeX模板 (2026版)

> 基于 [NSFC-LaTex](https://github.com/MCG-NKU/NSFC-LaTex) 修改，**已更新至2026年官方模板**，结构与国家自然科学基金委员会发布的Word模板完全一致。

## 🆕 2026版重大更新

**本次更新依据2026年官方Word模板进行了全面修订，确保LaTeX模板与官方要求完全一致。**

### 结构调整（三部分 → 四部分）
2026年申请书正文结构调整为四部分：
- **（一）立项依据** - 为什么要开展此项研究，研究的科学技术价值如何
- **（二）研究内容** - 提纲不做限制，请按照研究工作的自身逻辑撰写
- **（三）研究基础** - 研究基础与可行性分析、工作条件、科研项目情况等
- **（四）其他需要说明的情况** - 申请人相关情况说明

### 内容变化
- **研究内容**：放宽要求，"提纲不做限制，请按照研究工作的自身逻辑撰写"
- **研究基础**：增加"研究风险的应对措施"
- **工作条件**：更新为"国家实验室、全国重点实验室和部门重点实验室"

### 青年项目特殊说明
- 青年科学基金项目更名为**C类**
- 2026年实行**经费包干制**，无需编制预算
- 资助期限3年
- 相关条款只涉及"申请人"，不含"主要参与者"
- 年龄要求（2026年）：
  - 男性：1991年1月1日（含）以后出生
  - 女性：1986年1月1日（含）以后出生

## ✨ 模板样式改进（2026年实际申请书迭代版）

以下改进基于2026年面上项目申请书的实际撰写和调试经验，已回馈至模板：

### `nsfc.sty` 样式文件
| 改动 | 旧版 | 新版 | 效果 |
|------|------|------|------|
| 段落间距 | `0.5\baselineskip` | `0.3\baselineskip` | 更紧凑，节省页数 |
| `\NsfcSection` 字号 | `\large`（约14.4pt） | `\fontsize{14pt}{18pt}` | 精确控制节标题字号 |
| `\NsfcSection` 字体 | bold+italic+蓝色 | bold+蓝色（去斜体） | 标题更庄重，与官方风格一致 |
| `\subsection` 缩进 | `\z@`（无缩进） | `2\ccwd`（两字符） | 与中文段落缩进对齐 |
| `\subsection` 间距 | `{11pt}{6pt}` | `{6pt}{3pt}` | 更紧凑 |
| `\subsection` 颜色 | 黑色 | 蓝色（`MSBlue`） | 与 `\NsfcSection` 风格统一 |
| `\subsubsection` | 无定义 | 新增，`2\ccwd` 缩进，正文字号加粗 | 支持三级标题 |
| `\ContentDes` 计数器 | `\setcounter{section}{0}` | `\stepcounter{section}` + `\setcounter{subsection}{0}` | 各部分内子节编号正确递增 |
| 参考文献编号 | 无 | 新增 `etoolbox` 自动编号 | 文末文献列表自动加序号，正文保持 author-year |

### `面上_main.tex` 主文件
| 改动 | 说明 |
|------|------|
| `AutoFakeBold=true` | STKaiti 无原生粗体，XeLaTeX 合成粗体，`\textbf` 正常显示 |
| `\setmainfont{Times New Roman}` | 西文字体统一为 Times New Roman |
| 正文字号 `13pt/17pt` | `\normalsize` 覆盖为 13pt 字号、17pt 行距，比默认 12pt 更易读 |
| `[round,sort]{natbib}` | 去掉 `authoryear`（由 bst 文件控制），加 `sort` 排序 |
| 新增宏包 | `tcolorbox`, `float`, `multirow`, `array`, `longtable`, `tabularx`, `tikz` |
| `REF` 环境 | 用于在正文内嵌参考文献列表（如立项依据末尾），12pt 字号 |
| 定理类命令 | `\conjecture`, `\define`, `\lemma`, `\property`, `\proposition` |
| 标题页提示 | "30页"限制改为**红色加粗**，"请勿删除"改为**蓝色加粗**（去斜体） |
| `\setcounter{page}{1}` | 显式设置正文起始页码 |

### 结构变化
| 改动 | 说明 |
|------|------|
| **分文件编辑结构** | 新增 `面上_main.tex` + 4个 part 文件，大文档按部分分文件管理 |
| 提示文字缩进 | hint text 改用 `\noindent\hspace{\parindent}` 对齐正文首行 |
| 第（四）部分 `\NsfcSection` | `#2` 留空，全部文字移入 `#3`，呈现为非粗体蓝色 |

## 📁 文件结构

```
NSFC-LaTex-Kaiti/
├── 面上_main.tex              # ★ 面上项目主编译入口（分文件结构）
├── 面上_cover.tex             # 封面页与摘要（提交时在 _main.tex 中取消注释）
├── 面上_part1_立项依据.tex    # 第一部分
├── 面上_part2_研究内容.tex    # 第二部分
├── 面上_part3_研究基础.tex    # 第三部分
├── 面上_part4_其他.tex        # 第四部分
├── 青年.tex                   # 青年科学基金项目（C类）模板（含撰写指导）
├── 青年_blank.tex             # 青年项目空白模板（仅标题框架）
├── 官方模版/                  # 2026年官方Word模板（供参考对照）
├── nsfc.sty                   # LaTeX 样式文件
├── nsfc.bst                   # 参考文献格式（数字）
├── gbt7714-author-year.bst    # 参考文献格式（author-year，推荐）
├── Cmm.bib                    # 参考文献数据库示例
├── figures/                   # 图片文件夹
├── prepare/                   # 准备文件（PPT模板等）
└── README.md                  # 本文件
```

## 🚀 使用方法

### 编译要求
- **必须使用 XeLaTeX**（楷体字体 STKaiti + ctex 依赖）
- **平台支持**：Windows、macOS、Linux

### 编译命令
```bash
# 完整编译（带参考文献）
xelatex 面上_main.tex && bibtex 面上_main && xelatex 面上_main.tex && xelatex 面上_main.tex

# 快速编译（不更新参考文献）
xelatex 面上_main.tex

# 青年项目
xelatex 青年.tex && bibtex 青年 && xelatex 青年.tex && xelatex 青年.tex
```

> 切换引用格式（author-year ↔ 数字）后需删除 `.aux` `.bbl` `.blg` 再完整编译。

### 引用格式
当前默认为**混合格式**：正文 author-year 引用（如 `(Smith, 2020)`），文末参考文献列表自动添加序号（`nsfc.sty` 通过 `etoolbox` 实现）。

在 `面上_main.tex` 中设置 natbib：
```latex
\usepackage[round,sort]{natbib}
```

在 `面上_part1_立项依据.tex`（或其他含参考文献的 part 文件）末尾添加：
```latex
\bibliographystyle{gbt7714-author-year}
\bibliography{your-bib-file}
```

如需切换为纯数字格式 `[1]`（同时需注释掉 `nsfc.sty` 中的 etoolbox 编号块）：
```latex
\usepackage[numbers,sort&compress]{natbib}
\bibliographystyle{nsfc.bst}
```

### 在线编辑
可通过 [Overleaf](https://www.overleaf.com) 在线编辑和预览。

## ✨ 模板特色

- 📝 **分文件结构**：四部分各自独立文件，大文档管理更清晰
- 🎨 **楷体正文**：STKaiti + AutoFakeBold，`\textbf` 粗体正常显示
- 📐 **精确排版**：13pt 正文，14pt 节标题，2字符缩进，段间距 0.3 倍
- 🔢 **双轨引用**：正文 author-year，文末自动编号列表
- 📊 **丰富命令**：定理/命题/引理/定义，REF 内嵌文献环境，tikz 网络图

## 📜 致谢

本模板原版 Fork 自南开大学程明明教授的 [NSFC-LaTex](https://github.com/MCG-NKU/NSFC-LaTex) 项目。
