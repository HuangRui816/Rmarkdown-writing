---
title: "软件相关操作"
author: "Jin's students"
date: "2019-03-03"
output:
  bookdown::html_document2:
    number_sections: true
    seq_numbering: true
    fig_caption: true
    highlight: haddock
    theme: null
    md_extensions: +east_asian_line_breaks
    keep_md: true
    toc: false
    pandoc_args: ["--filter", "pandoc-crossref", "-M", "eqnPrefix="]
  bookdown::word_document2:
    fig_caption: true
    reference_docx: ./style/word-styles-02.docx
    md_extensions: +east_asian_line_breaks
    pandoc_args: ["--filter", "pandoc-crossref"]
  bookdown::pdf_document2:
    keep_tex: yes
    toc: false
    latex_engine: xelatex
    md_extensions: +east_asian_line_breaks
    pandoc_args: ["--listing", "--filter", "pandoc-crossref"]
css: ./style/markdown.css
autoEqnLabels: true
eqnPrefixTemplate: ($$i$$)
linkReferences: true
bibliography: Bibfile.bib
csl: ./style/chinese-gb7714-2005-numeric.csl
link-citations: true
---

**TODO**

- [ ] 1. 表格出不来
- [ ] 2. Bib文件如何整理
- [ ] 3. 把1、等改成1. ，以变成 markdown list

# 写作准备

每次写之前，以上头文件是不变的，表示设定了具体的环境和规则，只能改变title、author和date。

```
---
title: "软件相关操作"
author: "Jin's students"
date: "2019-03-03"
output:
  bookdown::html_document2:
    number_sections: true
    seq_numbering: true
    fig_caption: true
    highlight: haddock
    theme: null
    md_extensions: +east_asian_line_breaks
    keep_md: true
    toc: false
    pandoc_args: ["--filter", "pandoc-crossref", "-M", "eqnPrefix="]
  bookdown::word_document2:
    fig_caption: true
    reference_docx: ./style/word-styles-02.docx
    md_extensions: +east_asian_line_breaks
    pandoc_args: ["--filter", "pandoc-crossref"]
  bookdown::pdf_document2:
    keep_tex: yes
    toc: false
    latex_engine: xelatex
    md_extensions: +east_asian_line_breaks
    pandoc_args: ["--listing", "--filter", "pandoc-crossref"]
css: ./style/markdown.css
autoEqnLabels: true
eqnPrefixTemplate: ($$i$$)
linkReferences: true
bibliography: Bibfile.bib
csl: ./style/chinese-gb7714-2005-numeric.csl
link-citations: true
---
```

参考文献部分也是不变的：
```
# 参考文献
[//]: # (\bibliography{Bibfile})
```

注：
1、每次写作之前，.Rmd、.yml和style文件及其里面所有的文件都要放在一起，
.yml和style文件夹可以从老的项目中拷过来。
2、参考文献中Bibfile与头文件中的bibliography:Bibfile.bib中的Bibfile对应，
需要自己建立Bibfile.bib文件，与其他所有文件放在一起。

3. 开头固定格式





主要内容包含：设置路径、设置中文显示问题，但加载包放在后面具体实施部分，不需要放在此处

# 文本注意事项

1. **摘要**表示“摘要”加粗, *李研* 表示“李研”斜体
2. \# 实证分析表示一级标题，且#和引言之间有一个空格, \#\# 数据准备 表示二级标题, \#\#\# 数据及数据
来源 表示三级标题,······, \#\#\#\#\#\# 最多六个#，表示最小的字体
3. 一对美元符号 \$x\$ 表示行内公式，左右各空一格,  \$\$x+y\$\$ 两对美元符号表示行间公式，可以往后空
一格再进行写作
 
# 代码注意事项
 
1. \`r `表示行内计算，直接输入计算公式即可出结果
2.

~~~~
\```{r eval=T,echo=F,error=T,warning=F,message=FALSE,comment="",results='asis'}

\```
~~~~

上述表示写R代码，error=T表示可以存在错误，warning=F表示不要警告信息，message=F表示不要警告信
息，comment=”“表示不出现警告信息


3. `dev=c('png', 'CairoPDF')` #执行pdf时输出图片，图片名可以是中文，不会报错，但只能用于pdf，
在最开的` ```{r }```` `中加，下面代码中的画图参数要写`family="SimSun"`，表示字体为宋体，执行结
果是文字，高清图`dev=c('png')`#执行任何文件都可以加上，但是只能输出图片，不是文字，会模糊

4. 引用参考文献一共加四句话： 
```
csl: chinese-gb7714-2005-numeric.csl #文件（固定格式）
bibliography: baidu.bib #文件（baidu.bib可以改，改成自己参考的文献）自己构建的，是文本文件
# 参考文献
[//]: # (\bibliography{new}) #放在结尾，表示参考文献，new可根据自己的名称修改
```
文章中的上标[1]用[@ ] #空格用notepad++打开.bib文件中的文章复制粘贴, .bib文件自己在百度学术中
搜索，导出为.bib文件

5. `data.frame(a1,a2,a3)`#支持不同类型数据，数值部分不会转化成文本，仍然是数值，可以控制小数
点位数;	`cbind(a1,a2,a3)`#支持同类型的数据，cbind执行的结果如果在有文字的前提下都会转化文本

6. 只提取代码： 


7. `kable` 用来制作表格，可以在里面给表格增加名称等（需要加载knitr包）

8. 行间公式编号例子

