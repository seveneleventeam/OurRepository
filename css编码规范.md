#### css编码规范

###### 缩进/空格/换行

- 每个缩进使用4个空格，不允许使用2个空格或tab

  ```js
  //正确
  .seletor{
      margin: 0;
      padding: 0;
  }
  //错误
  .selector{
     margin: 0;
     padding: 0;
  }
  ```

- 选择器与{之间必须包含空格

```js
//正确
.selecter {
}

//错误
.selector{
}
```

- 属性名与之后的 : 之间不允许包含空格，: 与属性值之间必须包含空格

  ```js
  //正确
  margin: 0;
  //错误
  margin:0;
  ```

- 每条规则之间必须包含空行

  ```js
  //正确
  .sample {
      display: flex;
  }
  
  .sample1 {
      display: block;
  }
  //错误
  .sample {
      display: flex;
  }
  .sample1 {
      dispaly: block;
  }
  ```

- 逗号前不允许有空格 , 逗号后必须跟一个空格

  ```js
  //正确
  font-family: Arial, sans-serif;
  
  //错误
  font-family: Arial,sans-serif;
  ```

- SCSS mixin的方法参数括号与 { 之间必须包含一个空格, 各参数间必须有一个空格

  ```js
  //正确
  @mixin color-box($bg-color: $grey-light, $border-color: $grey) {
      background-color: $bg-color;
  } 
  //错误
  @mixin color-box($bg-color:$grey-light,$border-color: $grey) {
      background-color:$bg-color;
  } 
  ```

- ·>、+ 、~·选择器的两边各保留一个空格

  ```js
  //正确
  main > nav {
      padding: 10px;
  }
  
  label + input {
      margin-left: 5px;
  }
  
  input:checked ~ button {
      background-color: #69c;
  }
  
  //错误
  main>nav {
      padding: 10px;
  }
  
  label+input {
      margin-left: 5px;
  }
  
  input:checked~button {
      background-color: #69c;
  }
  ```

- 多个并行选择器使用同一规则，必须换行

  ```js
  //正确
  .a,
  .b,
  .c {
      box-sizing: border-box;
  }
  
  //错误
  .a, .b, .c {
      box-sizing: border-box;
  }
  ```

- 一组变量的定义，尽量以冒号对齐

  ```js
  //推荐
  $link-hover-color        : #29e;
  $hover-color-gray        : #ebebeb;
  $icon-hover-color        : #4d4d4d;
  $btn-hover-color         : #f0f0f0;
  $btn-hover-color-form    : #f9f9f9;
  $btn-hover-color-cancel  : #f63737;
  
  //不推荐
  $link-hover-color : #29e;
  $hover-color-gray : #ebebeb;
  $icon-hover-color : #4d4d4d;
  $btn-hover-color : #f0f0f0;
  $btn-hover-color-form : #f9f9f9;
  $btn-hover-color-cancel : #f63737;
  ```

###### 属性规范

- 属性定义必须另起一行

  ```js
  //正确
  .selector {
      margin: 0;
      padding: 0;
  }
  
  //错误
  .selector { margin: 0; padding: 0; }
  ```

- 属性定义就以分号结尾

  ```js
  //推荐
  .selector {
      margin: 0;
  }
  
  //不推荐
  .selector {
      margin: 0
  }
  ```

- 属性值为0时，省略单位

  ```js
  //正确
  .box {
      padding: 0;
  }
  
  //错误
  .box {
      padding: 0px;
  }
  ```

- 使用16进制表示颜色，颜色值采用小写，#rrggbb的情况简写为#rgb，有透明度的情况使用rgba表示

  ```js
  //推荐
  .box {
      background: rgba(0, 0, 255, .5);
      color: #3ec;
  }
  
  //不推荐
  .box {
      background: white;
      opacity: 0.5;
      color: #33eecc;
  }
  ```

- font-family 属性

  - font-family 不区分大小写，但在同一个项目中，同样的 Family Name 大小写必须统一。

  ```js
  // 正确
  body {
      font-family: Arial, sans-serif;
  }
  
  h1 {
      font-family: Arial, "Microsoft YaHei", sans-serif;
  }
  
  // 错误
  body {   
      font-family: arial, sans-serif;
  }
  
  h1 {    
      font-family: Arial, "Microsoft YaHei", sans-serif;
  }
  ```

- url()中的路径不添加引号

  ```js
  //推荐
  .box {
      background-image: url(../imgs/banner.jpg);
  }
  
  //不推荐
  .box {
      background-image: url('../imgs/banner.jpg');
  }
  ```

- 对于属性值或颜色参数，省略小于 1 的小数前面的 0 （例如，.5 代替 0.5；-.5px 代替 -0.5px）

  ```js
  //推荐
  opacity: .5;
  
  //不推荐
  opacity: 0.5;
  ```

- 无边框设置

  ```js
  // 正确
  .box {
      border: none;
  }
  // 错误
  .box {
      border: 0; // 浏览器会进行多余的渲染，性能不佳
  }
  ```

- 建议尽量不使用 !important (特殊情况除外，如覆盖第三方插件中的样式等)

  

###### 选择器

- 禁止使用ID应用于样式，应使用class

  ```js
  //正确
  .content { 
      display: flex;
  }
  
  //错误
  #content {
  	display: flex;
  }
  ```

- CSS选择器中避免标签名
  选择器应该是准确和有语义的class(类)名，不推荐使用标签选择器。这样会更容易维护, 只需要修改你的标签名，而不是你的class
  从分离的角度考虑,在表现层中不应该分配html标记/语义。

  ```js
  //推荐
  .content {
      display: flex;
  
      > .nav {
          flex: 1;
      }
  }
  
  //不推荐
  .content {
      display: flex;
  
      > nav {
          flex: 1;
      }
  }
  ```

- 尽量精准的选择

  ```js
  //推荐
  .content {
      display: flex;
  
      > .nav {
          flex: 1;
      }
  }
  
  //不推荐
  .content {
      display: flex;
  
      .nav {
          flex: 1
      }
  }
  ```

- 选择器嵌套
  正常的情况下，我们不推荐使用嵌套，如果需要使用嵌套，我们不推荐嵌套超过三层, 如果嵌套超过三层，应该考虑是不是哪里可以使用更精准更语义化的class。不推荐直接使用css的嵌套，而是使用SCSS的嵌套。

  ```js
  //推荐
  .content {
      display: flex;
  
      > .nav {
          flex: 1;
  
          > .item {
              text-align: center;
          }
      }
  }
  
  //不推荐
  .content .nav .item a {
      text-align: center;
  }
  ```

- 在CSS预处理器如LESS 和 SASS 里 media query 推荐直接在选择器的嵌套中使用，有助于保持媒体查询属于的上下文

  ```js
  //推荐
  .content {
      font-size: 1.2rem;
  
      @media screen and (min-width: 767px) {
          font-size: 1rem;
      } 
  }
  
  //不推荐
  .content {
      font-size: 1.2rem;
  }
  @media screen and (min-width: 767px) {
      .content{
          font-size； 1rem;
      }
  }
  ```

- 属性选择器必须使用双引号

  ```js
  //正确
  [class="icon-"] {
      font-size: 1rem;
  }
  
  //错误
  [class='icon-'] {
      font-size: 1rem;
  }
  ```

###### 字重

- font-weight 应该使用数值方式描述

  - CSS 的字重分 100 – 900 共九档，但目前受字体本身质量和浏览器的限制，实际上支持 `400` 和 `700` 两档，分别等价于关键词 `normal` 和 `bold`。

  ```js
  //推荐
  h1 {
      font-weight: 700;
  }
  //不推荐
  h1 {
      font-weight: bold;
  }
  ```

- 变量命名

  - 命名变量的最佳方式就是使用抽象名词，尽量取消名字和值之间的直接关系。
  - 使用'$'开头+ 语义化的变量名。
  - 避免使用无意义的词，如: $calendar-component -> $calendar
  - 推荐变量的意义在前面，功能在后面

  ```js
  // 不推荐
  $red: #F50707;
  $yellow: #B3F724;
  
  // 推荐
  $brand-color: #F50707;
  $accent-color: #B3F724;
  
  // 你可能会使用名称加-color的后缀来命名颜色的变量:
  // Base colors
  $base-color: #333;
  $brand-color: #F50707;
  $brand-80-color: rgba($color-brand, 0.8);
  $accent-color: #B3F724;
  
  // 或者使用header-或者footer-来命名一些特殊的区域：
  // Header
  $header-height: 100px;
  $header-background-color: $color-brand;
  // Footer
  $footer-height: 200px;
  $footer-background-color: #aaa;
  
  // 不推荐
  $z-index-modal
  $padding-body
  // 推荐
  $modal-z-index
  $body-padding
  ```

- 选择器命名

  ```js
  推荐采用BEM方式命名
    // BE模式 block__element：块里的元素，如：nav（block）里的 a 标签(element)
    <nav class="g-nav">
        <a href="#" class="g-nav__item">工作动态</a>
    </nav>
    .g-nav__item {
  
    }
  
    // BM模式 block--modifier: 块元素加修饰符
    // g-nav表示导航的通用样式，g-nav-top表示该导航特有的样式，g-nav--active表示激活的nav
    <nav class="g-nav g-nav-top g-nav--active">
    </nav>
    .g-nav--active {
  
    }
  
    // BEM模式 block__element--modifier nav块里的a元素加上active状态
    <nav class="g-nav">
        <a href="#" class="g-nav__item g-nav__item--active">当前状态</a>
    </nav>
    .g-nav__item--active {
  
    }
  
    BEM只允许出现B__E--M,不允许出现B__B__B__E--M   B__E__E__E--M   B__E--M--M--M
    如果层级过多，可以使用以下方式：
    B__E--M > B__E--M > B__E--M(最多3层B__E--M嵌套)
  
    // 推荐
    <div class="c-card"><!-- B -->
        <div class="c-card__header"><!-- B__E -->
            <h2 class="c-card-title"><!-- B__E > B -->
                <i class="c-card-title__icon--small"></i><!-- B__E > B__E--M -->
                <i class="c-card-title__icon--big"></i><!-- B__E > B__E--M -->
                <span class="c-card-title__text-wrap">Title text here</span><!-- B__E > B__E -->
            </h2>
        </div>
    </div>
    // 推荐
    .c-card {                      // B
  
        &__header {                // B__E
  
            > .c-card-title {      // B__E > B
  
                &__icon--small {   // B__E > B__E--M
  
                }
  
                &__icon--big {     // B__E > B__E--M
  
                }
  
                &__text-wrap {     // B__E > B__E
  
                }
            }
        }
  
    }
  
    // 不推荐
    <div class="c-card">
        <div class="c-card__header">
            <h2 class="c-card__header__title">
                <i class="c-card__header__title__icon"></i>
                <span class="c-card__header__title__text">Title text here</span>
            </h2>
        </div>
    </div>
  
    // 不推荐
    .c-card {
  
        &__header{
  
            &__title {
  
                &__icon {
  
                }
  
                &__text {
  
                }
            }
        }
    }
  
   
  ```

  

- mixins命名

  - 见名知义
  - 小写加中划线，不允许出现大小字母或_

  ```js
  // 不推荐
  @mixin button($background: green) {
  
  }
  // 不推荐
  @mixin buttonBg($background: green) {
  
  }
  // 不推荐
  @mixin button_bg($background: green) {
  
  }
  //推荐
  @mixin button_bg($background: green) {
  
  }
  ```

- 属性缩写

  - 建议在可以使用缩写的情况下，尽量使用缩写

  ```js
  //推荐
  .post {
      font: 12px/1.5 arial, sans-serif;
  }
  
  //不推荐
  .post {
      font-family: arial, sans-serif;
      font-size: 12px;
      line-height: 1.5;
  }
  ```

  