---
title: 源稿の標準
author: 陳奕達
date: '2021-09-09'
slug: source-text-note
categories:
  - themes
  - syntax
tags:
  - themes
  - css
  - markdown
  - shortcodes
  - html
  - emoji
  - text
  - tag with whitespaces
description: 所有貼文技術的東東都在這裡。
image: Unknown.jpg
math: ~
license: ~
hidden: no
comments: yes
---

本站是透過R[^1]的Blogdown[^2]套件所搭建的靜態網誌，站內所有文章皆以純文本（plain text）編寫，通過Pandoc[^3]轉換文件中的標記語言後，再以Hugo[^4]模板渲染為網頁文章。本文首先將說明此架構下，純文本的標記規則，以及其轉換之後的效果。並在最後提供文章格式建議，包括文章結構、層級安排及引用格式等相關說明。本文僅供編輯人員參考，受邀作者可依書寫習慣提交純文本、富文本（rich text）或所見即所得文件（WYSIWYG），唯需注意第二部分格式說明當中的建議。

[^1]: R是一套運用於統計的開發環境，具有非常活潑的開發生態。透過開發者的集體努力，R有著相當豐富的套件，使得研究者除了處理統計資料外，也可以直接將研究成果渲染成各種類型的研究報告。詳見[*The R Project for Statistical Computing*](https://www.r-project.org)*。*

[^2]: 由謝益輝所開發的R套件，詳見[*Blogdown*](https://pkgs.rstudio.com/blogdown/)。

[^3]: Pandoc是一個開源的文本轉換工具，Blogdown的文件標記轉換依賴其功能。詳見[Pandoc.org](https://pandoc.org)

[^4]: Blogdown所依賴的靜態網頁架構，詳見[The world's fastest framework for building websites \| Hugo](https://gohugo.io)。

## 標記語言

Markdown[^5]直覺的標記方式，除了免去如Word檔等所見即所得文件（WYSIWYG）的各種格式錯誤，省下書寫時所浪費的格式調整時間，也讓使用者的書寫得以從Google或Microsoft等企業所提供的封閉式辦公文件當中解放，輕鬆進行轉換與渲染，銜接各種工作流程。本站使用的R套件Blogdown即是一個以Markdown為基礎的靜態網頁環境，使用者可以直接將具有Markdown標記的平面文件轉換為網頁貼文。

[^5]: 由John Gruber所開發的輕量標記語言，因未訂定標準，目前已出現許多衍生版本。Blogdown所使用的版本為Pandoc Markdown，此版本也運用在RMarkdown及Bookdown等R套件中。本文僅列出本站需使用的標記方式，完整詳細的標記規則請見Rmarkdown中的說明[Pandoc Markdown](https://garrettgman.github.io/rmarkdown/authoring_pandoc_markdown.html)。

Blogdown套件除了提供簡潔的Markdown語法支持外，也提供了各種多媒體與格式支援。除了支援KaTex[^6]數學公式，Hugo也提供Shortcode[^7]語法，讓使用者可以插入YouTube影片及Instagram貼文等。另外，如果你是運用R語言的數據科學家的話，Blogdown套件也直接支持了R code的執行，讓研究者得以直接在網頁上發表可再製研究的內容與圖表，甚至可以運用BibTex[^8]管理所引用的參考文獻。

[^6]: KaTex是Tex文本排版系統的數學公式支援，Tex由Donald Ervin Knuth開發用於學術寫作，KaTex在目前某些開發較完整的Markdown編輯器中作為數學公式的補充標記語言。

[^7]: Shortcode是Hugo用以補充Markdown無法在渲染後的頁面顯示多媒體的語法延伸方案。

[^8]: BibTex是與Tex作為引用文獻資料的標記文本格式，也是目前許多Markdown編輯器處理引用文獻的主流格式，詳見[BibTex.org](http://www.bibtex.org)。

本節將依先來後到分為通用的Markdown標記語法與Blogdown（含Hugo）的特殊語法功能等兩部分，簡單介紹以上所提的標記法與顯示效果。若需要更詳細的資訊，建議參考Blogdown開發者謝益輝所著的專書[*《blogdown: Creating Websites with R Markdown》*](https://bookdown.org/yihui/blogdown/)。

### Markdown

Markdown是一種簡潔的標記語言，是目前主流的純文本標記語法，許多編輯器、筆記軟體及生產力工具現在都已經支援Markdown標記。在此除了說明一些寫作會運用到的基礎語法外，也會推薦一些開源的Markdown編輯器，提供尚未有慣用編輯器的朋友們參考。

除了編輯文本之外，如何用Pandoc渲染Markdown標記文本為其他類型的文件也是一門學問，尤其是含有中日韓（CJK）字元及LaTex標記的文本，在沒有設定好的狀況下，轉換為PDF時容易有缺字或渲染失敗的問題。不幸的是使用Pandoc僅僅是Markdown工作流程的基礎功而已，要建立流暢的工作流程，就必須熟悉各種文檔間的轉換及渲染的設定方式。

或許一開始在學的時候會因為超級折騰，而放棄純文本回去用WYSIWYG。一方面，這只能取決於每個人在內容生產上不被綁架的信念有多深；另一方面，其實這種折騰只是在一種末日預期下------沒有軟體支援、甚至是電力支援------建立進可攻退可守的多元媒介工作流程的前哨戰而已。本文僅在這裡給一劑進入Markdown世界前的預防針，畢竟被卡車撞這種事情也不是每個人都會發生。最後，請善用[Duckduckgo](https://duckduckgo.com/)或[Startpage](https://www.startpage.com)等搜尋引擎（不推薦賣個資又養套殺使用者的Google）或各編輯器所提供的說明文件來學習，本文不再贅述。

#### 編輯器

網路上已有不少對Markdown編輯器的推薦，許多筆記軟體如[Notion](https://www.notion.so/)、[Evernote](https://evernote.com)、[Roam Research](https://roamresearch.com)及[Obsidian](https://obsidian.md)等，都是以Markdown為基礎進行文本的標記與渲染。如果你已經用習慣了以上的軟體，可直接跳過本小節，但如果你是Markdown新手，或是想要開始嘗試開源軟體的話，可以試著瞭解以下所推薦的編輯器。

-   [**Atom**](https://atom.io)：GitHub開發的開源程式編輯器，在GitHub的生態系中有相當豐富的外掛。推薦給對Python等程式語言有興趣，或預計會開始學習程式語言的人。

-   [**RStudio**](https://www.rstudio.com)：功能強大的R語言整合開發環境（Integrated Development Environment, IDE），建議還在跑SPSS[^9]的朋友們趕快棄坑，轉投R語言的陣營。RStudio的生態系除了擁有各種強大的統計功能套件外，圍繞著Rmarkdown[^10]套件的書寫生態也相當豐富（並有支援Zotero[^11]），整合了資料蒐集、運算研究與書寫產出等流程，適合社會科學或數據科學研究者。

-   [**Zettlr**](https://www.zettlr.com)：與Roam Research和Obsidian一樣，主要的功能是卡片盒（Zettelkasten）筆記法[^12]，支援wiki式的網絡化筆記語法。差別在於Zettlr是開源軟體，並且對Zotero有直接支援，適合不需要用到統計，且對卡片盒有學習耐心的學術研究者。

-   [**Mark Text**](https://marktext.app)：以上三種開源軟體的Markdown功能，都只能算是支援主要功能的書寫整合，而且有著較高的學習成本。如果只需要純粹地編輯Markdown文件，我會推薦這個功能強大的開源編輯器。就算有安裝以上三種軟體，我也會推薦它作為備用或不需用到其主要功能時的主力編輯器。

-   [**Byword**](https://bywordapp.com)：非開源，售價為新台幣190元，推薦這個軟體的原因是iOS上缺乏夠好的開源編輯器，但許多人還是會有行動裝置的工作需求（Android應該會有比較多不錯用的Markdown開源編輯器，但我沒涉略）。Byword最主要是因應Apple生態系的工作需求，它除了可以用iCloud空間作為資料床外，也可與多種雲端空間同步，編輯功能也非常完整，推薦愛吃蘋果的阿迪仔與阿咩仔使用。我個人則是使用另一款同樣支援iCloud空間作為資料床的[Pretext](https://apps.apple.com/app/pretext/id1347707000)（非開源、基本功能免費），推薦給跟我一樣覺得能用就好的人。

[^9]: SPSS全稱為Statistical Package for the Social Sciences，是IBM所推出的又弱又貴的統計軟體，詳見[SPSS](http://www.ibm.com/analytics/us/en/technology/spss/)。

[^10]: Rmarkdown是RStudio基於整合研究與書寫流程，以Markdown為基礎，所推出的套件功能，詳見[Rmarkdown](https://rmarkdown.rstudio.com)。

[^11]: Zotero是一個開源的文獻管理軟體專案，擁有許多實用的外掛。目前的Beta版帶有強大的筆記功能，並預計於不久後推出iOS版本，詳見[Zotero](https://www.zotero.org)。

[^12]: 卡片盒（Zettelkasten）是提出社會系統理論的德國學者Niklas Luhemann生前使用的筆記法，最近諸多紅到發紫的筆記軟體都是以其網絡化的概念來設計。但其實此種筆記法需要有非常嚴謹的層級規範，並非許多中文教學文章所述，不斷紀錄和連結就可以變得跟他大佬一樣聰明伶俐。是一種門檻極高的筆記方式，不推薦各位朋友使用。

#### 標題

#### 段落

#### 粗體

#### 斜體

#### 註腳

#### 引文

#### 表格

#### 程式碼

#### 列表

#### 連結

#### 圖片

#### 跳脫字元

### Blogdown

#### Mathematical

#### Shortcode

##### Youtube

##### Vimeo

##### Instagram

##### Tweet

#### R code

#### Bibliography

## 格式說明

### 文章結構

### 層級安排

### 引用格式
