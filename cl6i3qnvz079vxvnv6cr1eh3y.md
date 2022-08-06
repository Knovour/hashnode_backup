## Keychron Q2 一些問題記錄

最近腦弱入手了一把 Keychron Q2 鍵盤，上手體驗還不錯，但還是遇到了幾個坑，在這邊記錄一下

### 一、按 Capslock 切換英文輸入會變成大寫
上 [Keychron Q 系列官網](https://q1q2q3.keychron.com.tw/)下載 VIA 鍵盤配置工具，隨便指定一個按鍵，讓他對應到 Special 欄位的 Toggle NKRO 按鍵

![SCR-20220806-wpk.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1659801667893/zKNKHs7Gg.png align="left")

設完之後按一下就恢復原狀了，不過每次鍵盤插拔都需要重新按一次，所以我把 Toggle NKRO 配置改到上面的 Layer 1，這是對應到鍵盤的 Windows 支援，只要重新插拔後把配置切換到 Win 按一下再切回 Mac 就好，不確定這是鍵盤本身的驅動問題還是 Mac 的 NKRO 支援問題

#### 參考來源
%[https://github.com/qmk/qmk_firmware/issues/15178#issuecomment-1032284061]
%[https://www.reddit.com/r/Keychron/comments/tn7rmw/comment/i25a63c/]

### 二、小麥注音在打字快時按三聲的部分不是沒出現就是出現兩次
目前改安裝威注音輸入法沒有遇到相同狀況

#### 參考來源
- [vChewing 威注音輸入法](https://vchewing.github.io/README.html)

### 三、威注音與 Dvorak 鍵盤配置衝突
在 Mac 我用 `Dvorak - QWERTY ⌘` 鍵盤配置，在 VSCode 下按 Capslock 切回英文輸入按 Command 鍵時切不回 qwerty 配置

解決方式：在 VSCode 設定中找到 `Keyboard.dispatch`，將偵測方式改為 `keyCode`
![截圖 2022-08-07 上午12.11.56.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1659802404204/TFz9NV2hU.jpg align="left")

#### 參考來源
%[https://stackoverflow.com/questions/59302499/vs-code-has-wrong-keyboard-shortcut-layout]