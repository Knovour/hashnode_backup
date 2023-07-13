---
title: "惡補一下 js 的 library 跟 framework"
seoDescription: "這兩年都用 Elixir + Phoenix + LiveView 在開發網站，遠離雜亂的 js 生態圈。最近剛好因為有相關需求，所以就大概看一下有哪些 js library 跟 framework，有興趣的就大概摸一下，寫個粗淺的心得"
datePublished: Thu Jul 13 2023 09:45:45 GMT+0000 (Coordinated Universal Time)
cuid: clk0ysugx000g0al9f4e87vpq
slug: some-js-library-and-framework
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689242164627/8d352730-bb95-4dc0-8acf-ea5c6787874b.jpeg
tags: frontend-development, backend-development, full-stack-development

---

這兩年都用 [Elixir](https://elixir-lang.org/) + [Phoenix](https://www.phoenixframework.org/) + LiveView 在開發網站，遠離雜亂的 js 生態圈。最近剛好因為有相關需求，所以就大概看一下有哪些 js library 跟 framework，有興趣的就大概摸一下，寫個粗淺的心得

為了這篇文章寫了三種 TodoMVC 組合供參考

* [Astro + Svelte](https://github.com/Knovour/astro-svelte-todomvc)
    
* [htmx + Alpine (data) + Nest.js](https://github.com/Knovour/htmx-alpine-nestjs-todomvc)
    
* [htmx + Alpine (store) + Adonis.js](https://github.com/Knovour/htmx-alpine-adonis-todomvc)
    

## 前端

### Svelte

<div data-node-type="callout">
<div data-node-type="callout-emoji">🔗</div>
<div data-node-type="callout-text"><a target="_blank" rel="noopener noreferrer nofollow" href="https://svelte.dev/" style="pointer-events: none">https://svelte.dev/</a></div>
</div>

%[https://www.youtube.com/watch?v=MnpuK0MK4yo] 

其實在轉用 Elixir 之前就用過 Svelte 寫過一兩個 side project；沒記錯的話，那時因為適逢 Vue2 到 Vue3 過渡期，就連 Nuxt.js 這 Vue 的最大推手也遲遲未有升級支援，而 React Hooks 帶來的開發體驗對我來說並沒有好多少，對於這兩大生態圈感到疲勞，所以就跳到 Svelte 去了

%[https://twitter.com/yuxiyou/status/1676093893979545608] 

<div data-node-type="callout">
<div data-node-type="callout-emoji">✅</div>
<div data-node-type="callout-text">優點</div>
</div>

* 同樣的功能，Svelte 可以用少量的程式碼實現，沒有太多冗餘的 function
    
* 從 jQuery 轉到這些前端大坑後，Svelte 是少數有帶給我所謂的「良好的開發體驗」的；上一個是 [Elm](https://elm-lang.org/)，可惜他死透了
    
* 使用 js library 大多不需要像 React 那樣繞來繞去，或是得找額外打包好的 xxx-react 套件，直接使用即可，所以不存在什麼「生態圈太小」的說法
    

<div data-node-type="callout">
<div data-node-type="callout-emoji">🤌</div>
<div data-node-type="callout-text">缺點</div>
</div>

* 數據綁定方面用了很多語法糖，compiler 做掉了很多東西，所以初次使用在這方面會需要一點「想像力」
    

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">延伸閱讀</div>
</div>

* [SvelteJS: My ecosystem is bigger than yours](https://hackmd.io/@Wg20j1S6Q8m8uV7j44GixQ/r1RKQMdt3)
    

%[https://twitter.com/fireship_dev/status/1675359786463031297] 

%[https://youtu.be/Qnpce8hwn58] 

### Astro

<div data-node-type="callout">
<div data-node-type="callout-emoji">🔗</div>
<div data-node-type="callout-text"><a target="_blank" rel="noopener noreferrer nofollow" href="https://astro.build/" style="pointer-events: none">https://astro.build/</a></div>
</div>

%[https://youtu.be/gxBkghlglTg] 

%[https://youtu.be/Sqp5VSqbQOY] 

<div data-node-type="callout">
<div data-node-type="callout-emoji">✅</div>
<div data-node-type="callout-text">優點</div>
</div>

* 由於框架特性，我可以把不需要用 js 的 components 寫成 astro 檔，剩下的檔案就幾乎是確定需要 js 邏輯操作的部分了，方便重點關注
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689217231028/b4e14ea9-1037-4bcb-8160-33fc0a678d6b.jpeg align="center")
    
* 除了產生一般的靜態 html 外，還可以打包成 middleware 給 express、fastify 或線上 server 做 SSR 用，十分聰明的做法
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689216472075/2cdfb4d1-867a-4de9-b5c6-775299affb90.jpeg align="center")
    
* 你學 React 就需要碰 Next，學 Vue 就需要接觸 Nuxt；基於上一條特性，不管你想學 React、Vue 還是 Svelte，你都可以先忽略那些專屬的 SSR framework，直接套到 Astro 上就行，降低學新東西或技術選擇時「要換就得全換」的門檻
    
* 大多數網站沒有 SPA 的必要，用 MPA 還能省掉頁面切換時可能要另外寫重設 state 數值的部分，讓邏輯更單純
    

<div data-node-type="callout">
<div data-node-type="callout-emoji">🤌</div>
<div data-node-type="callout-text">缺點</div>
</div>

* Astro 可以包其他 jsx 檔，但 jsx 不能反包 astro 檔，雖然可以[繞點遠路](https://docs.astro.build/en/core-concepts/framework-components/#can-i-use-astro-components-inside-my-framework-components)，但還是稍嫌可惜（以 React 為例）
    

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">延伸閱讀</div>
</div>

* [Astro 的正式發佈給前端界帶來了什麼？](https://www.readfog.com/a/1677476109768298496)
    
* [Web 框架 Astro 2.0 发布，在静态和动态渲染之外提供了混合渲染能力](https://www.infoq.cn/article/ymygqq5x3i5p6klpgrkf)
    
* [Unlock New Possibilities with Hybrid Rendering](https://astro.build/blog/hybrid-rendering/)
    

%[https://youtu.be/0FsmP9vF7ws] 

## 全端

首先給下面要介紹的東西先做個資訊補充，除了前端 framework 是吃後端的 json 再更新部分 html 外，也有一種是讓後端直接生成部分 html 丟給瀏覽器做局部更新的；好處是前端需要寫的 js 極少，甚至可以把 form validate 直接讓後端處理，不需要 js 做一次 validate，後端再做一次

舉凡 Laravel 的 [Livewire](https://laravel-livewire.com/)、RoR 的 [Hotwire](https://hotwired.dev/)、Phoenix 的 LiveView 都是此類

%[https://youtu.be/6isrz8LI00o] 

### htmx

<div data-node-type="callout">
<div data-node-type="callout-emoji">🔗</div>
<div data-node-type="callout-text"><a target="_blank" rel="noopener noreferrer nofollow" href="https://htmx.org/" style="pointer-events: none">https://htmx.org/</a></div>
</div>

%[https://www.youtube.com/watch?v=r-GSGH2RxJs] 

%[https://youtu.be/9eV62hj21OA] 

<div data-node-type="callout">
<div data-node-type="callout-emoji">✅</div>
<div data-node-type="callout-text">優點</div>
</div>

* 如果你使用的後端 framework 沒有像上述選項有自家的高度整合方案（比如 Django），htmx 會是一個很好的通用方案
    

<div data-node-type="callout">
<div data-node-type="callout-emoji">🤌</div>
<div data-node-type="callout-text">缺點</div>
</div>

* 由於參數遍佈 html，所以功能複雜的頁面在維護上可能會有反效果
    
* 自帶的 [Events](https://htmx.org/events/) 有點雜
    

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">延伸閱讀</div>
</div>

* [Htmx 意外走红，我们从 React“退回去”后：代码行数减少 67%，JS 依赖项从 255 下降到 9](https://www.infoq.cn/article/veskosrskc9xgiyygyku)
    

### Alpine

<div data-node-type="callout">
<div data-node-type="callout-emoji">🔗</div>
<div data-node-type="callout-text"><a target="_blank" rel="noopener noreferrer nofollow" href="https://alpinejs.dev/" style="pointer-events: none">https://alpinejs.dev/</a></div>
</div>

%[https://youtu.be/CPXUsbgv_V0] 

這是由 Livewire 作者所開發的，用来補足不需要與後端互動的部分

<div data-node-type="callout">
<div data-node-type="callout-emoji">✅</div>
<div data-node-type="callout-text">優點</div>
</div>

* 參數量極少，能夠快速上手
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689225240347/0073d9e5-4ff1-4301-a245-263f5c2edf57.jpeg align="center")
    
* 與後端溝通的部分由 htmx、LiveView 這些負責，剩下瑣碎的前端互動可由 Alpine 代勞，兩者結合之後，幾乎不用寫到什麼 js
    

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">延伸閱讀</div>
</div>

* [我们从 Vue 到 Alpine.js 的旅程](https://www.infoq.cn/article/uw1d6tvpxeqw1eke9s7a)
    
* [AlpineJS作者：不上班，一年10w刀](https://zhuanlan.zhihu.com/p/400613204)
    
* [一個小 demo](https://codepen.io/Knovour/pen/OJaQJLx)
    

## 後端

### Nest.js

<div data-node-type="callout">
<div data-node-type="callout-emoji">🔗</div>
<div data-node-type="callout-text"><a target="_blank" rel="noopener noreferrer nofollow" href="https://nestjs.com/" style="pointer-events: none">https://nestjs.com/</a></div>
</div>

%[https://youtu.be/0M8AYU_hPas] 

<div data-node-type="callout">
<div data-node-type="callout-emoji">✅</div>
<div data-node-type="callout-text">優點</div>
</div>

* [Decorator](https://ithelp.ithome.com.tw/articles/10274274) 的運用很漂亮，程式碼看起來很清晰
    

<div data-node-type="callout">
<div data-node-type="callout-emoji">🤌</div>
<div data-node-type="callout-text">缺點</div>
</div>

* 跟 Express、Koa 一樣屬於輕量型的 framework，對於專案結構沒有太嚴格的規劃。若不定義好結構容易跟以前一樣程式碼越多架構越亂
    

<div data-node-type="callout">
<div data-node-type="callout-emoji">💬</div>
<div data-node-type="callout-text">額外補充</div>
</div>

* 若要使用的話，我會傾向於把核心[從 Express 換成 Fastify](https://docs.nestjs.com/techniques/mvc#fastify)，除了 Express 現在是養老模式以外，Fastify 對 template engine 的參數設定的整合也比較好
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689229093554/c6176eda-e276-4204-8621-0096393727b3.jpeg align="center")
    
    Express 就沒法像這樣寫
    
* 如今大部分的 template engine 都沒在更新或是僅有維護了，雖然應該也沒人在用了
    

### Adonis.js

<div data-node-type="callout">
<div data-node-type="callout-emoji">🔗</div>
<div data-node-type="callout-text"><a target="_blank" rel="noopener noreferrer nofollow" href="https://adonisjs.com/" style="pointer-events: none">https://adonisjs.com/</a></div>
</div>

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689231293885/67cb521c-f0a1-411c-b0d8-1d6a71da3fa2.png align="center")

這個 framework 初衷是讓 PHP 用戶方便轉移到 Node，所以大量參考了 Laravel 的結構

<div data-node-type="callout">
<div data-node-type="callout-emoji">✅</div>
<div data-node-type="callout-text">優點</div>
</div>

* 有相對完整的專案結構
    
* 官方有[豐富的教學](https://adocasts.com/)且持續更新
    
* 官方的 [VSCode Extension](https://marketplace.visualstudio.com/items?itemName=jripouteau.adonis-vscode-extension) 功能支援十分豐富
    
* 自帶的 [edge template](https://docs.adonisjs.com/guides/views/introduction) 跟 [framework 的語法糖](https://docs.adonisjs.com/guides/views/components#components-as-tags)結合有不錯的開發體驗
    
* 不是 Express 套皮
    

<div data-node-type="callout">
<div data-node-type="callout-emoji">🤌</div>
<div data-node-type="callout-text">缺點</div>
</div>

* 或許是客群取向關係，純 js 的開發者的關注度不算高
    

<div data-node-type="callout">
<div data-node-type="callout-emoji">💬</div>
<div data-node-type="callout-text">額外補充</div>
</div>

* [目前正開發 6 版中](https://github.com/adonisjs/core/discussions/4184)，想試的可以再等等
    
* 開發者親測，效能與 Fastify 相當
    
    %[https://twitter.com/AmanVirk1/status/1598717428812611584]