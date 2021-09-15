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

本站是透過 **R**[^1] 的 **Blogdown**[^2] 套件所搭建的靜態網誌，站內所有文章皆以純文本 (plain text) 編寫，通過 **Pandoc**[^3] 轉換文件中的標記語言後，再以 **Hugo**[^4] 模板渲染為網頁文章。本文首先將說明此架構下，純文本的標記規則，以及其轉換之後的效果。並在最後提供文章格式建議，包括文章結構、層級安排及引用格式等相關說明。

[^1]: **R**是一套運用於統計的開發環境，具有非常活潑的使用者開發生態。透過使用者的集體努力， **R**有著相當豐富的套件，使得研究者除了處理統計資料外，也可以直接將研究成果渲染成各類型的圖表以及研究報告。詳見 [*The R Project for Statistical Computing*](https://www.r-project.org)。

[^2]: 由**謝益輝**所開發的**R**套件，詳見 [*Blogdown*](https://pkgs.rstudio.com/blogdown/)。

[^3]: **Pandoc**是一個開源的文本轉換工具，**Blogdown**的文件標記轉換依賴其功能。詳見 [*Pandoc.org*](https://pandoc.org)

[^4]: **Blogdown**所依賴的靜態網頁架構，詳見[*The world's fastest framework for building websites \| Hugo*](https://gohugo.io)。

本文僅供對 **Markdown** 完全沒有概念的朋友參考，有 **Markdown** 使用經驗的朋友可以略過第一部分的說明，唯需注意第二部分格式說明當中的建議。另外，本站並不強迫受邀作者繳交 **Markdown** 文件，**作者可依書寫習慣提交純文本，包括 `.md` 、 `.Rmd` ；或富文本 (rich text) ，包括 `.docx` 、 `.odt` 或 `.gdoc` 等所見即所得 (WYSIWYG) 文件**，但也請**稍加注意第二部分的格式說明**，本站會在收到稿件後與你討論並編輯處理。

## 第一部分｜標記語言

**Markdown**[^5] 直覺的標記方式，除了免去如 **Word** 檔等所見即所得文件 (**WYSIWYG**) 的各種格式錯誤，省下書寫時所浪費的格式調整時間，也讓使用者的書寫得以從 **Google** 或 **Microsoft** 等企業所提供的封閉式辦公文件當中解放，輕鬆進行轉換與渲染，銜接各種工作流程。本站使用的 **R** 套件 **Blogdown** 即是一個以 **Markdown** 為基礎的靜態網頁環境，使用者可以直接將具有 **Markdown** 標記的平面文件轉換為網頁貼文。

[^5]: 由 **John Gruber** 所開發的輕量標記語言，因未訂定標準，目前已出現許多衍生版本。 **Blogdown** 所使用的版本為 **Pandoc Markdown** ，此版本也運用在 **R Markdown** 及 **Bookdown** 等 **R** 套件中。本文僅列出本站需使用的標記方式，完整詳細的標記規則請見 **R Markdown** 中的說明 [*Pandoc Markdown*](https://garrettgman.github.io/rmarkdown/authoring_pandoc_markdown.html) 。

**Blogdown** 套件除了提供簡潔的 **Markdown** 語法支持外，也提供了各種多媒體與格式支援。除了支援 **KaTex**[^6] 數學公式，也提供了 **Hugo** 式的 **Shortcode**[^7] 語法，讓使用者可以插入 **YouTube** 影片及 **Instagram** 貼文等。另外，如果你是運用 **R** 語言的數據科學家的話， **Blogdown** 套件也直接支持了 **R code** 的執行，讓研究者得以直接在網頁上發表可再製研究的內容與圖表，甚至可以運用 **BibTex**[^8] 管理所引用的參考文獻。

[^6]: **KaTex** 是一種支援 **LaTex** 與網頁顯示的數學公式支援， **KaTex** 在目前某些開發較完整的 **Markdown** 編輯器中作為數學公式的補充標記語言詳見 [*KaTeX - The fastest math typesetting library for the web*](https://katex.org)。

[^7]: **Shortcode** 是 **Hugo** 用以補充 **Markdown** 無法在渲染後的頁面顯示多媒體的語法延伸方案。

[^8]: **BibTex** 是一種與 **LaTex** 配合，作為引用文獻資料的標記文本格式，也是目前許多 **Markdown** 編輯器處理引用文獻的主流格式，詳見 [*BibTex.org*](http://www.bibtex.org)。

本節將依先來後到分為通用的 **Markdown** 標記語法與 **Blogdown** （含 **Hugo** ）的特殊語法功能等兩部分，簡單介紹以上所提的標記法與顯示效果。若需要更詳細的資訊，建議參考 **Blogdown** 開發者**謝益輝**所著的專書 [*blogdown: Creating Websites with R Markdown*](https://bookdown.org/yihui/blogdown/)。

### Markdown

**Markdown** 是一種簡潔的標記語言，是目前主流的純文本標記語法，許多編輯器、筆記軟體及生產力工具現在都已經支援 **Markdown** 標記。在此除了說明一些寫作會運用到的基礎語法外，也會推薦一些開源的 **Markdown** 編輯器，提供尚未有慣用編輯器的朋友們參考。

除了編輯文本之外，如何用 **Pandoc** 渲染 **Markdown** 標記文本為其他類型的文件也是一門學問，尤其是含有中日韓 (**CJK**) 字元及 **LaTex** 標記的文本，在沒有設定好的狀況下，轉換為 PDF 時容易有缺字或渲染失敗的問題。

不幸的是使用 **Pandoc** 僅僅是 **Markdown** 工作流程的基礎功而已，要建立流暢的工作流程，就必須熟悉各種文檔間的轉換及渲染的設定方式。反之，使用 **Markdown** 又不理解 **Pandoc** 的話，比較不會對工作流程有明顯的助益， **Markdown** 文本也會僅僅成為一種存在於不同軟體中的資料而已。

或許一開始在學的時候會因為超級折騰，而放棄純文本回去用 **WYSIWYG** 。在此之前，推薦各位可以先看看以下的精彩文章，參考其他人如何運用純文本，再回過頭來對照自己的筆記及寫作流程，以及自己是否有使用標記語言進行純文本寫作的需求。

-   [*網路時代下的寫作 - Why R Markdown? - 協作閣*](https://collabin.netlify.app/yongfu/write-in-rmd/)
-   [*Markdown 写作，Pandoc 转换：我的纯文本学术写作流程 - 少数派*](https://sspai.com/post/64842)
-   [*如何构建自己的笔记系统？ - 知乎*](https://www.zhihu.com/question/23427617/answer/1461195696)（請用電腦版模式打開，手機版瀏覽需要知乎app）

我並不是完全的純文本信徒，我除了在意資料遷徙的自由度之外，更注重的是文獻來源的整理與運用，而且現在大多數的 **Markdown** 編輯器也都支援富文本等 **WYSIWYG** 文件的格式辨認。因此，使用純文本在資料遷徙上比較自由的認識論是必須受到質疑的，尤其是在充滿不少富文本開源編輯器的當代世界，格式支援並不是什麼大問題，比較要思考的反而是如何在末日下的電力危機，把資料從電腦裡搬出來。

在與 **Markdownism** 拉出一點距離後，我的工作流程中並沒有最近很紅的 **Obsidian** 或 **Roam Research** 等純文本網絡化筆記軟體，我反而在 **Zotero**[^9] 下蒐集、整理資料並製作富文本筆記，然後在寫作時直接將內容複製到 **RStudio** 及 **Mark Text** 等編輯器中，並用 **Git** 控制版本。雖然純文本已經挾著 **Markdown** 的潮流，勢不可擋地進入到書寫編輯的各領域當中，但依需求選擇適合自己的工具並與 **Markdown** 所擁有的自由度配合才是最重要的。

[^9]: **Zotero** 是一個開源的文獻管理軟體專案，擁有許多實用的外掛。目前的 Beta版帶有強大的筆記功能，預計於不久後也會推出 **iOS** 版本，詳見 [*Zotero*](https://www.zotero.org)。

回過頭來，這篇文章要說明的其實是本站使用的工具以及調和此工具與（ **Word** 式的）舊書寫習慣之間的落差，而這些 **Markdown** 的入門資訊恰恰好也會有助於理解目前電腦書寫的趨勢。最後，技術細節的部分請善用 [**Duckduckgo**](https://duckduckgo.com/) 或 [**Startpage**](https://www.startpage.com) 等搜尋引擎（不推薦賣個資又養套殺使用者的 **Google** ）或各編輯器所提供的說明文件來學習，本文不再贅述。

#### 開源編輯器推薦

網路上已有不少對 **Markdown** 編輯器的推薦，許多筆記軟體如 [**Notion**](https://www.notion.so/) 、 [**Roam Research**](https://roamresearch.com) 及 [**Obsidian**](https://obsidian.md) 等，都是以 **Markdown** 為基礎進行文本的標記與渲染， [**Evernote**](https://evernote.com) 也在最近跳進來沾了一點醬油。如果你已經用習慣了以上的軟體，可直接跳過本小節，但如果你是 **Markdown** 新手，或是想要開始嘗試開源軟體的話，可以試著瞭解以下所推薦的編輯器。

-   [**Atom**](https://atom.io)： **GitHub** 開發的開源程式編輯器，在 **GitHub** 的生態系中有相當豐富的外掛。推薦給對 **Python** 等程式語言有興趣，或預計會開始學習程式語言的人。

-   [**RStudio**](https://www.rstudio.com)：功能強大的 **R** 語言**整合開發環境** (**Integrated Development Environment, IDE**) ，建議還在跑 **SPSS**[^10] 的朋友們趕快棄坑，轉投 **R** 的陣營。**RStudio** 的生態系除了擁有各種強大的統計功能套件外，圍繞著 **R Markdown**[^11] 套件的書寫生態也相當豐富（並有支援 **Zotero** ），整合了資料蒐集、運算研究與書寫產出等流程，適合社會科學或數據科學研究者。

-   [**Zettlr**](https://www.zettlr.com)：與 **Roam Research** 和 **Obsidian** 一樣，主要的功能是卡片盒 (**Zettelkasten**) 筆記法[^12]，支援 wiki 式的網絡化語法標記。差別在於 **Zettlr** 是開源軟體，並且對 **Zotero** 有直接支援，適合不需要用到統計，且對卡片盒有信仰的學術研究者。

-   [**Mark Text**](https://marktext.app)：以上三種開源軟體的 **Markdown** 功能，都只能算是支援主要功能的書寫整合，而且有著較高的學習成本。如果只需要純粹地編輯 **Markdown** 文件，我會推薦這個功能強大的開源編輯器。就算有安裝以上三種軟體，我也會推薦它作為備用或不需用到其主要功能時的主力編輯器。

-   [**Byword**](https://bywordapp.com)：非開源，售價為新台幣190元，推薦這個軟體的原因是 **iOS** 上缺乏夠好的開源編輯器（**Android** 應該會有比較多不錯用的開源編輯器，但我沒涉略）。它因應了 **Apple**生態系的工作需求，除了可以存取 **iCloud** 檔案夾（這很重要！很多 app 都是做軟體內的封閉式同步），編輯功能也非常完整，推薦愛吃蘋果的阿迪仔與阿咩仔使用。我個人則是使用另一款同樣可以存取 **iCloud** 檔案夾的 [**Pretext**](https://apps.apple.com/app/pretext/id1347707000) （非開源、基本功能免費），推薦給覺得能用就好的人。

[^10]: **SPSS** 全稱為 **Statistical Package for the Social Sciences** ，是 **IBM** 所推出的又弱又貴的統計軟體，詳見 [***SPSS***](http://www.ibm.com/analytics/us/en/technology/spss/)。

[^11]: **R Markdown** 是 **RStudio** 以 **Markdown** 為基礎，用以整合研究與書寫流程的功能套件，詳見 [R Markdown](https://rmarkdown.rstudio.com)。

[^12]: 卡片盒 (**Zettelkasten**) 是提出社會系統理論、致力於社會風險管理的德國學者 **Niklas Luhemann** ，生前使用的筆記法。最近有許多紅到發紫的筆記軟體都是以這種網絡化筆記的概念來設計。但其實此種筆記法需要有非常嚴謹的層級規範配合，才能有效控制雜訊，並非許多中文教學文章所述，不斷紀錄和連結就可以變得跟他大佬一樣聰明俐落。是一種門檻極高的筆記方式，不推薦各位朋友使用。

#### 語法說明與顯示效果

**Markdown** 並非艱深困難的語法，它僅僅是區塊與區段的標記語言，學習時間與記憶成本非常低，直接使用是習慣它的最快方法。以下推薦先閱讀 **Markdown** 的基本語法規則，並配合本站的 **Hugo** 模板所提供的範例，參考顯示效果（基於 **Blogdown** 的轉換，Other Elements 的 **Hugo** 標記元素是失效的）。

-   [*Markdown 語法說明*](https://markdown.tw)

-   [*Markdown Syntax Guide*](https://hazukagi.sintaika.com/p/markdown-syntax-guide/)（顯示效果）

-   [*Markdown Syntax Guide*](https://github.com/aciddylan/hazukagiWeb/blame/master/content/post/markdown-syntax/index.md) (**Markdown**)

這邊需要特別說明的是腳註的語法。腳註並非 **Markdown** 的原生功能，但許多編輯器都已經支援腳註的語法，而且在上引的本站模板範例當中也有示範，因此直接在這邊稍作說明。其語法為`[^數字]`，數字的部分需要編輯者自行編碼，以下範例供參：

-   **標註方式**：

``` markdown
今晚，我想要來點阿岸米糕[^13]，還有阿宏師的雞肉飯加半熟蛋。

[^13]: **UberEat** 的廣告質感好很多， **FoodPanda** 的廣告我都不忍直視。
```

-   **顯示效果**：

今晚，我想要來點阿岸米糕[^13]，還有阿宏師的雞肉飯加半熟蛋。

[^13]: **UberEat** 的廣告質感好很多， **FoodPanda** 的廣告我都不忍直視。

如上列範例所示，一旦標記了 `[^13]` 的腳註，通常都會直接在段落的下方，以 `[^13]:` 說明註釋的內容。顯示效果的部分則可以看到，標註後會在錨點顯示含有數字13的上標，而所有腳註說明都會集中在頁面的最下方，並提供雙向的跳轉連結。這是本站及其他 HTML 輸出時的效果，而在輸出類型改為 `.pdf` 或 `.docx` 等多頁文件時，腳註說明則會直接出現在標註點的單頁下方。

#### YAML

在繼續往下之前，必須先介紹一個叫做 **YAML**[^14] 的東東。**YAML** 是儲存文件後設資料 (metadata)的區塊，一般會置於文件開頭，用以描述檔案性質或是用於寫入特定程式功能執行的指示，資訊內容可以包含標題、簡述、日期時間、語言類型、標籤、⋯⋯等對應到 **HTML** 語言的基本資訊；也可以包含配合編輯器或 **Pandoc** 的功能訊息，例如：書目資訊位置、渲染格式、程式碼模式、⋯⋯等。而本站在 **Blogdown** 架構下的 **YAML** 以 **HTML** 的應用為主，以下就本篇文章的 **YAML** 為例來說明各元素所代表的意義：

[^14]: **YAML**是一種序列化的格式語言，常見於網站構建及資料庫的描述等用途上，也是目前 **Markdown** 文本儲存後設資料的主要格式，參見 [*yaml.org*](https://yaml.org)。

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

文章所儲存的後設資料包含了 `title` 、 `author` 、 `date` 、 `categories` 、 `tags` 和 `description` 等較直覺的資訊，本文不另外說明，其他項目則說明如下：

-   `slug`：指定文件生成的永久檔名。

-   `image`：指定封面圖片，本文的封面圖片檔名為 `Unknown.jpg` ，此例封面圖片與文件置於同一目錄下。若置於某子資料夾下，例如 `pic` 資料夾的話，描述則成為 `image: pic/Unknown.jpg` 。

-   `math`：指定是否以 **KaTex** 顯示數學公式， `~` 代表預設值開啟。

-   `license`：指定文件的授權方式，預設值為 CC-BY-NC-SA 4.0。

-   `hidden`：指定文章是否隱藏，都開放源了，這個功能大概也雞肋化了。

-   `comments`：指定是否開放用戶評論文章的外掛模組，本站使用的模組為 [**Disqus**](https://disqus.com) 提供。但不知道為什麼這篇的留言功能掛掉了，明明其他篇都正常。

### Blogdown

如上一小節所示， **Markdown** 的基本標記語法僅能提供平面書寫的需求，而網頁貼文其實還包含了插入 **YouTube** 影片或社群網站內容等多媒體需求。在傳統的 **Markdown** 書寫當中，會直接以 **HTML** 語言來補充，但既然我們都使用 **Blogdown** 套件了，那這些功能當然也是要以更簡潔的語法方案來取代嘍。

雖然說本站所使用的語法集是由 **R** 套件 **Blogdown** 所提供，但其實除了 **Shortcode** 及 **R code** 之外，大部分允許使用 **Pandoc** 轉換的編輯器都有提供對 **KaTex** 數學公式及 **BibTex** 書目資訊的支援。平常使用下，都是可以無痛轉換的。

#### Shortcode

**Shortcode** 是由 **Hugo** 靜態網頁架構提供，藉此補充 **Markdown** 標記語法對 **HTML** 支援的不足之處。因此， **Hugo** 的 **Shortcode** 其實是一組對應到所有 **HTML** 的語法支援，而大部分的基礎書寫語法、插入圖片及超連結語法等已有 **Markdown** 語法的支持，此小節僅需理解 **YouTube** 及 **Vimeo** 等多媒體影片的插入，以及對 **Tweet** 或 **Instagram** 等社群貼文的顯示語法。語法內容如官方說明文件及本站模板示例：

-   [*Shortcodes \| Hugo*](https://gohugo.io/content-management/shortcodes/)

-   [*Rich Content*](https://hazukagi.sintaika.com/p/rich-content/)（顯示效果）

-   [*Rich Content*](https://github.com/aciddylan/hazukagiWeb/blame/master/content/post/rich-content/index.md) (**Markdown**)

#### R code

身為 **R** 套件的 **Blogdown** 理所當然地提供了 **R code** 的操作運算。含括在 **R Markdown** 生態中的 **Blogdown** 或 **Bookdown** ，都可以直接在文件渲染的過程中運算數據，並直接生成各種資料圖表，並且可以根據研究進度更新，或替換數據進行可重製研究。

本站未來會提供一篇小研究來示範這個功能，也期待以後有機會看到在嘉義的主題下有更多此類型的文章。有用過 **SPSS** 且對統計或數據科學有興趣的朋友可藉此機會瞭解 **R Markdown** 的趣味所在，另外也推薦一本可再製研究的著作供各位參考：

-   [*R Markdown*](https://rmarkdown.rstudio.com)
-   [*R Markdown Cookbook*](https://bookdown.org/yihui/rmarkdown-cookbook/)
-   [*Reproducible Research with R and RStudio (Third Edition)*](https://github.com/christophergandrud/Rep-Res-Book)

#### Mathematical

如上一小節所示，原生的 **Markdown** 並不支援數學公式的顯示。但由於學術書寫的需求逐漸拓及 **Markdown** 的領域，於是依附於 **Pandoc** 強大轉換能力的編輯器一一出現，它們借助於 **KaTex** 語法有效地顯示各種數學符號及其在公式當中的相對位置， **KaTex** 的技術文件及本站模板示例如下：

-   [*KaTex*](https://katex.org)

-   [*Math Typesetting*](https://hazukagi.sintaika.com/p/math-typesetting/)（顯示效果）

-   [*Math Typesetting*](https://github.com/aciddylan/hazukagiWeb/blame/master/content/post/math-typesetting/index.md) (**Markdown**)

#### Bibliographic

與數學公式一樣，書目引用的支援也來自於漸漸形成的 **Markdown** 學術寫作需求。雖然書目引用同樣可以透過手動的方式來加入（相信各位研究生們都很在行），但 **Pandoc** 同樣也具有對 **BibTex** 的格式支援，並且可以透過 **CSL**[^15] 渲染為指定的引用樣式。這些功能在許多編輯器裡當然是不會缺席的，甚至還有編輯器提供了對 **Zotero** 的直接支援（例如本文介紹的 **RStudio** 和 **Zettlr** 都支援 **Zotero** ），從 **Zotero** 直接引用就可以自動生成 **BibTex** 文件。

[^15]: CSL 是一種引用格式語言，廣泛用於 **Zotero** 及 [Mendeley](https://www.mendeley.com/) 等文獻管理軟體或支援 **BibTex** 文件的編輯軟體中，在西方世界有許多期刊文獻除了說明格式之外，也會釋出 `.csl` 檔案供作者使用，可惜的是台灣尚未習慣運用這些工具，參見 [Citation Style Language](https://citationstyles.org)。

本站的 **Blogdown** 架構自然也是支援這種引用方式的。只要將 **BibTex** 文件與 **Markdown** 文本放在同一資料夾下，並在 **YAML** 當中指定 **BibTex** 文件的檔名，即可渲染出引用的格式。由於本站模板的格式關係，比起 **APA** 等行內引用格式，會較為適合運用註腳的引用格式。未來將會釋出一篇貼文，示範本站的引用格式以及 **CSL** 的樣式文件，以下僅先提供 **BibTex** 的官方網站給各位瞭解。

-   [*BibTex*](http://www.bibtex.org)

## 第二部分｜格式說明

如上述，本節最主要的目的是調和本站所運用的工具及（**Word**式的）舊書寫習慣之間的落差。如果你並非純文本的使用者也不必擔心技術上的問題，只需要理解文章格式即可，其他工作會由編輯處理。在這裏，你可能會有另一個疑惑------自己的書寫風格真的能套用到一個標準格式當中嗎？這也大可不必擔心，這個格式僅僅是基於網站顯示的可讀性參考資料，並不是要框限作者文字的表現力。以下將分為後設資料、凡例、層級安排及引用格式等四個小節，進行簡短說明。

### 後設資料

如第一部分對YAML的介紹，每篇文章除了內文之外，還會有後設資料的存在，以下將羅列文章所需提供的後設資料，並對應YAML的資訊欄位，請作者依序填列。若是使用**Word**等**WYSIWYG**文件者，可將後設資料列於文章開頭，有星號者請務必填寫。

| 項目       | YAML          | 說明                                                                            |
|------------|---------------|---------------------------------------------------------------------------------|
| 標題\*     | `title`       | 文章的中文標題。                                                                |
| 作者\*     | `author`      | 作者姓名，可依個人習慣選擇使用本名或筆名，複數作者以分號分隔。                  |
| 日期\*     | `date`        | 文章發表日期。                                                                  |
| 英文標題\* | `slug`        | 文章的英文標題，將作為永久網址的位址。                                          |
| 範疇       | `categories`  | 文章在本站中的分類，由編輯處理。                                                |
| 標籤\*     | `tags`        | 文章的標籤，跟文章的主題、領域或方法有關的關鍵字，至少列出五個。                |
| 簡介\*     | `description` | 150字左右的文章簡述。                                                           |
| 封面圖片   | `image`       | 封面圖片，格式為解析度1600\*900以上的橫式圖片。                                 |
| 授權       | `license`     | 作者可依CC授權條款，選擇文章的授權模式。未選填時將依預設值CC-BY-NC-SA 4.0授權。 |

### 凡例

本站各篇文章使用以下的格式：

-   **專有名詞**：人名、公司、機構名稱、學科詞彙等，以粗體字表現。如：**嘉義市崇文國民小學**， **Markdown** 標記為 `**嘉義市崇文國民小學**`。
-   **著作**：著作包括文章、攝影、影音、書籍、⋯⋯等文學、科學及藝術領域受著作權法保障之著作，以斜體字表現。如：*嘉義市老戲院踏查誌*， **Markdown** 標記為 `*嘉義市老戲院踏查誌*` 。
-   **中譯**：提及英文**專有名詞**或**著作**時，請盡量使用原文，如是行文風格的考慮，而必須以中文表現者，特殊狀況外，請盡量使用台灣本地約定俗成之譯法，並在其後以括弧標註原文，或以腳註說明。
-   **括弧**：段落括弧內若全為英文者請使用半形括弧，如：他的名字叫做醬爆，本名何文輝 (Ho Wenhui)；若含中日韓字元者則使用全形，如：他興奮要跳舞（喺呢個moment要爆喇）。
-   **行內程式碼**：行內程式碼請以反引號 \` 包裹，如： `x = 1` ， **Markdown** 標記為 \`x = 1\`。
-   **區塊程式碼**：區塊程式碼請以三個反引號 \`\`\` 包裹，並指定程式碼類型。如要插入 **HTML** 程式碼的話，請以 **Markdown** 標記開頭如 \`\`\` {HTML} ，並在程式碼結束後以 \`\`\` 包裹。
-   **檔案與位址**：電腦或網路檔案與位址請以反引號 \` 包裹，如： `image/taiwan.png` ， **Markdown** 標記為 \`image/taiwan.png\` 。
-   **其他電腦程式物件**：與電腦或各種程式有關的物件，請以反引號 \` 包裹，如： `Package` ， **Markdown** 標記為 \`Package\` 。

### 層級安排

不管是哪一種類型的文本，標題層級絕對可以說是最重要的功能。但在 **Word** 等 **WYSIWYG** 文件當中，常常會因為「看起來像」的原因，而讓使用者混淆內文與標題的格式設定，在 **Markdown** 標記中則不常發生這種狀況。（試想你要把內文加粗、放大，並且得到和渲染後的某層標題一樣的字型和顏色效果的話，要加多少標記呢？）

在 **Markdown** 文件當中，第一級標題通常就代表整份文件的大標，第二級之後才是內文各章節的標題。但依編輯器與轉換設定的不同，渲染規則也會有些許差異。例如，使用 **RStudio** 時，如果將文本類型指定為 **rtical** （如 **ctexart** ）或是使用 **bookdown** （如 **ctexbook** ）時，第一級標題便會是各章節的標題，而文件的大標則會儲存在 **YAML** 當中； **Blogdown** 雖然也將大標儲存在 **YAML** 中，但內文則遵循一般的標題規則，若在內文使用第一級標題的話，雖然會顯示其格式，但目錄表會忽略不計。特例的部分就只能請各位跟編輯器好好培養感情，理解自己常用的格式及渲染的效果了。

而一般的 **Markdown** 提供有六層的標題記號，但第五級之後的標題文字會漸漸變得比段落內文的字體還小，而且不會出現在預設生成的目錄表中。因此，除非有特別調整渲染格式，一般 **Markdown** 文本在輸出為 **HTML** 時，**文章結構不建議超過四級，因此，請在二到四級標題間規劃文章的結構**。

### 引用格式

待補！

## 後記

雖然說這篇文章一開始只是要說明本站使用的工具，藉此讓作者和編輯可以有一個參照的索引。但開始寫下去之後才意識到，原來以 **Blogdown** 所製作的網頁，在技術上竟然會牽涉到這麼多東西。尤其是寫第一部分標記語言時，本來僅想把各種標記語法平行羅列，並示範樣式就好。但寫一寫才開始覺得，如果沒有更多技術索引，包括：各種類型的 **IDE** 或編輯器、 **YAML** 、 **Pandoc** 、 **BibTex** 等東東的話，大概也很難讓入門的使用者掌握 **Markdown** 最基本的運用樣貌。

修修補補寫完之後，本文看起來反而比較像是濃縮版的開源軟體寫作關鍵詞指引（以架站為例）。雖然說要架站的話可能還有超多東西沒有提到，但 **Blogdown** 其實是極輕量的架站框架，就算只參考（**謝益輝**的）官方文件，其實也足夠了。最後的最後，如果這篇文章讓你暈暈的，那就是我一次丟太多詞彙出來了，謹此向各位道歉。
