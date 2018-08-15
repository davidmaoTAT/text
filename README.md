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
    
```
取得选择的文本
```javascript
function getSelectedText(textbox){
        // return textbox.value.substring(textbox.selectionStart,textbox.selectionEnd);
        if(typeof textbox.selectionStart == "number"){
            return textbox.value.substring(textbox.selectionStart,textbox.selectionEnd);
        }else if(document.selection){
            return document.selection.createRange().text;
        }
    }
    
```
选择部分文本
```javascript
function selectText(textbox,startIndex,stopIndex){
        if(textbox.setSelectionRange){
            textbox.setSelectionRange(startIndex,stopIndex);
        }else if(textbox.createTextRange){
            var range = textbox.createTextRange;
            range.collapse(true);
            range.moveStart("character",startIndex);
            range.moveEnd("character",stopIndex-startIndex);
            range.select();
            textbox.focus();
        }
    }
```