$$y=ax+b$$ {#eq:model1}

在[@eq:model1] 中，引用上述格式即可自动编号。

9. 图表编号例子



在表\@ref(tab:tab1)中，即可在输出的文档中显示表的序号。此处\@ref(tab: )是固定的，
tab1根据自己上面程序中```{r tab1}中r后的tab1确定名称

图编号与之类似，也为\@ref(fig:fig1)。本文档输出显示不出具体编号，是因为没有图表输入

# 编码注意事项

1. 行间公式后空一行，行内公式、代码前后各空一格（行）
2.	worktools文件包含内容：everything notepad++ rstudio telive PathEditor 两个环境变量
3. 程序、路径、文件名少用中文，要用UTF-8编码
4. 尽量将程序的路径单独用一个变量表示出来，放在最前面
5. 不要轻易尝试直接在rstutio中复制，先复制到notepad++（**只支持文本**）再复制
6. 文件备份：default .tex
7. 三个软件链接：
	1. https://elearningindustry.com/12-best-free-online-bibliography-and-citation-tools
	2. http://www.jabref.org/
	3. http://download1.rstudio.org/RStudio-0.99.903.zip



# GitHub相关操作

## 注册

网页操作https://github.com

## Github程序

## GitHub嵌入Rstudio中需要做的工作

安装GitHub，在Rstudio中菜单栏点击Tools→Global Options，在弹出的对话框左边一栏点击Git/SVN，在Git executable中
输入git.exe所在路径，点击ok

按下快捷键win+R，在弹出的窗口中输入CMD，之后在弹出的窗口中输入：
git config --global user.email "380906952@qq.com"
git config --global user.name "Zeng Yuanzheng"
（注：引号里改为自己的邮箱和名字，名字用汉语拼音写）

## 把本地文件夹用git控制并push到Github的步骤

1、使用Github网页操作：网页中建立项目。把需要版本控制的文件上传到项目中，然后再把项目clone到文件夹中。

2、使用git命令操作，可以在Terminal运行git命令。

## 合作者步骤

1、repository owner向合作者发出邀请（repository setting）

2、被邀请者在网页（https://github.com/username/reponame/invitations) 接受邀请，成为合作者
（注：uername为帐户名，reponame为项目名）

3、合作者clone owner的repository到本地repository，具体操作为：

在Rstudio中，点击file→new project→version control→git，在弹出的对话框中，Repository URL输入项目链接，
Project directory name输入项目名字（一般写入项目链接后会自动生成），Create project as subdirectory of
中输入自己电脑上要把项目保存的位置，点击Create Project，项目创建完毕。之后会在Rstudio右下角
显示出项目里的所有内容。

4、打开项目中的.Rmd，对文件中的内容进行修改（Modified），修改完之后点击保存（Save），在git图标下
点击commit，在弹出的窗口中，左上角勾选刚刚修改的Rmd文件，右上角登记修改的内容（比如，在Rmd中修改
了图片，写入modify figures即可），点击commit，之后push

5、重新开始工作时，在git图标中点击pull，到最新版本

6、如果push的时候，remote已经修改，两个修改不一致则会产生冲突，这时需要重新pull并手工解决冲突后
再按照push步骤提交（此时，pull的最新版本会出现“<<<<<< ====== >>>>>>”这三个符号标记的内容，
解决冲突可以同时保留其他内容，此时只需将这三个符号及其后面紧跟的内容删掉即可）

注：
1、在编写Rmd时，要使用相对路径，不能使用绝对路径，因为绝对路径只有在自己电脑上才可以运行，
相对路径大家都可以运行。
2、在编写markdown时，需要手动换行，大概80个字符或40个汉字左右的时候可以换一行，编辑窗口
左下角可以看到字符数，碰到标点符号或者行内公式，保持在一行。
3、每次提交之前切忌把全部内容剪切复制，否则无法知晓真正改动内容。

# Equalx的设置和用法

下载Equalx，打开equalx.exe，菜单栏点击edit→prefrences→Advanced，点击pdflatex后的change，
找到pdflatex.exe所在的路径（基本为：./texlive/2014/bin/win32/pdflatex.exe，.表示texlive所在的路径，
注：装Equalx之前需要下载texlive），之后点击ghostscript后的change，找到gswin32c.exe所在
的路径（注：修改之前需要下载gs）,如图\@ref(fig:fig1) 所示。

<div class="figure">
<img src=".\results\Equalx安装.png" alt="Equalx安装"  />
<p class="caption">(\#fig:fig1)Equalx安装</p>
</div>

edit→prefrences→editor，family选择Consolas，size选择14，字体可以调大一点

edit→prefrences→Preview，Automatic after □ milliseconds，□中输入5000

在编辑框中输入\alpha+\hat{\beta}就会显示出公式，此软件的意义在于，当输入\a时，
就会出现\alpha等以\a开头的字母，选中自己所需要的直接enter即可，会自动补全，
避免记不住markdown中公式一直看文档。还可以通过点击上面的符号直接输入。对于比较复杂的公式，
可以先在这里面输入，然后把latex代码复制到rmd中。

# Mathtype的设置和用法

1、首先下载mathtype，将其嵌套到word中去，操作成功之后word菜单栏会出现mathtype；
2、点击mathtype中的convert equations,设置相关属性，勾选Equation Type to convert模块的前两
项和第四项，Range模块的“whole document”,在Convert equation to模块下的“Text using MathType translator”
选择“LaTex 2.09 and lator”，如图 \@ref(fig:fig2) 所示，设置完成以后点击convert就能将word
文档中的公式转化为LaTex公式。

<div class="figure">
<img src=".\results\Mathtype安装.png" alt="Mathtype安装"  />
<p class="caption">(\#fig:fig2)Mathtype安装</p>
</div>

# 参考文献
[//]: # (\bibliography{Bibfile})