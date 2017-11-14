## js学习入门
[引用自](https://github.com/rccoder/blog/issues/15)
### 声明变量
- 注意：在JavaScript第一个版本released的的时候`var`这个关键词就是可以使用的。在`ES6（ES 2015`以及之后的版本中出现了`let`和`const`关键词
#### var，let，const区别
1. 根据引用文章，了解到，`var`可以在封闭的函数作用域进行声明，但是如果不在封闭的函数作用域进行声明，这个声明就将是全局的。它没有块级作用域的概念。
2. `let`与`var`区别在于，`let`不仅在函数中封闭，也在块语句封闭，即在`{` 与`}`包裹着的所有语句中。
3. `const`的声明，只能在初始化时赋值给变量，是无法改变被`const`声明的变量的值的。

#### if语法
1. if后跟的条件需要用`(``)`包裹。若true or false后的语句存在多层，应用`{``}`块级符号包裹
#### hash语法
1. 用`[``]`是一种简写，可以省略数组内的变量（从0开始）
#### js语法
1. 
```
div1 = document.createElement('div')
x.appendChild(div1)
```
- 意思为在id为`'x'`的父元素中添加一个`div`元素。
- 这里为什么要叫div1呢，因为这是容器的名字，随便叫什么都可以，无需纠结。
```
index = 0
while(index< keys['length']){
  div1 = document.createElement('div')
  x.appendChild(div1)
  index = index+1
}
```
- 创建三个div
```
index = 0
  while(index< keys['length']){
  div1 = document.createElement('div')
  x.appendChild(div1)
  z = document.createElement('kbd')
  div1.appendChild(z)
  index = index+1
}
```
- 每个div内有一个kbd
```
    index = 0
    while(index< keys['length']){
      div1 = document.createElement('div')
      main1.appendChild(div1)
      index2 = 0
      while(index2<10){
        kbd1 = document.createElement('kbd')
        kbd1.textContent = 'hi'
        div1.appendChild(kbd1)
        index2 = index2+1
      }
      index = index+1
    }
```
- 每个div內生成10个kbd
```
    index = 0
    while(index< keys['length']){
      div1 = document.createElement('div')
      main1.appendChild(div1)
      row = keys[index]
      index2 = 0
      while(index2< row['length']){
        kbd1 = document.createElement('kbd')
        kbd1.textContent = 'hi'
        div1.appendChild(kbd1)
        index2 = index2+1
      }
      index = index+1
    }
```
- 每个div内生成不一样多的kbd


```
    index = 0
    while(index< keys['length']){
      div1 = document.createElement('div')
      main1.appendChild(div1)
      row = keys[index]
      index2 = 0
      while(index2< row['length']){
        kbd1 = document.createElement('kbd')
        kbd1.textContent = row[index2]
        div1.appendChild(kbd1)
        index2 = index2+1
      }
      index = index+1
    }
```
- 不仅更改了生成的div中的kbd数量，并且让每个kbd的内容也根据数组改变。
```
    document.onkeypress = function(zzzzzzz){
      key = zzzzzzz['key']
      website = hash[key]
      console.log(website)
      //location.href = 'http://'+website
      window.open('http://'+website,'_blank')
    }
```
- `function`后的括号内容是随便取得，这是一个hash的名字，包含我们按键的所有信息
- 监听的部位可能是错的，多换对象重试
- 多用`console.log`调试js
- `location.href = 'http://'+website`表示在当前页面打开。
- `window.open`括号内很眼熟吧，就不多说了。
```
        button1 = document.createElement('button')//1
        button1.textContent = '编辑'//2
        button1.id = row[index2]//3
        button1.onclick = function(xxxxxxx){//4
          key = xxxxxxx['target']['id']//5
          p = prompt('请输入您想更改的网址链接')//6
          hash[key] = p//7
        }//8
```
- 创建button，第四，五行告诉我们用户点击了哪个button，并且在第六行编辑网址，更改了hash中的key对应的网址。
- `xxxxxxx.target`表示被用户点击的按钮，不用`button1`是因为它只是一个容器，在二十六个循环中，也只有一个`button1`，只是容器内的值一直在变化。如果写的是`button1`，就会一直调用循环最后`button1`内的值。
- 目前还有问题，用户更改之后再刷新，无法存储用户的更改。
```
    hashInLocalStorage = JSON.parse(localStorage.getItem('uuu') || 'null') 
    if(hashInLocalStorage){
      hash = hashInLocalStorage
    }
```
- `localStorage.setItem('uuu',JSON.stringify(hash))`只要这个hash变了，就把hash存在'uuu'中。也就是把hash备份在uuu这个桶里。
- 上方的代码串作用是每次刷新页面，如果localStorage不为空，就把里面的hash替换掉js里写的hash，实现保存功能。
#### 渐变色
- 需要取最初的和最尾端的颜色，去搜索css Gradient Generator进行渐变色的操作。
- 边框外的边框，用box-shadow。`box-shadow: 0 0 0px 1px red;`这个`0px`是指不让边框模糊，而后的`1px`是让向外延伸1px。如果想再扩展一层，可以写成`box-shadow: 0 0 0 1px red, 0 0 0 2px black;`若在键盘下方再做阴影，则为`box-shadow: 0 0 0 1px red, 0 0 0 2px black,0 3px 0 2px white;`
```
display: inline-flex;
align-items: center;
justify-content: center;
```
- 可令我们做的键盘内的文字局中。
- `kbd1.className = 'key'`改名。
- 由于之前学到，inline元素之间如果有回车，显示出来就会有空格。
#### 让一个元素绝对局中
```
display: flex;
align-items: center;
justify-content: center;
```

#### 如何让main和body的高度占满整个屏幕
- 需要给body一个高度，100vn是屏幕的高度。
#### 背景图
1. 背景图尽量不要太大；
2. 背景图用自适应，`background-size: cover;`
3. `background`有六个样式。
#### 关于logo
- 一般都是在目标网址的/favicon.ico地址
- 如果img的src写作空，就相当于src等于当前页面

#### 若有图标无法显示
```
        if(hash[row[index2]]){
          img1.src = 'http://'+hash[row[index2]] + '/favicon.ico'
        }else{
          img1.src = '//i.loli.net/2017/11/14/5a0ace9e26e8c.gif'
        }
        img1.onerror = function(aaa){
          aaa.target.src = '//i.loli.net/2017/11/14/5a0ace9e26e8c.gif'
        }
```
- 最后行为若有该地址，但是被拒绝访问icon，则也显示我们准备的图标。
#### 如何做到更改地址后，图标一同更改而不用刷新
```
        button1.onclick = function(xxxxxxx){
          button2 = xxxxxxx['target']
          img2 = button2.previousSibling
          key = button2['id']
          p = prompt('请输入您想更改的网址链接')
          hash[key] = p
          img2.src = 'http://'+p + '/favicon.ico'
          img1.onerror = function(aaa){
          aaa.target.src = '//i.loli.net/2017/11/14/5a0ace9e26e8c.gif'
        }
```
- 找到button2对应的img2，也就是点击了这个按钮后，找到对应的图标，然后更改图标的地址。
#### 函数封装
1. 就好比是把x带入到f(x)中一样。
2. 如果在创建元素的同时，还想附带定义这个元素的一些标签，可以如下
```
    function c(tagName,attributes){
      var element = document.createElement(tagName)
      for(var key in attributes){
        element[key] = attributes[key]
      }
    return element
    }
```
- 打个比方，如果我输入了`c('div',{className:'row'})`，这个函数首先会先创建div，然后会把输入的这个hash里的所有元素拿出来，放到创建的元素中去。`key`对应我们输入的hash数组里的这个元素的所有信息，就好比是一一对应生成。
#### for循环和while循环的关系
1. for循环将while循环的三部分提炼出来，也就是定义，条件，以及再加1后为主要部分，用()抱起来，然后中间的其他操作在后面的花括号包裹起来