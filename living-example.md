#Living Example(实例)
####[返回目录](https://github.com/huojunhui/living-example)
***
##一、Lottery Draw(随机抽奖)
####1.object方法
[open](../exercise/1-lottery-draw1.html)
######思路：若该对象的属性名未定义，标记该属性名，否则重抽。
```javascript
<script>
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
</script>
```
####2.array方法
[open](../exercise/1-lottery-draw2.html)
######思路：创建新数组，如果新创建的数组个数小于存放人名这个数组的个数，遍历这个新数组，如果随机抽取的人名等于我这个数组的人名，重新抽，抽完终止，遍历后没有发现重名，则存入新数组，并输出。
```javascript
<script>
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
</script>
```
***
##二、imageSwitcher(切换图片)
####1.jquery方法(改变图片来源)
[open](../exercise/imageSwitcher.html)
######思路：用数组存放图片来源，好处是图片名字可以任意取。点击索引时切换相应图片来源。
```javascript
<script>
    var src1=[
        "images/1.jpg",
        "images/2.jpg",
        "images/3.jpg",
        "images/4.jpg",
        "images/5.jpg"
        ];
    $(".list li").click(function(){
        var ind=$(this).index();
        $(".image").attr("src",src1[ind]);
    });
</script>
```
***
##三、viewpager(翻页效果)
####1.jquery方法
######思路：点击时li也随之改变。小盒子套大盒子，改变大盒子的margin   -top;
```javascript
<script>
    $("#list li").click(function(){
        var ind=$(this).index();
        console.log(ind)
        $(".img1").animate({"margin-top":-600*ind});
        $("#list li").eq(ind).css("background-color","white").siblings().css("background-color","red");
    })
    $("#images .img1 img").click(function(){
        var ind=$(this).index();
        if(ind<3){
            $(".img1").animate({"margin-top":-600*(ind+1)});
            $("#list li").eq(ind+1).css("background-color","white").siblings().css("background-color","red");
        }else if(ind===3){
            $(".img1").animate({"margin-top":0});
            $("#list li").eq(0).css("background-color","white").siblings().css("background-color","red");
        }     
    })
</script>  
```
***
##四、arithmetic(算法)
####1.元素互换
######思路：var t=a;a=b;b=t;
####2.冒泡排序(bubbleSort)
######思路：相邻者有序，i控制行，j控制列。
```javascript
<script>
function bubbleSort(array){
    for(var i=array.length;i>1;i--){
        for(var j=0;j<i-1;j++){
            if(array[j]>array[j+1]){
                var t=array[j];
                array[j]=array[j+1];
                array[j+1]=t;
            }
        }
    } 
    return array;
}
</script>
```
***
##五、将数组中数据更新到表格
######思路：i层控制tr，j层控制td..遍历二维数组，数组中的元素就是td
的文本节点(text)，tr添加td(append)
```javascript
<body>
    <table></table>
    <script src="script/jquery.js"></script>
    <script>
        var studentsList=[
            {name:"zhangsan",age:13,sex:"female"},
            {name:"lisi",age:18,sex:"male"},
            {name:"wangwu",age:20,sex:"male"},
        ];
        for(var i in studentsList){
            $tr=$("<tr>");//创建tr;
            for(var j in studentsList[i]){
                $td=$("<td>");
                var text=studentsList[i][j];
                $td.text(text);
                $tr.append($td);
            }
            $("table").append($tr);
        }
    </script>
</body>
</script>
```