### 创建二维数组
方法一：
new Array(x).fill().map(() => new Array(y).fill(0))

方法二：
Array.from(new Array(x), () => new Array(y).fill(0))

————————————————

方法三：（不要使用）
new Array(x).fill(new Array(y).fill(0))
但注意，当一个对象别传递给fill方法时，填充数组的是这个对象的引用。即二维数组的第一个维度中的每一个数组都指向同一个引用，如果向第一个维度中的任一元素执行push，则每一个二维中都会多一个元素。

### apply, call, bind
apply 、 call 、bind 三者都是用来改变函数的this对象的指向的；
apply 、 call 、bind 三者第一个参数都是this要指向的对象，也就是想指定的上下文；
apply 、 call 、bind 三者都可以利用后续参数传参；
bind 是返回对应函数，便于稍后调用；apply 、call 则是立即调用 。

call 需要把参数按顺序传递进去，而 apply 则是把参数放在数组里。比如：
func.call(this, arg1, arg2);
func.apply(this, [arg1, arg2])

### 数组去重的方法
一、利用ES6 Set去重（ES6中最常用）
function unique (arr) {
  return Array.from(new Set(arr))
}

// [...new Set(arr)] 


var arr = [1,1,'true','true',true,true,15,15,false,false, undefined,undefined, null,null, NaN, NaN,'NaN', 0, 0, 'a', 'a',{},{}];
console.log(unique(arr))
 //[1, "true", true, 15, false, undefined, null, NaN, "NaN", 0, "a", {}, {}]
不考虑兼容性，这种去重的方法代码最少。这种方法还无法去掉“{}”空对象，后面的高阶方法会添加去掉重复“{}”的方法。


二、利用indexOf去重
function unique(arr) {
    if (!Array.isArray(arr)) {
        console.log('type error!')
        return
    }
    var array = [];
    for (var i = 0; i < arr.length; i++) {
        if (array .indexOf(arr[i]) === -1) {
            array .push(arr[i])
        }
    }
    return array;
}

var arr = [1,1,'true','true',true,true,15,15,false,false, undefined,undefined, null,null, NaN, NaN,'NaN', 0, 0, 'a', 'a',{},{}];
console.log(unique(arr))
   // [1, "true", true, 15, false, undefined, null, NaN, NaN, "NaN", 0, "a", {…}, {…}]  //NaN、{}没有去重

三、利用hasOwnProperty
function unique(arr) {
    var obj = {};
    return arr.filter(function(item, index, arr){
	// typeof item + item 是数组项类型与值构成的字符串
        return obj.hasOwnProperty(typeof item + item) ? false : (obj[typeof item + item] = true)
    })
}
    var arr = [1,1,'true','true',true,true,15,15,false,false, undefined,undefined, null,null, NaN, NaN,'NaN', 0, 0, 'a', 'a',{},{}];
        console.log(unique(arr))
// [1, "true", true, 15, false, undefined, null, NaN, "NaN", 0, "a", {…}]   //所有的都去重了（仅可以去重空对象）

### CLOSURE（闭包）

Closure is a behavior of functions and only functions. If you aren't dealing with a function, closure does not apply. An object cannot have closure, nor does a class have closure (though its functions/methods might). Only functions have closure.

Each of those references from the inner function to the variable in an outer scope is called a closure. 


Definition:
Closure is observed when a function uses variable(s) from outer scope(s) even while running in a scope where those variable(s) wouldn't be accessible.

The key parts of this definition are:
* Must be a function involved
* Must reference at least one variable from an outer scope
* Must be invoked in a different branch of the scope chain from the variable(s)


We explored two models for mentally tackling closure:
* Observational: closure is a function instance remembering its outer variables even as that function is passed to and invoked in other scopes.
* Implementational: closure is a function instance and its scope environment preserved in-place while any references to it are passed around and invoked from other scopes.
Summarizing the benefits to our programs:
* Closure can improve efficiency by allowing a function instance to remember previously determined information instead of having to compute it each time.
* Closure can improve code readability, bounding scope-exposure by encapsulating variable(s) inside function instances, while still making sure the information in those variables is accessible for future use. The resultant narrower, more specialized function instances are cleaner to interact with, since the preserved information doesn't need to be passed in every invocation.

Reference: https://github.com/getify/You-Dont-Know-JS/blob/2nd-ed/scope-closures/ch7.md

###  高亮标签外关键字
``` js
/** 
 * 高亮标签外关键字
 * str为html采用此方法
 * @param {String}
 */
export function highlightHtml(str, keyword) {
  // 匹配标签之间字符
 //  (.*?)匹配标签间的字符，?表示惰性模式，只匹配1个
  let markReg = new RegExp("(>+)(.*?)(<+)", "ig");
  // 匹配标签间字符中的keyword
  let wordReg = new RegExp(keyword, "g");
  // 高亮关键字值
  let replaceString = `<span class="primary">${keyword}</span>`;

  return str.replace(markReg, function(keyword, $1, $2, $3) {
    return $1 + $2.replace(wordReg, replaceString) + $3
  });
}
```

