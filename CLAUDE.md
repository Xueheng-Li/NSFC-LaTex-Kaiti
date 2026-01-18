## 📚 项目概述

NSFC（国家自然科学基金）申请书 LaTeX 模板，支持面上项目和青年项目（C类）。

## 🔧 编译命令

```bash
# 完整编译（带参考文献）
xelatex 面上.tex && bibtex 面上 && xelatex 面上.tex && xelatex 面上.tex
```

## 📖 引用格式

当前使用 Author-Year 格式 (Author, Year)：
```latex
\usepackage[authoryear,round]{natbib}
\bibliographystyle{gbt7714-author-year}
```

如需切换为数字格式 [1], [2]：
```latex
\usepackage[numbers,sort&compress]{natbib}
\bibliographystyle{nsfc.bst}
```

切换格式时需清除 `.aux`, `.bbl`, `.blg` 等辅助文件后重新完整编译。

## 语言要求

- 注意不要列点，要写成层次分明、中心突出的多个论述性段落
- 通常每段的首句为承上启下或总结性的句子
- 避免翻译腔
- 不要有 AI 味表达
- 写自然流畅的地道文书中文
- 使用标准中文标点符号: 。，？！：；（）……——
- 如非必要，勿用引号
