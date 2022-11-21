# 西南石油大学硕士学位论文 LaTeX 模板

本项目基于 [qingbyin](https://github.com/qingbyin) 在博士期间制作的学位论文模板 [swputhesis](https://github.com/qingbyin/swputhesis)。在此表示感谢。

## 效果预览
见 [swputhesis.pdf](https://github.com/sudrizzz/swputhesis/blob/main/swputhesis.pdf)。

## 前置条件

### 安装 TeXLive
请前往镜像站下载最新版 TeXLive，安装时可通过 customize 操作去除不需要的语言包（如韩语、德语等），以加快安装速度。

下载地址：[北京外国语大学镜像站](https://mirrors.bfsu.edu.cn/CTAN/systems/texlive/Images/)、[清华大学镜像站](https://mirrors.tuna.tsinghua.edu.cn/CTAN/systems/texlive/Images/)

## 使用方法
### 在 VSCode 中编译

**下述编译方式都已配置好，无需再次配置，直接使用即可。相关配置见项目路径下 `.vscode/settings.json`。**  

首先需要安装 [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop) 插件。打开 swputhesis.tex 时，左侧导航栏会出现 TeX 菜单。

- 使用 `latexmk` 编译  
点击 TeX 菜单，选择 COMMANDS -> Build LaTeX Project -> **Recipe: latexmk** 即可编译。

- 使用 `xelatex` 编译  
点击 TeX 菜单，选择 COMMANDS -> Build LaTeX Project -> **Recipe: xelatex -> biber -> xelatex\*2** 即可编译。

### 手动编译（较硬核，不推荐）

- 使用 `latexmk` 编译  
执行如下命令即可编译。  
```shell
latexmk -synctex=1 -interaction=nonstopmode -file-line-error -xelatex swputhesis.tex
```

- 使用 `xelatex` 编译  
如果使用 `xelatex` 编译项目，那么需要按照 `xelatex -> biber -> xelatex -> xelatex` 的顺序依次调用 `xelatex` 与 `biber` 命令行工具，命令如下。
```shell
# 第一步 xelatex
xelatex -no-pdf --interaction=nonstopmode swputhesis.tex
# 第二步 biber
biber swputhesis
# 第三步 xelatex
xelatex -no-pdf --interaction=nonstopmode swputhesis.tex
# 第四步 xelatex
xelatex --interaction=nonstopmode swputhesis.tex
```

编译完成后会在项目根目录中生成 swputhesis.pdf。

## 参考文献管理
为了方便配置中文参考文献和国标要求，使用 biblatex + `biber` 而不是默认的 BibTeX。

## 已知问题
目前项目仍处于早期开发版本，欢迎提交 issue 和 pull request。
1. 由于学术硕士和专业硕士封面存在较大差异，建议使用 Word 单独制作封面；
2. 由于 Windows 附带的中易宋体（即宋体）与中易黑体（即黑体）仅有一个字重，因此在加粗时会使用假粗体（AutoFakeBold），会产生笔画粘连问题。已知的解决办法是安装带有多种字重的字体，如[思源宋体](https://mirrors.bfsu.edu.cn/adobe-fonts/source-han-serif/SubsetOTF/CN/)与[思源黑体](https://mirrors.bfsu.edu.cn/adobe-fonts/source-han-sans/SubsetOTF/CN/)，并在 swputhesis.cls 样式文件中将 `SimSun` 与 `SimHei` 替换为 `Source Han Serif CN` 与 `Source Han Sans CN`；

## 免责申明
由于学校图书馆网站上说明只接受 Word 格式的学位论文文档（见[学位论文提交系统常见问题](https://lib.swpu.edu.cn/95_80/mason/0317x/faq.html?q=13#a)），本模板不能保证在提交学校审查时能一切顺利，请提前咨询相关负责老师。

## 参考资料

1. [一份不太简短的 LaTeX2ε 介绍](https://mirrors.bfsu.edu.cn/CTAN/info/lshort/chinese/lshort-zh-cn.pdf)
2. [北京理工大学非官方本科生毕业设计、毕业论文的 LaTeX 模板文档指南](https://bithesis.spencerwoo.com/Guide/2-Usage/Downloading-and-using-templates.html)
3. [在 LaTeX 中使用 OpenType 字体（二）](https://stone-zeng.github.io/2019-07-06-use-opentype-fonts-ii/)
