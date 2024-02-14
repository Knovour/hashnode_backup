---
title: "Steam Deck OLED 小主機調教記錄"
seoDescription: "將我的 Macbook Pro 換成 Steam Deck OLED"
datePublished: Tue Feb 13 2024 15:57:14 GMT+0000 (Coordinated Universal Time)
cuid: clskjqpx7000208l2aljj7imv
slug: steam-deck-oled-for-work-pc
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1707839698565/2dc009de-49a7-4188-b205-6f787890acda.jpeg
tags: linux, stream-deck, flatpak

---

看了國外一些用 Steam Deck 拿來當小主機用的影片感覺很心動，去年底 OLED 版推出時想把他拿來代替我的 Macbook Pro，原本是用 MBP 外接螢幕上下看，但除了前端開發外，其實很少用到 mac 螢幕，加上換了比較大的主螢幕後需求更低了，而且同時使用也會佔桌面前後空間

當然我知道一般人都是筆電蓋起來放旁邊當個小主機用，我以前有接雙螢幕時會這樣做，但因為雙螢幕需要時常轉頭傷到脖子後就放棄了

%[https://www.youtube.com/watch?v=tH_aHZQqTqI] 

想想我也沒在玩什麼 3A 大作，更沒有在訓練 AI（被時代拋棄）

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707838878764/b5a94f09-ad25-4fb3-b664-3880ff56f6de.jpeg align="center")

所以 M 系列晶片對我來說應該算是資源過剩，加上原本的 Linux PC 壞掉後就有在考慮改用 Linux 小主機，但一直沒有特別滿意的，也沒什麼動力；然而這次 Steam Deck OLED 有打中我，目前從下單入手到現在一個多月逐漸習慣了，所以把遇過的坑記錄一下

本文章需要對 ArchLinux 或衍生的發行版有操作經驗或基本瞭解

## 系統設定

在開始前先在 konsole 裡面輸入 `passwd` 設好 root 密碼

### 優化

<div data-node-type="callout">
<div data-node-type="callout-emoji">🛠</div>
<div data-node-type="callout-text"><strong>CryoUtilities</strong>: <a target="_blank" rel="noopener noreferrer nofollow" href="https://github.com/CryoByte33/steam-deck-utilities" style="pointer-events: none">https://github.com/CryoByte33/steam-deck-utilities</a></div>
</div>

