---
title: 源稿の技術文件
author: 陳奕達
date: '2021-09-09'
slug: source-text-note
categories:
  - themes
  - syntax
tags:
  - themes
  - markdown
  - shortcodes
  - html
  - text
description: 所有貼文技術的東東都在這裡。
image: Unknown.jpg
math: ~
license: ~
hidden: no
comments: yes
---

本站是透過R[^1]的Blogdown[^2]套件所搭建的靜態網誌，站內所有文章皆以純文本（plain text）編寫，通過Pandoc[^3]轉換文件中的標記語言後，再以Hugo[^4]模板渲染為網頁文章。本文首先將說明此架構下，純文本的標記規則，以及其轉換之後的效果。並在最後提供文章格式建議，包括文章結構、層級安排及引用格式等相關說明。

[^1]: R是一套運用於統計的開發環境，具有非常活潑的開發生態。透過開發者的集體努力，R有著相當豐富的套件，使得研究者除了處理統計資料外，也可以直接將研究成果渲染成各種類型的研究報告。詳見[*The R Project for Statistical Computing*](https://www.r-project.org)*。*

[^2]: 由謝益輝所開發的R套件，詳見[*Blogdown*](https://pkgs.rstudio.com/blogdown/)。

[^3]: Pandoc是一個開源的文本轉換工具，Blogdown的文件標記轉換依賴其功能。詳見[Pandoc.org](https://pandoc.org)

[^4]: Blogdown所依賴的靜態網頁架構，詳見[The world's fastest framework for building websites \| Hugo](https://gohugo.io)。

本文僅供對Markdown完全沒有概念的朋友參考，有Markdown使用經驗的朋友可以略過第一部分的說明，唯需注意第二部分格式說明當中的建議。另外，本站並不強迫受邀作者繳交Markdown文件，作者可依書寫習慣提交純文本、富文本（rich text）或所見即所得文件（WYSIWYG），但也請稍加注意書寫的格式說明，本站會在收到稿件後交由編輯處理。

## 第一部分｜標記語言

Markdown[^5]直覺的標記方式，除了免去如Word檔等所見即所得文件（WYSIWYG）的各種格式錯誤，省下書寫時所浪費的格式調整時間，也讓使用者的書寫得以從Google或Microsoft等企業所提供的封閉式辦公文件當中解放，輕鬆進行轉換與渲染，銜接各種工作流程。本站使用的R套件Blogdown即是一個以Markdown為基礎的靜態網頁環境，使用者可以直接將具有Markdown標記的平面文件轉換為網頁貼文。

[^5]: 由John Gruber所開發的輕量標記語言，因未訂定標準，目前已出現許多衍生版本。Blogdown所使用的版本為Pandoc Markdown，此版本也運用在RMarkdown及Bookdown等R套件中。本文僅列出本站需使用的標記方式，完整詳細的標記規則請見Rmarkdown中的說明[Pandoc Markdown](https://garrettgman.github.io/rmarkdown/authoring_pandoc_markdown.html)。

Blogdown套件除了提供簡潔的Markdown語法支持外，也提供了各種多媒體與格式支援。除了支援KaTex[^6]數學公式，Hugo也提供Shortcode[^7]語法，讓使用者可以插入YouTube影片及Instagram貼文等。另外，如果你是運用R語言的數據科學家的話，Blogdown套件也直接支持了R code的執行，讓研究者得以直接在網頁上發表可再製研究的內容與圖表，甚至可以運用BibTex[^8]管理所引用的參考文獻。

[^6]: KaTex是一種支援LaTex與網頁顯示的數學公式支援，KaTex在目前某些開發較完整的Markdown編輯器中作為數學公式的補充標記語言。

[^7]: Shortcode是Hugo用以補充Markdown無法在渲染後的頁面顯示多媒體的語法延伸方案。

[^8]: BibTex是一種與LaTex配合，作為引用文獻資料的標記文本格式，也是目前許多Markdown編輯器處理引用文獻的主流格式，詳見[BibTex.org](http://www.bibtex.org)。

本節將依先來後到分為通用的Markdown標記語法與Blogdown（含Hugo）的特殊語法功能等兩部分，簡單介紹以上所提的標記法與顯示效果。若需要更詳細的資訊，建議參考Blogdown開發者謝益輝所著的專書[*《blogdown: Creating Websites with R Markdown》*](https://bookdown.org/yihui/blogdown/)。

### Markdown

Markdown是一種簡潔的標記語言，是目前主流的純文本標記語法，許多編輯器、筆記軟體及生產力工具現在都已經支援Markdown標記。在此除了說明一些寫作會運用到的基礎語法外，也會推薦一些開源的Markdown編輯器，提供尚未有慣用編輯器的朋友們參考。

除了編輯文本之外，如何用Pandoc渲染Markdown標記文本為其他類型的文件也是一門學問，尤其是含有中日韓（CJK）字元及LaTex標記的文本，在沒有設定好的狀況下，轉換為PDF時容易有缺字或渲染失敗的問題。不幸的是使用Pandoc僅僅是Markdown工作流程的基礎功而已，要建立流暢的工作流程，就必須熟悉各種文檔間的轉換及渲染的設定方式。

或許一開始在學的時候會因為超級折騰，而放棄純文本回去用WYSIWYG。一方面，這只能取決於每個人在內容生產上不被綁架的信念有多深；另一方面，其實這種折騰只是在一種末日預期下------沒有軟體支援、甚至是電力支援------建立進可攻退可守的多元媒介工作流程的前哨戰而已。本文僅在這裡給一劑進入Markdown世界前的預防針，畢竟被卡車撞這種事情也不是每個人都會發生。最後，請善用[Duckduckgo](https://duckduckgo.com/)或[Startpage](https://www.startpage.com)等搜尋引擎（不推薦賣個資又養套殺使用者的Google）或各編輯器所提供的說明文件來學習，本文不再贅述。

#### 開源編輯器推薦

網路上已有不少對Markdown編輯器的推薦，許多筆記軟體如[Notion](https://www.notion.so/)、[Evernote](https://evernote.com)、[Roam Research](https://roamresearch.com)及[Obsidian](https://obsidian.md)等，都是以Markdown為基礎進行文本的標記與渲染。如果你已經用習慣了以上的軟體，可直接跳過本小節，但如果你是Markdown新手，或是想要開始嘗試開源軟體的話，可以試著瞭解以下所推薦的編輯器。

-   [**Atom**](https://atom.io)：GitHub開發的開源程式編輯器，在GitHub的生態系中有相當豐富的外掛。推薦給對Python等程式語言有興趣，或預計會開始學習程式語言的人。

-   [**RStudio**](https://www.rstudio.com)：功能強大的R語言整合開發環境（Integrated Development Environment, IDE），建議還在跑SPSS[^9]的朋友們趕快棄坑，轉投R語言的陣營。RStudio的生態系除了擁有各種強大的統計功能套件外，圍繞著Rmarkdown[^10]套件的書寫生態也相當豐富（並有支援Zotero[^11]），整合了資料蒐集、運算研究與書寫產出等流程，適合社會科學或數據科學研究者。

-   [**Zettlr**](https://www.zettlr.com)：與Roam Research和Obsidian一樣，主要的功能是卡片盒（Zettelkasten）筆記法[^12]，支援wiki式的網絡化筆記語法。差別在於Zettlr是開源軟體，並且對Zotero有直接支援，適合不需要用到統計，且對卡片盒有學習耐心的學術研究者。

-   [**Mark Text**](https://marktext.app)：以上三種開源軟體的Markdown功能，都只能算是支援主要功能的書寫整合，而且有著較高的學習成本。如果只需要純粹地編輯Markdown文件，我會推薦這個功能強大的開源編輯器。就算有安裝以上三種軟體，我也會推薦它作為備用或不需用到其主要功能時的主力編輯器。

-   [**Byword**](https://bywordapp.com)：非開源，售價為新台幣190元，推薦這個軟體的原因是iOS上缺乏夠好的開源編輯器（Android應該會有比較多不錯用的開源編輯器，但我沒涉略）。它因應了Apple生態系的工作需求，除了可以存取iCloud檔案夾（這很重要！很多app都是做軟體內的封閉式同步），編輯功能也非常完整，推薦愛吃蘋果的阿迪仔與阿咩仔使用。我個人則是使用另一款同樣可以存取iCloud檔案夾的[Pretext](https://apps.apple.com/app/pretext/id1347707000)（非開源、基本功能免費），推薦給覺得能用就好的人。

[^9]: SPSS全稱為Statistical Package for the Social Sciences，是IBM所推出的又弱又貴的統計軟體，詳見[SPSS](http://www.ibm.com/analytics/us/en/technology/spss/)。

[^10]: Rmarkdown是RStudio以Markdown為基礎，用以整合研究與書寫流程的功能套件，詳見[Rmarkdown](https://rmarkdown.rstudio.com)。

[^11]: Zotero是一個開源的文獻管理軟體專案，擁有許多實用的外掛。目前的Beta版帶有強大的筆記功能，預計於不久後也會推出iOS版本，詳見[Zotero](https://www.zotero.org)。

[^12]: 卡片盒（Zettelkasten）是提出社會系統理論、致力於社會風險管理的德國學者Niklas Luhemann，生前使用的筆記法。最近有許多紅到發紫的筆記軟體都是以這種網絡化筆記的概念來設計。但其實此種筆記法需要有非常嚴謹的層級規範配合，才能有效控制雜訊，並非許多中文教學文章所述，不斷紀錄和連結就可以變得跟他大佬一樣聰明俐落。是一種門檻極高的筆記方式，不推薦各位朋友使用。

#### 語法說明與顯示效果

Markdown並非艱深困難的語法，它僅僅是區塊與區段的標記語言，學習時間與記憶成本非常低，直接使用是習慣它的最快方法。以下推薦先閱讀Markdown的基本語法規則，並配合本站的Hugo模板所提供的範例，參考顯示效果（基於Blogdown的轉換，Other Elements的Hugo標記元素是失效的）。

-   [Markdown語法說明](https://markdown.tw)

-   [Markdown Syntax Guide](https://hazukagi.sintaika.com/p/markdown-syntax-guide/)（顯示效果）

-   [Markdown Syntax Guide](https://github.com/aciddylan/hazukagiWeb/blame/master/content/post/markdown-syntax/index.md)（Markdown）

### Blogdown

如上一小節所示，Markdown的基本標記語法僅能提供平面書寫的需求，而網頁貼文其實還包含了插入YouTube影片或社群網站內容等多媒體需求。在傳統的Markdown書寫當中，會直接以HTML語言來補充，但既然我們都使用Blogdown套件了，那這些功能當然也是要以更簡潔的語法方案來取代嘍。

雖然說本站所使用的語法集是由R套件Blogdown所提供，但其實除了Shortcode及R code之外，大部分允許使用Pandoc轉換的編輯器都有提供對KaTex及BibTex的支援。所以，如果你使用的編輯器並非RStudio也不必太過擔心。

#### YAML

在開始介紹Blogdown可以運用的語法前，必須先介紹一個叫做YAML[^13]的東東。這個YAML是儲存文件元數據（metadata）的區塊，一般會置於文件開頭，用以描述檔案性質或是用於寫入特定程式功能執行的指示，資訊內容可以包含標題、簡述、日期時間、語言類型、標籤、⋯⋯等對應到HTML語言的基本資訊；另外也有配合編輯器或Pandoc的特殊格式，例如：書目資訊、渲染格式、程式碼模式、⋯⋯等功能。本站在Blogdown架構下的YAML以本篇為例：

[^13]: YAML是一種序列化的格式語言，常見於網站構建及資料庫的描述等用途上，也是目前Markdown文本儲存元數據的主要格式，參見[yaml.org](https://yaml.org)。

``` yaml
title: 源稿の技術文件
author: 陳奕達
date: '2021-09-09'
slug: source-text-note
categories:
  - themes
  - syntax
tags:
  - themes
  - markdown
  - shortcodes
  - html
  - text
description: 所有貼文技術的東東都在這裡。
image: Unknown.jpg
math: ~
license: ~
hidden: no
comments: yes
```

文章所儲存的元數據包含了`title`、`author`、`date`、`categories`、`tags`和`description`等較直覺的資訊，本文不另外說明，其他項目則說明如下：

-   `slug`：指定文件生成的永久檔名。

-   `image`：指定文件的封面圖片，本文的圖片檔名為`Unknown.jpg`，置於文件同一目錄下。

-   `math`：指定是否以KaTex顯示數學公式，`~`代表預設值開啟。

-   `license`：指定文件的授權方式，預設值為 CC-by-nc-sa 4.0。

-   `hidden`：指定文章是否隱藏。

-   `comments`：指定是否開放用戶評論文章的外掛模組，本站使用的模組為[Disqus](https://disqus.com)提供。

#### Shortcode

Shortcode是由Hugo靜態網頁架構提供，藉此補充Markdown標記語法對HTML支援的不足之處。因此，Hugo的Shortcode其實是一組對應到所有HTML的語法支援，而大部分的基礎書寫語法、插入圖片及超連結語法等已有Markdown語法的支持，此小節僅需理解YouTube及Vimo等多媒體影片的插入，以及對Tweet或Instagram等社群貼文的顯示語法，官方說明文件及本站模板示例如下。

-   [Shortcodes \| Hugo](https://gohugo.io/content-management/shortcodes/)

-   [Rich Content](https://hazukagi.sintaika.com/p/rich-content/)（顯示效果）

-   [Rich Content](https://github.com/aciddylan/hazukagiWeb/blame/master/content/post/rich-content/index.md)（Markdown）

#### R code

R code部分包含了R統計學的操作方法，各位或許不太用得上，但本站希望未來可以收錄各種可重製研究的文章，因此特別給了它一個小小位置，對統計或數據科學有興趣的朋友可藉此機會瞭解RMarkdown的趣味所在。

-   [RMarkdown](https://rmarkdown.rstudio.com)

#### Mathematical

如上一小節所示，原生的Markdown並不支援數學公式的顯示。但由於學術書寫的需求逐漸拓及Markdown的領域，於是依附於Pandoc強大轉換能力的編輯器一一出現，它們借助於KaTex語法有效地顯示各種數學符號及其在公式當中的相對位置，KaTex的技術文件及本站模板示例如下。

-   [KaTex](https://katex.org)

-   [Math Typesetting](https://hazukagi.sintaika.com/p/math-typesetting/)（顯示效果）

-   [Math Typesetting](https://github.com/aciddylan/hazukagiWeb/blame/master/content/post/math-typesetting/index.md)（Markdown）

#### Bibliographic

與數學公式一樣，書目引用的支援也來自於漸漸形成的Markdown學術寫作需求。雖然書目引用同樣可以透過手動的方式來加入（相信各位研究生們都很在行），但Pandoc同樣也具有對BibTex的格式支援，並且可以透過CSL[^14]渲染為指定的引用樣式。這些功能在許多編輯器裡當然是不會缺席的，甚至還有編輯器提供了對Zotero的直接支援（例如本文介紹的RStudio和Zettlr都支援Zotero），從Zotero直接引用後就自動生成BibTex文件。

[^14]: CSL是一種引用格式語言，廣泛用於Zotero及[Mendeley](https://www.mendeley.com/)等文獻管理軟體或支援BibTex文件的編輯軟體中，在西方世界有許多期刊文獻除了說明格式之外，也會釋出CSL檔案供作者使用，可惜的是台灣尚未習慣運用這些工具，參見[Citation Style Language](https://citationstyles.org)。

本站的Blogdown架構自然也是支援這種引用方式的。只要將BibTex文件與Markdown文本放在同一資料夾下，並在YAML當中指定BibTex文件的檔名，即可渲染出引用的格式。那由於本站模板的格式關係，比起APA等行內引用格式，會較為適合運用註腳的引用格式。未來將會釋出一篇貼文，示範本站的引用格式以及CSL的樣式文件，以下僅先提供BibTex的官方網站給各位瞭解。

-   [BibTex](http://www.bibtex.org)

## 第二部分｜格式說明

### 文章結構

### 層級安排

不管是哪一種類型的文本，標題層級絕對可以說是最重要的功能。但在Word等WYSIWYG文件當中，常常會因為「看起來像」的原因，而讓使用者混淆內文與標題的格式設定，在Markdown標記中則不常發生這種狀況。（試想你要把內文加粗、放大，並且得到和渲染後的某層標題一樣的字型和顏色效果的話，要加多少標記呢？）

在Markdown文件當中，第一級標題通常就代表整份文件的大標，第二級之後才是內文各章節的標題。但依編輯器與轉換設定的不同，渲染規則也會有些許差異。例如，使用RStudio時，如果將文本類型指定為rtical（如ctexart）或是使用bookdown（如ctexbook）時，第一級標題便會是各章節的標題，而文件的大標則會儲存在YAML當中；Blogdown雖然也將大標儲存在YAML中，但內文則遵循一般的標題規則，若在內文使用第一集標題的話，雖然會顯示其格式，但目錄表會忽略不計。特例的部分就只能請各位跟編輯器好好培養感情，理解自己常用的格式及渲染的效果了。

標題的標記方式為：在行頭以`#`符號註記，並在空格後輸入標題文字，如`# 標題文字`。`#`符號的數量對應標題的層級，一般的Markdown提供有六層的標題記號。但透過以上的展示，可以看到第四級之後的標題文字漸漸變得比段落字體還小。因此，除非有特別調整渲染格式，一般Markdown文本在輸出為HTML時，文章結構不建議超過四級。

### 引用格式
