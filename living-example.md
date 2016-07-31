#Living Example(实例)
***
##一、Lottery Draw(随机抽奖)
####1.object方法
######思路：若该对象的属性名未定义，标记该属性名，否则重抽。
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
***
####2.array方法
######思路：创建新数组，如果新创建的数组个数小于存放人名这个数组的个数，遍历这个新数组，如果随机抽取的人名等于我这个数组的人名，重新抽，抽完终止，遍历后没有发现重名，则存入新数组，并输出。
```javascript
var array=[];
        var people=["张三","李四","王五","赵柳","虞美人"];
        $(".btn").click(function(){
            LotteryDraw(people,array);
        });
        function LotteryDraw(arr,array){                
            var rand=Math.floor(Math.random()*arr.length);
            var person=arr[rand];
            if(array.length<arr.length){
                for(var i=0;i<array.length;i++){
                    if(array[i]===person){
                        LotteryDraw(arr,array);
                        return;
                    }
                }
                array.push(person);
                console.log(person);            
            }
        }
```
***