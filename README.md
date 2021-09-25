

# latex_intro

typesetting of intro by leo liu with latex

Learn《LaTeX入门》by implementing typesetting of《LaTeX入门》



## Chap. 01



```latex
% 
\NeedsTeXFormat{LaTeX2e}
\ProvidesPackage{thisbookstyle}[2019/10/01]
%
\RequirePackage{calc}
\RequirePackage{manfnt,textcomp}
\RequirePackage{amssymb}
\RequirePackage{graphicx}
```



```latex
% \CTeXpkg: from ctex_faq.sty
\DeclareRobustCommand\CTeXpkg{$\mathbb{C}$\kern-.05em\TeX}
\DeclareRobustCommand\MiKTeX{Mik\TeX}
\DeclareRobustCommand\TeXLive{\TeX{}~Live}
% τεχ
\RequirePackage[artemisia]{textgreek}
\DeclareRobustCommand\greektex{\texttau\textepsilon\textchi}
```



```latex
% font
\setmainfont{Times New Roman}
\setsansfont{Arial}
\setmonofont{Courier}
\newfontfamily\Palatino{Palatino}
```



```latex
% chapter style: from `texdoc ctex`
\newcommand\chapternamebox[1]{%
    \parbox{\ccwd}{\linespread{1}\selectfont\centering #1}}
\ctexset {
    secnumdepth = 3,
    fontset = mac,
    chapter = {
        beforeskip = 0pt,
        fixskip    = true,
        format     = \Huge\bfseries\kaishu\Palatino,
        nameformat = \rule{\linewidth}{1bp}\par\bigskip\hfill\chapternamebox,
        number     = \arabic{chapter},
        aftername  = \par\medskip,
        aftertitle = \par\bigskip\nointerlineskip\rule{\linewidth}{2bp}\par,
        afterskip  = 15pt
    }
}
```



```latex
% 脚注序号带圈文字
\RequirePackage{pifont}
% From: tex.stackexchange
\newcommand*{\circnum}[1]{%
    \expandafter\@circnum\csname c@#1\endcsname
}
\newcommand*{\@circnum}[1]{%
\ifnum#1<1 %
\@ctrerr
\else
\ifnum#1>20 %
\@ctrerr
\else
\ding{\the\numexpr 171+(#1)\relax}%
\fi
\fi
}
% 取消脚注的上标格式
% From: zhihu/muzi
\RequirePackage{xpatch}
% cancel the superscript style of counter used in footnote text
\xpatchcmd\@makefntext
{{\hss\@makefnmark}}
{{\hss\@makefnmark@nosuperscript}\space}
{}{\fail}

\def\@makefnmark@nosuperscript{\lower .1ex \hbox{\normalfont\@thefnmark}}
\renewcommand*{\thefootnote}{\circnum{footnote}}
```



TODO

- Pagestyle: 
  -  different headers on odd/even pages;
  - (**) Chapter number in half-circle on the outer edge;
  - (??) afterskip `\chapter*` different from `chapter`
- References(`cleveref :: pkg`);
- Index;
- Newcounter of exercise;
- Environments:
  - danger/ddanger;
  - Itemize env with finger icon;
  - exercise env with pencil icon;
  - (**) env Source code on left, outcome on right;
  - ...
- Linespacing in ToC
- ...

