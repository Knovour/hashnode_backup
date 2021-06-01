## 個人的 Css 習慣

這邊紀錄一下個人寫 CSS 時的習慣，不是 BEM、ATOMIC 那些命名，只是紀錄程式的排列方式，有些我也還沒嚴格遵守，透過這篇整理來做為往後的參考。

> **不包含 postcss 的部份**

#### 樣式彼此有關聯的做 nesting

忘記從哪篇文看到的，覺得不錯就習慣這樣了。


```
.class {
  position: absolute;
    top: 0;
    left: 0;
    z-index: 10;
}
``` 
```
.class {
  display: flex;
    align-items: center;
    justify-content: center;
  flex: 1;  /* 這部份受上一層 DOM 的影響，所以不做內縮 */
}
``` 
```
.class {
  background-image: '';
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
}
``` 


#### 樣式排列順序

- `content`：有 `::before` 或 `::after` 元件的話，如果有 `counter- `之類會影響 `content` 的值就放在上面
- `position` - `top`、`right`、`bottom`、`left`、`z-index`：如果沒有 `position` 那其他相關的數值就佔這個位置
- `display`
- 與上一層的 `display` 有關聯的值：比如 `flex: 1`
- `width`
- `height`
- `margin`
- `border`
- `padding`
- `background`
- `box-shadow`
- `color`
- 隨意，只是要分好類，比如 `font-` 開頭的放一起。
- `transform`
- `transition` or `animation`

#### 整體樣式如下

```
.class::before {
  content: '';
  position: absolute;
    top: 0;
    z-index: 0;
  display: flex;
    justify-content: center;
    align-items: center;
  flex: 1;
  width: 100px;
  height: 100px;
  margin: 24px;
  border: 1px solid orange;
  padding: 24px;
  background-image: '';
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
  box-shadow: none;
  color: #333;
  /* 隨意 */
  font-size: 12px;
  font-weight: bold;
  line-height: 1.2em;
  /* 隨意 */
  transform: translate(50px);
  transition: all 200ms linear;
}
``` 

有想到其他的再補上，不知道 [stylelint](https://stylelint.io) 能不能搞到這種程度。