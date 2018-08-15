# text
文本框脚本
选择文本
选择（select）事件
```javascript
var textbox = document.forms[0].elements["textbox1"];
    EvenUtil.addHandler(textbox,"select",function(event){
        alert("Text selected"+ textbox.value);
        alert(selectText(textbox,1,4));
    })
