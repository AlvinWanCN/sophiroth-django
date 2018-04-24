
## javascript note

```
<script type="text/javascript">
        function ad() {
            var d = new Date()
            var t = d.toLocaleDateString(); //获得时间
            document.getElementById('clock').innerHTML=d
            {#            alert(t);#}
        }
        setInterval('ad()',1000)
 </script>
 ```

 上面我们在script 里面定义了一个可以通过id clock获得的内容，通过document.getElementById('clock').innerHTML=d条命令可以将d的内容放到使用该id的内部html里。
 而同时我们设置了setInterval('ad()',1000)，也就是每秒钟执行一次那个函数，那d的值每秒钟都会变化一次，那html里的内容也就没秒钟都变一次了。 </br>

 我们也可以替换上面那行为document.getElementById('clock').innerHTML="\<h1>"+d+" <\/h1>"， 拼接一个h1标签的内容。
 ```
 <body>
{#<input type="text " value="aaa" id="clock">#}
<p id="clock"></p>
</body>

```