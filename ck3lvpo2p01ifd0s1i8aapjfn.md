## 這幾年使用 Linux 當一般作業系統的感受

上圖是我的 Linux 現在的樣子：

- 發行版：[Manjaro Linux](https://manjaro.github.io/)
- 桌面環境：KDE 5 Plasma
- 佈景：Maia Theme

Linux 在我大學期間就開始嘗試拿來作為一般的作業系統使用，但那段期間其實一直都在 Windows 跟 Linux 之間切換（你知道的，遊戲），後來這兩年開始固定用 Linux，工作時用 Mac，基本上已經沒怎麼碰 Windows 了。

當然，這個過程並沒有讓我成為什麼 Linux 大師，我也沒有這個打算，只是嘗試能在日常生活中使用而已。前一陣子看到[這篇文章](https://lex.sh/linux10khrs/)後覺得很有趣，於是決定也來寫篇自己的經歷以及感受。以下我會將本篇文章分成數個大項目來做探討。

裏面一些資訊可能與印象有所不同，請見諒。

#### 作業系統

我第一個用的 Linux 發行版是 Ubuntu 7.10，當時 [Compiz Fusion](http://www.compiz.org/) 這個桌面特效大補帖的相關影片出現時小紅了一陣子，我也是在那時候知道 Linux 以及其中的 Ubuntu。我已經忘記當時看到的影片是哪個了，不過就是如下面的影片所呈現的那樣。

%[https://www.youtube.com/watch?v=4QokOwvPxrE]

那段期間打開 Ubuntu 之後，也不過就是玩一玩特效、隨便打幾個指令、開 Firefox 晃一下就切回去玩遊戲了，沒辦法，這就是 Windows 最大的優勢。

到大二的時候，原本的電腦寄回老家，我再另外買一台基本配備的套裝主機，那時候 Vista 剛推出，而我也不疑有他直接用預設的。

**誰知道這正是噩夢的開始。**

當時那台主機記憶體只有 1GB，但光 Vista 本身居然就吃了 70% ~ 80% 的記憶體，隨便晃個滑鼠、開個視窗，記憶體要過 90% 都不是問題。在這情況下，這作業系統根本是沒辦法用的，不只吃記憶體，而且極端的不穩定，雖然後來多插了記憶體以及幾次系統更新後症狀逐漸減輕，但從那時候開始，我在空閒時折騰 Ubuntu 的次數反而大幅增加了。

比起 Vista，Ubuntu 裝上之後記憶體只吃了 20% ~ 30% 左右，開特效也沒有什麼大問題，但自從 8.04、8.10 版本推出之後，問題也開始多了。我還蠻執著於軟體什麼都要到最新版才行，所以新版本推出之後我也就升級了，但版本上到 8 之後，一切都不那麼美好了。半年一次的版本升級基本上就是個災難，直接升級的後果會讓 Ubuntu 有一堆奇奇怪怪的問題，與其花時間找方法解決這些問題，直接用新版重灌取代升級反而是最好的方法；當然，如果只要半年重灌一次就可以解決那到還好，怎樣都不會比我重灌 Vista 的次數多。但 Ubuntu 的軟體、library 版本不上不下，也稱不上穩定，在系統更新個幾次之後又開始有奇怪的問題了。

那時 Ubuntu 給我的感受是：**我有的問題別人不一定有，別人有的問題我基本上都會有，但別人提供的解決方式起碼有一半在我這邊行不通。**

拜這所賜，我的 Google 搜尋能力得到了提升，而主打一般人也能使用的 Linux 反而變得很常與指令、系統 config 打交道。所以想學好 Linux 基礎的話，去被 Ubuntu 惡整搞不好是最快的方式，這是我折騰到後面的感想。也因為如此，在我心目中最穩定的 Ubuntu 版本是 7.10（當然我也不算是很頻繁的用他），而在架伺服器時，我通常會先考慮 [CentOS](https://www.centos.org/) 或 [Scientific Linux](https://www.scientificlinux.org/)，Ubuntu Server 反而不會是我優先考慮的發行版。

後來有次在 Ubuntu 上當一次機之後，每重開機一次就有某個系統設定或某個軟體設定被初始化，重開越多次，就會越像系統剛裝好的樣子。在那場悲劇之後，一怒之下我就跳槽到 [ArchLinux](https://www.archlinux.org/) 了。

![](https://i.imgur.com/g130C.jpg)

> 在此掛上 8.10 的桌布來紀念那段日子（這也是歷來 Ubuntu 版本裡，我最喜歡的預設桌布）

當時看到這篇 [ArchLinux 推廣教學文](https://antimalicious.blogspot.tw/2009/04/archlinux.html)時就一直考慮要換，看了幾次教學文以及搜尋其他教學文章跟 VM 練習之後才下定了決心。要知道，那時候智慧型手機還沒有推出，手機上網也是件不容易的事，所以當時我把過程抄在紙上後，燒了光碟就開始弄了。當時的安裝過程就跟那篇推廣文的內容差不多，有基本的引導流程，所以沒有很大的麻煩（其實我不小心把 D 槽給格式化了）。

ArchLinux 裝完後問題其實也不少，但有很完整的 Wiki 在，基本上都是可以解決的事，就算要額外搜尋，也不太會有別人的解決方式我行不通的情形發生，雖然安裝過程麻煩了一些，但重灌的次數少了非常多。話雖如此，ArchLinux 的開發者卻覺得應該要提高安裝的難度，所以新版連基本的安裝導引都拿掉了，你得從頭到尾打指令才行。

第一次重灌時覺得算了，反正久久才會重灌一次，等到那個「久久」的時刻真的來臨時，我反而沒什麼耐心再搞安裝了。在這之前有搜尋過 ArchLinux 的衍生版，其中 [Chakra](https://chakralinux.org/) 以及 Manjaro Linux 是比較常看到有在討論的，安裝上也比較方便，在試了幾次 Chakra 都無法安裝成功後，我選擇了後者直到現在。

#### 桌面環境

Linux 的桌面環境基本上就是 Gnome 跟 KDE 這兩個為大宗，前者基於 GTK，後者基於 Qt，一個是以 Mac 桌面環境為參考，一個是以 Windows 為參考；在版本前進到 Gnome 3 以及 KDE 4 之後，兩者都開始走出屬於自己的路了。

當時 Ubuntu 是以 Gnome 2 為預設環境，8.10 以前是以淺色為基調

![](https://linux-cdn.softpedia.com/screenshots/Ubuntu-Gutsy-Gibbon_1.jpg)

> 來源：Softpedia

基本上看起來就是很無聊的樣子，到 9.04 時換成深色佈景，質感提升了不少。

![](https://news.softpedia.com/images/extra/LINUX/large/ubuntu904released-large_001.jpg)

> 來源：Softpedia

但對我來說他還是有個問題──他很好看，但不耐看，看了差不多三個月之後就看膩了。在那段期間，除了折騰系統上的問題之外，我還深深陷入了更換佈景及調整桌面配置的過程中；只要在 RSS 上看到有什麼 Gnome 佈景推荐的文章，或是像 [GNOME-LOOK.ORG](https://www.gnome-look.org/) 之類的網站看有什麼不錯的佈景，我就會抓下來試一試。

這些佈景在試用後的感想是：**深色系的普遍都不好看也不耐看，淺色系的有些雖不好看但還算耐看。**

而那時在我的作業系統上留最久的佈景應該是 [Bamboo Zen](https://www.gnome-look.org/p/1115382)。

![](https://cdn.pling.com/img//hive/content-pre2/85860-2.jpg)

> 來源：GNOME-LOOK.ORG

當時有一部份 Gnome 的淺色系佈景很喜歡打上一種噱頭：**像 Mac 一樣**。我不懂為什麼很多人想要讓作業系統看起來「像 Mac 一樣」，但他真的發生了。他們把色彩調成淺銀色或銀白色，加上點光澤，換掉圖標（我覺得在這當中最可憐的是 Firefox，因為他常被迫換上 Safari 的圖標），一個 Mac Like 介面就誕生了。在這段期間，最嚴重的莫過於誕生了 Pear OS 這個發行版。

![](https://news-cdn.softpedia.com/images/news2/Pear-OS-Is-Making-a-Comeback-Rumor-468670-3.jpg)

> 來源：Softpedia

不論這些像 Mac 一樣的佈景有多麼強調這件事，他們唯一不會跟你講的就是：「當你裝好之後，切記！盯著桌面看就好，不要做任何事，不要打開任何東西。」，因為隨便點開一個視窗就徹底破功了。這種事在 Android 上也在發生，只是模仿對象變成了 iOS。

不過 Pear OS 已經收掉了，目前的 Mac Like 發行版變成 [GMac Linux](https://sourceforge.net/projects/gmaclinux/)。

![](https://a.fsdn.com/con/app/proj/gmaclinux/screenshots/Screenshot%20from%202016-04-30%2014:30:55.png)

至於 Ubuntu 自己的 [Unity](https://unity.ubuntu.com/) 介面我就不知道要說啥了…

鏡頭切到 KDE 這邊，當時 KDE 3 我覺得沒什麼特色，完全沒有想用的慾望；但是當 KDE 4 推出之後，整個感受都不一樣了，不僅好看，而且耐看。在那之後推出的 Windows 7 更被調侃是「抄襲 KDE 4」，而後來 KDE 也很不客氣的把 Windows 7 上一些特色給抄了過來（比如拖拉標題到邊邊讓他佔半個螢幕）。所以在我跳槽到 ArchLinux 時，我也改用 KDE 作為我的桌面環境。

![](https://pic.pimg.tw/qwert535286/4b30ae36828b3.jpg)

> 這是當時的樣子：ArchLinux + KDE 4

KDE 好看歸好看，但還是得說，他從來沒有穩定過。並不是說用到一半就會全面崩潰之類的（早期倒是很頻繁），但總是會東壞一點西壞一點，雖不影響正常使用，但總是有疙瘩。

後來 KDE 5 Plasma 推出，整體而言又更上了一層，但還是一樣，他從來沒有真正穩定過，至少現在問題已經少非常多了。

![](https://c2.staticflickr.com/8/7788/28077094630_326e5dd9b8_o.png)
> 這是 KDE 5 Plasma 的預設佈景

有一個主打 Material Design 的桌面環境 [Papyros](https://liri.io/blog/2017/01/01/welcome-to-liri.html) 還在開發中，等穩定的時候再來試試看。

![](https://i.ytimg.com/vi/6XSyBV0h2n4/maxresdefault.jpg)

> 來源：YouTube

題外話：如果想要找個節省資源的桌面環境，比起 [Xfce](https://www.xfce.org/)，我會比較推荐 [LXQt](https://lxqt.org/)，至於其他一些比較硬派的桌面環境，我的興趣就不大了。

#### 開發工具

一開始把玩過一下 Emacs，後來在 Vim 上使用了一段不算短的時間，然而最終我還是沒能掌握那一堆快捷鍵以及指令的精髓，要是逼我使用 60% 鍵盤，我大概會瘋掉。那時大學時學的語言還是以 Java 為主，所以 Eclipse 等 IDE 還是比較常使用的，曾經看過一名同學在 Eclipse 上用快捷鍵用得嚇嚇叫，讓我十分佩服，雖然最後他被當了。

工作之後開始使用 Mac 跟 Sublime Text，在開發 web 挺方便，缺點是在 Linux 底下無法打中文，不管打什麼補丁、用什麼方法都不管用，不過當時也沒有比較好的替代品，所以在 Linux 底下還是只能將就。之後 Atom 推出 Beta 測試，不算上他用起來像 Alpha 這件事，光是能好好打中文就謝天謝地了，在推出測試之後就立馬換上。再之後推出正式版時，Visual Studio Code 推出了，這編輯器在使用上感覺比 Atom 舒服不少，所以在試用一陣子之後就又換了。將來會不會又想跳哪個編輯器我也不知道，不過 [Spacemacs](http://spacemacs.org/) 頗讓我感興趣的，前提是我有沒有心想記那一堆快捷鍵…

![](https://i.imgur.com/hTIXoZe.png)

#### 硬體支援

顯卡就是挑 NVIDIA，驅動在 Linux 上的支援度比 AMD 好太多太多了。一些小東西比如無線網卡之類的，不要挑功能太多或看起來好像很高檔的，不然就算有幸找到支援的驅動，在抓取硬體時很可能也會是這次有抓到，但下次就不一定了。

#### 軟體

如同 Gnome 與 KDE 之爭一樣，軟體開發的 GUI Library 也是以 GTK 跟 Qt 為主流，少部份會用 Tcl/Tk 之類的東西。不過不論是用哪種 Library，最困難的一點莫過於跨平台這件事，基本上有跨平台又好用的軟體少之又少，而在跨平台之中，每個都能有一樣的使用體驗更是難上加難。

一些像 [Krita](https://krita.org/)、[Blender](https://www.blender.org/) 跟 [LibreOffice](https://zh-tw.libreoffice.org/) 之類的軟體都能在三個作業系統上有不錯的體驗，而 [GIMP](https://www.gimp.org/)、[MyPaint](http://mypaint.org/) 在 Windows 及 Mac 平台上有時會因為編譯問題而延遲發佈，穩定性也稍微低一點，至於 [Inkscape](https://inkscape.org/)…他連在 Linux 上都不一定穩定了。誠心建議，如果想在非 Linux 平台使用 GIMP 跟 Inkscape 的話，可到[這個網站](http://www.partha.com/)下載另外編譯打包好的版本，執行起來相對穩定許多。

而有些企業會突然宣佈產品支援 Linux，比如 [Xara Xtreme](http://www.xaraxtreme.org/)，在宣佈支援的時候可是歡騰了一小陣子，畢竟除了 Inkscape 外沒有什麼強大的替代品可供挑選，然而在更新幾個小版本後就已經沒有任何維護了；要不然就是像 [Foxit Reader](https://www.foxitsoftware.com/products/pdf-reader/comparison.php) 那樣，維持最低限度的更新。

![](http://downloads.xara.com/opensource/images/screenshots/technical/05.jpg)
> 圖片來源：Xara Xtreme

在這幾年裡，[Electron](https://electron.atom.io/) 開始流行，很多服務開始用「包著網頁當軟體」的方式來實現跨平台，如果打一開始就這樣推出的話到不是什麼問題，但如果是中途變更可能反而會造成反效果。

比如像 Linux 上的 Skype，簡直就像是半個僵屍一般，在 Linux 上破破爛爛的，當 Windows 跟 Mac 都換上新介面的時候，只有 Linux 版在被收購那一陣子換上微軟大大所有、加上微軟帳號登入後就不再有任何更新，不論官方論壇上的人有多憤怒，聽不到就是聽不到。

然而前幾天微軟突然發佈一個好消息，宣佈 Linux 版 Skype 重新製作的 Alpha 版測試，這基本上就是個大消息，之前他在表面上說自己有多麼積極擁抱 Linux 的時候，Linux 版的 Skype 默默的躺在一邊啜泣，而現在卻又重獲關注，多麼棒的消息！

Skype 的 GUI 是基於 Qt，但是在裝上 Alpha 版之後發現，怎麼捨棄了 Qt 用上 GTK 了？打開後的直覺是這應該是 Electron 打包的（Electron 基於 Chromium，Chromium 基於 GTK），Reddit 以及一些文章也有提到這件事；雖然 Visual Studio Code 也是 Electron 打包的，用起來也不錯，但 Skype 這種作法實在是太忽悠人，畢竟有四五年沒有任何更新。尤其在這之前已經有許多人嘗試用這種方式打包網頁版了，其中有些運作得還不錯，微軟真的沒有直接拿別人的程式碼來改？再一次，微軟又讓人失望了。

![](https://i.imgur.com/7ypK1jF.png)
> Ghetto Skype, base on Electron（人家還可以選佈景勒）

很多時候，在 Linux 上使用軟體真的覺得自己像個次等公民一樣，但現在 web 技術愈來愈發達，很多東西已經都是改在網頁上完成，所以這個隔閡就顯得比較不那麼嚴重了（但微軟還是該死）。

#### 遊戲

拜 [DOOM](http://doom.com/) 系列遊戲 Open Source 所賜，以前 Linux 上 3D 大型遊戲裡佔絕大多數的就是 FPS 類遊戲，其他的就是一些像 [SuperTux](https://supertux.github.io/) 之類的 2D 小遊戲，沒有什麼能夠提起興趣的，主要還是開 Windows 打魔獸三國之類的居多。

後來 [HoN](http://www.heroesofnewerth.com/) 推出，第一款不用魔獸三就能獨立執行的 Dota 類遊戲，而且還支援 Linux，在玩過幾次之後就慫恿朋友也跟著跳坑，但無奈官方希望能夠用收費的方式經營，在歷經一年多的免費暢玩後，遊戲收費的第一天，人氣直跌谷底，分別回流到原本的魔獸與那時剛推出不久的 [LoL](http://na.leagueoflegends.com/)，過幾年後 [Dota2](http://blog.dota2.com/) 推出，我也就這樣轉戰過去了。幾年之後，HoN 默默改回免費模式，但已不再吸引人了。

之後開始工作時，玩的遊戲也變少了，通常都是周末時才會開 Windows 打一下 [PoE](https://www.pathofexile.com/) 或 Dota2，當時我跟我朋友開玩笑說：「如果兩款其中一款出了 Linux 版，那我大概就不會再切到 Windows 了」。在大約又快一年之後，[Valve](http://www.valvesoftware.com/) 開始全力推廣 Linux 遊戲，首先就將 Dota2 與 [CS:GO](http://blog.counter-strike.net/) 等旗下遊戲轉移到 Linux 上，從那時起，我自己的電腦就再也沒開過 Windows。

時至今日，Steam 上面的 Linux 遊戲愈來愈多，個人的收藏庫裡有過半是有支援 Linux，之後有空再來考慮怎麼玩那些 Windows 的遊戲。

#### 最後說一點 Mac

雖說是因為工作需求而買了 Macbook Pro，但那時對 Mac 實在沒有什麼感覺，只是覺得「有一天應該會需要用 XCode 寫 APP 吧」，所以對當時的我來說，就像是花了幾萬塊買了 XCode，但卻從來沒用過的感覺。

用了幾年基本上除了覺得觸控版做得很棒之外，真的沒有什麼很特別的評價，不討厭也沒特別喜歡。不過上面的軟體倒是有不少挺喜歡的，比如 [Sketch](https://www.sketchapp.com/)、[Affinity Designer](https://affinity.serif.com/) 等等，如果往後要說我為什麼會用 Mac 的話，大概會是因為上面有我喜歡的軟體吧（有 Linux 版我會很願意再花一次錢…，前提是功能要能完整體驗）。

#### 結論

- 感謝 Vista 讓我的人生有了轉折，其次是 Ubuntu（？
- Windows 上可以互相取代的軟體非常多，如果有人又在拿 GIMP 之類的說你或許不需要用 PS 云云，我建議你不妨先試試例如 [Paint.NET](http://www.getpaint.net/) 之類的替代方案，或是上 [AlternativeTo](https://alternativeto.net/) 找找看。
- 真的想用 GIMP 或 Inkscape 的話，[這個網站](http://www.partha.com/)編譯打包的比較穩定。
- Linux 推廣勸世文看看就好。
- 真的被勸成了也別挑 Ubuntu，挑 [Linux Mint](https://www.linuxmint.com/) 之類的 Ubuntu 衍生版比較穩定。
