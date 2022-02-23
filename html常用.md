# HTML

# Jquery

## 输入框

```js
//取值
var appmc = $('#appmc').val();
//赋值
$('#appmc').val("123");
```

## 多选框

```js
//取值
var yxhj_str = "";
var yxhj_arr = [];
$('input[name="yxhj"]:checked').each(function () {
    yxhj_arr.push($(this).val())
});
yxhj_str = yxhj_arr.join(",");
//赋值   result["yxhj"]='1,2,3'
$('input[name="yxhj"]').each(function () {
    var value = $(this).val();
    if (result["yxhj"].indexOf(value)!==-1){
        $(this).attr("checked",true);
    }
});
```

## 单选框

```js
//取值
var zt = $("input[name='zt']:checked").val()
//赋值 result["zt"]='1'
$('input[name="zt"]').each(function () {
    var value = $(this).val();
    if (result["zt"].indexOf(value)!==-1){
        $(this).attr("checked",true);
    }
});
```

## 下拉框

```js
//取值
var dmdjqk = $("#dmdjqk").val();
//赋值  result["dmdjqk"]='1'
$("#dmdjqk").find("option[value='"+result["dmdjqk"]+"']").attr("selected",true);
```

# JS

## 时间戳转字符串

```js
function timestampToTime(timestamp) {
    var date = new Date(timestamp);
    var Y = date.getFullYear() + '-';
    var M = (date.getMonth() + 1 < 10 ? '0' + (date.getMonth() + 1) : date.getMonth() + 1) + '-';
    var D = (date.getDate() < 10 ? '0' + date.getDate() : date.getDate()) + ' ';
    var h = (date.getHours() < 10 ? '0' + date.getHours() : date.getHours()) + ':';
    var m = (date.getMinutes() < 10 ? '0' + date.getMinutes() : date.getMinutes()) + ':';
    var s = date.getSeconds() < 10 ? '0' + date.getSeconds() : date.getSeconds();
    return Y + M + D + h + m + s;
}
```

