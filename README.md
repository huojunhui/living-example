#Living Example
##一、Lottery Draw(随机抽奖)
####1.object方法
######思路：若该对象的属性名未定义，
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Lottery draw</title>
    <style type="text/css">
        *{
            padding:0;
            margin:0;
        }
        .btn{
            display:block;
            width: 50px;
            height: 50px;
            margin:0 auto;
        }
    </style>
</head>
```
```javascript
        var obj={};
        var people=["张三","李四","王五","赵柳","虞美人"];
        $(".btn").click(function(){
            LotteryDraw(people,obj);
        });
        function LotteryDraw(arr,obj){              
            var rand=Math.floor(Math.random()*arr.length);
            var person=arr[rand];
            if(obj[person]===undefined){
                obj[person]=1;
                console.log(person);
            }else if(objLength(obj)<arr.length){
                LotteryDraw(arr,obj);
            }
            obj={};
        }
        function objLength(object){
            var n=0;
            for(var i in object){
                n++;
            }
            return n;
        }
```
###2.array方法