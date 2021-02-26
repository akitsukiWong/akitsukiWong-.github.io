title: canvas
date: 2021-02-05 10:10:28
---
<H1>canvas</H1>
    <canvas id="myCanvas" width="200" height="100"></canvas>
    <script type="text/javascript">
        var c = document.getElementById("myCanvas");
        var cxt = c.getContext("2d");
        cxt.fillStyle = "#FF0000";
        cxt.fillRect(0, 0, 150, 75);
    </script>