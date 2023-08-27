---
title: C0. LaTeX Basics
date: '2023-03-02'
type: book
weight: 5
---
<!--more-->
{{< icon name="clock" pack="fas" >}} 30 min

## C0.1. Texlive

- Download [Texlive](https://tug.org/texlive/windows.html) overnight and install.
    - We will use a small tool "latexmk" that comes with texlive. Last time I check latexmk is written in Perl.
    - `latexmk.exe` is located here: `D:\Programs\texlive\2021\bin\win32\latexmk.exe`. I often add this directory to my path variable and I can execute latexmk.exe in cmd.exe
    - To use latexmk to do the dirty job for ya, execute following commands in the diretory where your .tex file locates:
        - `latexmk -quiet -pdf -synctex=1 -pvc -view=none main.tex`
    - If your .tex file contains Chinese characters, use this instead:
        - `latexmk -quiet --xelatex -synctex=1 -pvc -view=none main.tex`

## C0.2. SumatraPDF

- Download [SumatraPDF](https://www.sumatrapdfreader.org/download-free-pdf-viewer) and install.
- I recommend to use [SumatraPDF 2](https://www.sumatrapdfreader.org//dl//rel/2.5.2/SumatraPDF-2.5.2-install.exe).

## C0.3. WinEdt

I am aware that there are a lot of options for LaTeX editor,
and I am also aware VS code is one of them.
However, I would still suggest you trying out [WinEdt](https://www.winedt.com/download.html). It seems since WinEdt 11 it is no longer free, so download WinEdt 10.

- You can make it work with SumatraPDF.
    - See [my tips for using WinEdt](https://github.com/horychen/snippets#winedt-103-and-sumatrapdf). 

{{< callout note >}}
My tips are valid for WinEdt 10 and are not tested for WinEdt 11.
{{< /callout >}}

## C0.4. Overleaf

[Overleaf](https://www.overleaf.com/) provides you web browser based editor and compiler experience.
If you are IEEE member, you can use the full capability of overleaf including collaborate with multiple authors and git service.

YOU CAN LEARN LaTeX by going through [the documentation of Overleaf](https://www.overleaf.com/learn),
or of course there is a ["Learn LaTeX in one video" video by Derek Banas](https://www.youtube.com/watch?v=VhmkLrOjLsw).

{{< youtube VhmkLrOjLsw >}}



