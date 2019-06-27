Example Project:https://codepen.io/no_stack_dub_sack/pen/JbPZvm?editors=0010
FreeCodeCamp-Front End Libraries Projects - Build a Markdown Previewer
Configuration: React+Webpack+Babel

# markPre_with_toolbar
Description: Free Code Camp part3 project2 plus version, not only display markdown file, but also input with toolbar
Example project: https://codepen.io/no_stack_dub_sack/pen/JbPZvm?editors=0010
同样bold图标官网的是fas fa-bold, 为什么它引用fontawesome的时候写的却是 fa fa-bold
bug: textarea里输入完之后，会自动跳到文档末尾

自己编写时遇到的问题：
1. 添加third-party插件时( marked)，configuration不懂原理，只能照搬搜索答案
2. index.js里 document.getElementsByTagName("textarea").value 无法获取textarea值，必须用document.getElementsByTagName("textarea").item(0).value
3. sessionStorageManage 写成funciton会怎样，有别的解决途径吗？
Preview部分编写dangerouslySetInnerHTML时，必须插入function才可以，直接写成一句就会出错
4. handleClick(event)里通过 event.target.id获取点击名称不行，className可以--改为event.currentTarget.id
5. 选中“abc"中”b“,点击 bold button, 需要程序不仅自动添加a**b**c，也要选中b(function selectText())。如果不利用setTimeout()来执行selectText()，selectText()的执行对象就会变成值仍为“abc"的state,而不是已经改变过的state.尝试另一个解决办法：r/reactjs - JavaScript's .setSelectionRange() incompatible with React?
6. **尚未解决（function selectText()）**Google Chrome中，click button之后，textarea会自动跳到文档末尾（firefox不会）-- https://stackoverflow.com/questions/7464282/javascript-scroll-to-selection-after-using-textarea-setselectionrange-in-chrome   这个问题的本质是当textarea.value填充内容后，自动默认是滑动到填充内容末尾的，此时selectText中textarea.focus一运行后，就会自动调到文档末尾  利用链接中第二种方法解决这个问题会导致selectText无效，因为要暂停focus()