### Embed PDF File in HTML
Use the following code to embed PDF file in the HTML web page.

``` html
<embed src="files/Brochure.pdf" type="application/pdf" width="100%" height="600px" />
```

Now we will show how you can control the PDF document view on the web page. Using parameters in URL, you can specify exactly what to display and how to display PDF document.
The following parameters are commonly used to embed PDF file in HTML or open in the browser.
* page=pagenum – Specifies a number (integer) of the page in the document. The document’s first page has a pagenum value of 1.
* zoom=scale – Sets the zoom and scroll factors, using float or integer values. For example, a scale value of 100 indicates a zoom value of 100%.
* view=Fit – Set the view of the displayed page.
* scrollbar=1|0 – Turns scrollbars on or off.
* toolbar=1|0 – Turns the toolbar on or off.
* statusbar=1|0 – Turns the status bar on or off.
* navpanes=1|0 – Turns the navigation panes and tabs on or off.
* 

Specifying Parameters in a URL
You can specify multiple parameters in URL. Each parameter should be separated with either an ampersand (&) or a pound (#) character. Actions are executed from left to right and later actions will override the previous actions.
URL with parameters looks like the following.

http://example.com/doc.pdf#Chapter5
http://example.com/doc.pdf#page=5
http://example.com/doc.pdf#page=3&zoom=200,250,100
http://example.com/doc.pdf#zoom=100
http://example.com/doc.pdf#page=72&view=fitH,100

### 密码正则表达式
写出正确的正则表达式，实现密码“8位以上的字母，数字的组合至少包含一位大写字母以及一位数字”

【分析】
 *预判：*
Step1：预判字符串不全是数字和小写字母
(?![0-9a-z]+$) 可能包含大写或特殊符号
Step2：预判字符串不全是字母
(?![a-zA-Z]+$) 可能包含数字或特殊符号
Step3：[0-9a-zA-Z]{8,} 只能用数字和字母
(?![0-9a-z]+$)(?![a-zA-Z]+$)[0-9a-zA-Z]{8,}
结果：
/^(?![0-9a-z]+$)(?![a-zA-Z]+$)[0-9a-zA-Z]{8,}$/

### 正则匹配电话号码
const regExp = /(^1[3456789]\d{9}$)|(^((010|02\d|\d{4})-)?\d{7,8}$)|(^((010|02\d|\d{4})-)?\d{7,8}(-\d{1,4})$)/;
regExp.test(phoneNum);

/^1[3456789]\d{9}$/		匹配13-19开头，以9位数字结尾的11位手机号
/^((010|02\d|\d{4})-)?\d{7,8}$/ 	匹配010/02*/四位区号开头-7～8位数字结尾座机号
/^((010|02\d|\d{4})-)?\d{7,8}(-\d{1,4})$/ 	匹配以1～4位数字分机号结尾的座机号

❗️正则表达式不要加全局匹配符号g，因为当校验一组电话号码时，每次匹配校验后会记录lastIndex，下次匹配校验从这个lastIndex索引开始

### 使用正则表达式的方法
	
| 方法　| 描述　|
|--|--|
|exec |	一个在字符串中执行查找匹配的RegExp方法，它返回一个数组（未匹配到则返回 null）。|
|test	| 一个在字符串中测试是否匹配的RegExp方法，它返回 true 或 false。|
|match	| 一个在字符串中执行查找匹配的String方法，它返回一个数组，在未匹配到时会返回 null。|
|matchAll |	一个在字符串中执行查找所有匹配的String方法，它返回一个迭代器（iterator）。|
|search	| 一个在字符串中测试匹配的String方法，它返回匹配到的位置索引，或者在失败时返回-1。|
|replace	| 一个在字符串中执行查找匹配的String方法，并且使用替换字符串替换掉匹配到的子字符串。|
|split	| 一个使用正则表达式或者一个固定字符串分隔一个字符串，并将分隔后的子字符串存储到数组中的 String 方法。|

exec(), test()为正则方法，其他5种为字符串方法。

### 数组去重合并
``` js
function combine(){
    let arr = [].concat.apply([], arguments);  //没有去重复的新数组
    return Array.from(new Set(arr));
}
```

数组迭代方法
every, some满足函数条件返回true

filter 返回满足函数条件构成的数组
map返回函数调用后的数组

forEach对每一项运行函数，无返回值

### window.close 不生效
``` js
window.opener = null;
window.open(' ', '_self');   // 字符串’ ’有空格
window.close();
```