%[https://www.youtube.com/watch?v=C9EjXYZUqUs] 

[CryoUtilities](https://github.com/CryoByte33/steam-deck-utilities) 算是當小主機用之前必須先弄的優化方案，安裝好後打開輸入密碼，直接點 Recommended 就行

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707746149105/169bf1a3-43a8-4c79-9e3d-190b6e0a6614.jpeg align="center")

VRAM 的部分需要進到 BIOS 裡設定，原本建議是 4GB，但想說我沒有玩什麼很吃資源的遊戲所以設 2GB，不過平常使用時還是會有意無意的卡一下，所以重灌後就照建議設 4GB 了，再觀察

**參考來源**

* [【密技】 Steam Deck效能調校心得 （圖多注意）](https://forum.gamer.com.tw/C.php?bsn=60599&snA=40696)
    
* [\[閒聊\] SteamDeck兩周心得(配件、調校、套件)](https://www.ptt.cc/bbs/Steam/M.1672478420.A.6FC.html)
    

<div data-node-type="callout">
<div data-node-type="callout-emoji">🛠</div>
<div data-node-type="callout-text"><strong>Decky Loader</strong>: <a target="_blank" rel="noopener noreferrer nofollow" href="https://github.com/SteamDeckHomebrew/decky-loader" style="pointer-events: none">https://github.com/SteamDeckHomebrew/decky-loader</a></div>
</div>

目前不急著試，先坑起來放著

### 套件管理

<div data-node-type="callout">
<div data-node-type="callout-emoji">📦</div>
<div data-node-type="callout-text"><strong>Pacman</strong></div>
</div>

不建議直接用 pacman 安裝套件，官方說法是在系統更新時可能會洗掉安裝的東西，雖然我在這期間沒有遇到（我還把更新設成測試頻道），但其實有比可能會被洗掉更大的問題存在

一是官方維護的套件版本大多偏舊，而 Steam 除了 Arch 之外還有另外維護自己的專屬套件與 library，所以換 mirrorlist 不是個明智的選擇

二是系統的硬碟分割很吃緊，可能裝沒幾個就沒空間了，主要還是看該套件對應到哪些系統資料夾就是

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707749275767/c0ce3db2-f68b-450b-876f-11200cc9cbdf.jpeg align="center")

三是官方有對已安裝的套件刪掉部分檔案，比如附圖的 `stdio.h` 是包在 glibc 裡；雖然該套件已安裝，但大部分的檔案都刪掉了，若你裝的套件（比如 aur）或是專案是需要編譯的話則會遇到很大的麻煩，當然你也可以選擇[超暴力解](https://github.com/Jguer/yay/issues/1910)，把所有東西重裝一遍，或是改用 brew 安裝

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707749469834/fb66a15e-e4d9-4167-8c72-e5aa07f6a3ea.jpeg align="center")

如果決定要裝的話，先輸入以下兩行指令解鎖系統讀寫跟初始化，我還是有裝一些 KDE 相關以及不需要最新版的套件

```bash
sudo steamos-readonly disable
sudo pacman-key --init && sudo pacman-key --populate archlinux
```

<div data-node-type="callout">
<div data-node-type="callout-emoji">📦</div>
<div data-node-type="callout-text"><strong>Yay: </strong><a target="_blank" rel="noopener noreferrer nofollow" href="https://github.com/Jguer/yay" style="pointer-events: none">https://github.com/Jguer/yay</a></div>
</div>

AUR 的套件管理器，照著 Binary 的方案安裝即可，但鑑於上述的風險，安裝 AUR 套件時建議選擇 -bin 結尾或是 AppImage 的套件

<div data-node-type="callout">
<div data-node-type="callout-emoji">📦</div>
<div data-node-type="callout-text"><strong>Homebrew: </strong><a target="_blank" rel="noopener noreferrer nofollow" href="https://docs.brew.sh/Homebrew-on-Linux" style="pointer-events: none">https://docs.brew.sh/Homebrew-on-Linux</a></div>
</div>

非 GUI 相關套件的最佳選擇，會安裝在 home 資料夾底下，所以重灌後不用擔心會洗掉，缺點是套件相依性會照 brew 的設定走，所以有可能會因為一個套件而連帶裝了大量相依的東西

<div data-node-type="callout">
<div data-node-type="callout-emoji">📦</div>
<div data-node-type="callout-text"><strong>Zap: </strong><a target="_blank" rel="noopener noreferrer nofollow" href="https://github.com/srevinsaju/zap" style="pointer-events: none">https://github.com/srevinsaju/zap</a></div>
</div>

AppImage 的管理方案，不是每個程式都有出 Flatpak 版本（比如 [Heptabase](https://heptabase.com/)），所以只能選擇這個方案，一方面也是因為他可以直接抓 GitHub 打包的版本。當然你也可以直接用 yay 裝 AUR 裡打包的 AppImage，但 zap 也會把檔案放到 home 裡，也會幫你更新 menu，所以自行取捨吧

雖然 AUR 裡有 zap-bin，但該版本過於老舊，bug 非常多，建議裝 GitHub 裡的 `install.sh` 最新打包版本

<div data-node-type="callout">
<div data-node-type="callout-emoji">📦</div>
<div data-node-type="callout-text"><strong>Flatpak</strong></div>
</div>

官方建議的安裝方案，直接用 KDE 的 Discover 軟體中心安裝即可，但我發現少數的套件並非最新版也沒法抓到更新，後來我在設定裡直接按新增來源，再把 Flathub 的軟體庫重新加入一次之後就正常了

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707752418484/7d47a36b-032f-4049-b1d4-4f54d6ef4cd8.jpeg align="center")

* [Installing from FlatHub | Discover](https://trigg.github.io/Discover/install_flathub.html)
    
* [https://flathub.org/repo/flathub.flatpakrepo](https://flathub.org/repo/flathub.flatpakrepo)
    

### 輸入法

之前在 Mac 是使用[威注音輸入法](https://github.com/vChewing/vChewing-macOS)，對 Dvorak 佈局有很完整的支援，十分推薦。遷移到 Steam Deck 之後原本是用 Fcitx 的新酷音，但他對該佈局的支援不包含標點符號的位置，逗號、句號那些都跟 Dvorak 一樣在鍵盤左半邊，而且頓號打不出來

後來改用 RIME 的中州韻輸入法，除了自訂成 Dvorak 對應外，標點符號也有做對應的變動

%[https://gist.github.com/Knovour/350cabad17d51adaa5085b14ff825f36] 

將檔案存成 `bopomofo_tw.custom.yaml` 放到 `~/.var/app/org.fcitx.Fcitx5/data/fcitx5/rime`下，也可以照下面的設定點開使用者資料夾，放好後重新啟動輸入法即可

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707784820825/8f9e88b9-7460-449e-ae8f-9c2b9b4db648.png align="center")

另外由於 Fcitx 也是以 Flatpak 的形式安裝，所以以前原生的輸入法設定不再管用，若你需要用 Bottles、Lutris 等 Wine 方案來跑 Windows 的軟體，則必須在權限下新增這三個環境變數才能正常打字

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707789238214/d4a3a0c1-883b-4a9c-894e-4cfaddae8ac5.jpeg align="center")

不過這樣繼續讓輸入法跟鍵盤佈局爭鬥也不是辦法，可能真的要考慮考慮行列輸入法也說不定，另外威注音長期計劃也打算跨平臺支援，算是我的 Mac 生涯中最好用的輸入法，值得期待

**參考來源**

* [Rime 定製指南](https://github.com/rime/home/wiki/CustomizationGuide)
    
* [能否支持 docker desktop #238](https://github.com/fcitx/fcitx/issues/238)
    
* [行列30](https://github.com/rime/rime-array)
    
* [\[長期計畫\] 世界樹行動：將威注音的跨作業系統通用邏輯獨立成一個單獨的 Swift Package。 #514](https://github.com/vChewing/vChewing-macOS/issues/514)
    

## 開發環境

### Terminal

[Yakuake](https://apps.kde.org/zh-tw/yakuake/) 讚，每次用 Linux 必裝

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707793860783/0bf3bfaa-2834-4b77-8a24-3a13e1e60036.jpeg align="center")

另外還有 [WezTerm](https://wezfurlong.org/wezterm/index.html) 作為 Helix 編輯器載體

### Shell

雖然 [Fish](https://fishshell.com/) 在這幾年關注度有提高，但我個人比較喜歡 [Nushell](https://www.nushell.sh/)，不過 Nu 目前尚未 1.0，許多 config 語法會因為版本更新而必須調整，加上 Steam Deck 提供的版本並非最新版，所以無法直接套用從 Mac 備份過來的設定檔，只能用 brew 裝

另外將原本用的美化方案 [Oh My Posh](https://ohmyposh.dev/) 改成比較輕量的 [Starship](https://starship.rs/)，而 Starship 本身也有提示功能，所以不想折騰的直接用 Zsh 也行

另外像 Konsole、Yakuake 等預設要用哪個 shell 不是用 chsh 調整，而是要去設定重新指定路徑，WezTerm 也一樣

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707874698040/d9cfd8b0-0124-4e15-94f5-509172c15336.jpeg align="center")

### IDE

VSCode 目前還是首選，雖然他是用 Electron，但我在沒有跑優化前打開來還是能正常使用，反倒是另一個主打 Rust 開發的 [Lapce](https://lapce.dev/) 我一打開來就當機，開了五次當了四次

不過大概是因為 Flatpak 的影響，VSCode 的 terminal 抓到的 shell 不是外部的，所以現在用 Yakuake 代替

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707797623380/9492afb3-51b3-4f26-8f50-a4e00eb38a43.jpeg align="center")

另一個 Rust 寫的 [Zed](https://zed.dev/) 在最近也開源了，雖然目前只有 Mac 版就是，加減期待一下吧

### 編輯器

[Neovim](https://neovim.io/)、[Helix](https://helix-editor.com/) 等需要在 terminal 執行的編輯器，會因為 Flatpak 的關係導致無法直接用指令開啟，另外因為環境封閉的關係，還需要另外安裝 `org.freedesktop.Sdk.XXX`才能用 LSP 做語法檢查、highlight 等功能，完全是本末倒置

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707799445234/b51536b4-3efa-43be-8dc2-e7ae0c8ddb5a.jpeg align="center")

更別說個別的版本還得等官方更新了，有些甚至沒有對應的資源，如果要照著弄，還會導致一些語言或 framework 的支援還得特地連到 Flatpak 之外的環境才行，對於 Vue、React 等前端開發只是自找麻煩

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707800329962/b35322cf-1c02-482f-9455-c27029d6d4c6.jpeg align="center")

另外對於編輯器的選擇，比起 Neovim，我對 Helix 的興趣要大一些，雖然 plugin 之類的功能尚未實作，但目前拿來開發一些小專案也是綽綽有餘

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707796535188/d5f016ba-bd2e-471f-9e54-bf194a565a15.jpeg align="center")

* [Neovim Flatpak First Run](https://github.com/flathub/io.neovim.nvim/blob/master/neovim-first-run.txt)
    
* [Helix Flatpak First Run](https://github.com/flathub/com.helix_editor.Helix/blob/master/HELIX_FIRST_RUN.md)
    

### 版本控制

直接用 pacman 裝 docker 跟 docker-compose 掛 volumes 把專案打包就好，頂多就是編輯器需要接 LSP 所以用 brew 裝一下

不想用 docker 的方案也可以考慮用 [asdf](https://asdf-vm.com/) 來做版本控制

## 設計

### 網頁設計

想要讓 Flatpak 版本的 Figma 抓到系統字型的話，記得把 `/usr/share/fonts`、`/usr/local/share/fonts`再加一次才能讀到字型，重灌後記得重新加一次

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707832337356/84cdbb59-3d50-4d54-a099-d13a3a1d9eba.jpeg align="center")

### 平面列印

好幾年前因為有做海報、名片等設計需求所以有買 [Affinity 三兄弟](https://affinity.serif.com)，雖然我的功力跟需求並沒有到非常需要專業軟體，但當時 Inkscape 很不穩定，Scribus 很過時，也是不爽 Adobe 開始推訂閱制所以買了 Affinity 來支持

而 Affinity 的產品用 Wine 跑不起來，現在也只剩名片有在更新內容，所以就先在 Affinity 把他匯出成 svg 轉到 Inkscape 處理，本來是想讓 Scribus 接手，但 Scribus 用起來感受實在是太糟糕了，而 Inkscape 如今也變得很穩定了，Scribus 只要負責匯出就好，加上現在有不少網路服務，所以先這樣撐著

### 圖片管理

[Eagle](https://eagle.cool/) 目前還可以用 Wine 啟動，用 Lutris 跑比用 Bottles 正常，在 Bottles 底下有些圖會跑不出來，但 Lutris 會讓桌面 icon 無法點擊，瀏覽器附加元件可以正常保存圖片，但我很懷疑接下來要出的 4.0 是否也能正常運作

%[https://twitter.com/eagle_app/status/1718950644411932723] 

前陣子有看到 [Allusion](https://github.com/allusion-app/Allusion) 這個 app，但還沒實際試過，先裝起來放著

## 其他

### 瀏覽器

當初沒優化時用 Brave 瀏覽器一天當機兩三次，用 Edge 兩三天才會當一次

不過 Edge 在開 Youtube 時界面都會卡很久才載入，跟前陣子的 [AdBlock 事件](https://www.techbang.com/posts/112561-google-youtube-browsers-adblocks)無關，就是單純超卡。後來發現 [Floorp](https://floorp.app/) 這個 Firefox 改的瀏覽器，Youtube 載入很正常，目前體驗下來各方面都很不錯，現在是我的預設瀏覽器，而 Edge 頂多在網站開發時才會用到

%[https://www.youtube.com/watch?v=7GoINJcMLOE] 

更重要的是，Chrome 為基礎的瀏覽器在使用 Picture in Picture 功能時視窗大小有限制，如果把視窗拉到 Steam Deck 裡就會變得很小，而 Firefox 則沒有這個限制，不僅能顯示字幕還能全螢幕，讓我的 Steam Deck 在桌面環境下外接螢幕時有額外用途

Edge

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707835568166/12f8dd5e-dbe0-4181-881e-b8999464fc94.jpeg align="center")

Floorp

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707835576100/f6ed7a39-0a68-4073-b52f-0c3b50be6990.jpeg align="center")

你可能會在 Discover 裡發現他叫 Floorp Lightning，這是停止更新的版本，遇到的話照上面套件管理的地方把 flathub 來源重新加一次應該就正常了

### 聊天軟體

Line 用 Bottles 跑比較正常，執行器用 sys-wine，也能正常打字，只是不想看到視窗的話記得縮小或關掉，不然會有殘影在上面

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707837022118/cd0f0901-eee4-43db-a9f0-63962adac9b3.jpeg align="center")

### 其他套件

<div data-node-type="callout">
<div data-node-type="callout-emoji">📦</div>
<div data-node-type="callout-text"><strong>Pacman 安裝</strong></div>
</div>

* kdegraphics-thumbnailers：讓 Dolphin 檔案瀏覽器有圖片縮圖預覽功能
    
* qt5-imageformats：同上，讓縮圖增加 webp 支援
    
* ffmpegthumbs：同上，增加影片格式支援
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707837247782/ab37f68a-1a01-497c-ae32-fe353a362734.jpeg align="center")
    

<div data-node-type="callout">
<div data-node-type="callout-emoji">📦</div>
<div data-node-type="callout-text"><strong>Yay 安裝</strong></div>
</div>

* Shutter：截圖工具，內建的 Spectacle 不太好用，在螢幕有設定等比例放大的狀況下視窗截圖有機會跑掉；但 Shutter 正常，只是沒有 Flatpak 版本
    

<div data-node-type="callout">
<div data-node-type="callout-emoji">📦</div>
<div data-node-type="callout-text"><strong>Flatpak</strong></div>
</div>

* YOGA Image Optimizer：Linux 版的 [ImageOptim](https://imageoptim.com/mac) 圖片壓縮程式
    
* Flatsweep：幫你清理 Flatpak 套件移除後留下來的檔案
    
* KWalletManager：Discord 之類的會要求啟用 KWallet
    

## 結尾

目前使用下來大致穩定，但每週還是有機會當機一次，不確定到底是我太操還是抽到機王。另外由於 Flatpak 的方案，遇到問題時還得多考慮是不是跟權限設定有關

一般玩家當然不推薦，但對於有在把 Linux 當成個人電腦來用的人來說，算是很有趣的經驗，我不確定我這決定能撐多久，但就現階段來說是滿意的