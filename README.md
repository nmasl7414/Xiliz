<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>翻牌</title>
    <script src="jquery-3.5.1.min.js"></script>
</head>

<style>
    
  
    #beg {
  text-decoration:none;
  color:#FFF;
}
#beg {
  width:calc(20vw + 6px);
  height:calc(8vw + 6px);
  background-image: linear-gradient(90deg, rgb(187, 10, 187) 0%, rgb(209, 114, 228) 49%, rgb(158, 95, 173) 80%, rgb(228, 36, 132) 100%);
  border-radius:5px;
  display:flex;
  align-items:center;
  justify-content:center;
  text-transform:uppercase;
  font-size:3vw;
  font-weight:bold;
}
#beg {
  content:attr(alt);
  width:235px;
  height:200px;
  background-color:#912d2d;
  display:flex;
  align-items:center;
  justify-content:center;
}
#beg {
  animation:slidebg 4s linear infinite;
}

@keyframes slidebg {
  to {
    background-position:25.5vw;
  }
}
    #beg{
        margin:10px;
  background-color:#191919;
  min-height:40px;
  display:flex;
  align-items:center;
  justify-content:center;
  font-family:Helvetica,Sans-serif;
        
    }
    div{
       
      height: 350px;
        
  
    }
    .upcard{
        color: rgb(250, 214, 11);
        background-image:url("MOON.pngㄋ");
        height: 90px;
        width: 70px;
        margin:20px;
        background-color: rgb(0, 0, 0)
    }
    .downcard{
        color: rgba(2, 81, 95, 0.986);
        height: 90px;
        width: 70px;
        margin: 20px;
        background-color: rgb(255, 255, 255)
       
    }
</style>
<body background="NightStar.png">
    
    <div>
        <input type="button" value="" class="upcard">
        <input type="button" value="" class="upcard"><br>
        <input type="button" value="" class="upcard">
        <input type="button" value="" class="upcard">
        
    </div>
    <div>
        <input type="button" value="" class="downcard">
        <input type="button" value="" class="downcard"><br>
        <input type="button" value="" class="downcard">
        <input type="button" value="" class="downcard">
    </div>
    <input type="button" value="開始翻牌" id="beg">

</body>
<form>
    <a href="ddssaa.html">
        <input type="button" value="前往九宮格">
    </a>
</form>
</html>

<script>
    
    x=[1,2,3,4]
    var turn="up";
    justclickdata="";
    rightclick=0
    function valClear(){
        for(i=0;i<4;i++){
            $(".upcard:eq("+i+")").val("")
            $(".downcard:eq("+i+")").val("")
        }
    }
    $("#beg").click(function(){
        turn="up"
        x.sort(function(){
            return Math.random()<0.5?1:-1;
        });
        for(i=0;i<4;i++){
            $(".upcard:eq("+i+")").val(x[i])
            $(".upcard:eq("+i+")").data("num",x[i])
        }
        x.sort(function(){
            return Math.random()<0.5?1:-1;
        });
        for(i=0;i<4;i++){
            $(".downcard:eq("+i+")").val(x[i])
            $(".downcard:eq("+i+")").data("num",x[i])
        }
        setTimeout("valClear()",2000);
    });
        $(".upcard").click(function(){
            if(turn="up"){
                $(this).val($(this).data("num"));
                turn="down"
                justclickdata=$(this).data("num");
            }
        });
        $(".downcard").click(function(){
            if(turn="down"){
                if($(this).data("num")==justclickdata){
                    $(this).val($(this).data("num"));
                turn="up"
                rightclick++
                    if(rightclick==4){
                       alert("YOU WIN~~~")
                    }
            }else
            {
                for(i=0;i<4;i++){
                $(".upcard:eq("+i+")").val("")
                $(".downcard:eq("+i+")").val("")
                  }
                  turn="up";
                    rightclick=0
            }
                  }
        });
</script>

