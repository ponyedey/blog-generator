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