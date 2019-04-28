---
title: css3做banner
date: 2018-05-12 15:02:56
tags: css
---

也是面试时候遇到的问题,回来随便弄了一个

在线地址：<http://dflxm.oschina.io/code/>

代码

```
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title>css3写一个banner</title>
		<style type="text/css">
			*{
				margin: 0;
				padding: 0;
			}
			ul li {
				list-style: none;
			}
			.banner-box {
				position: relative;
				width: 400px;
				height: 200px;
				overflow: hidden;
			}
			.banner {
				width: 1600px;
				position: absolute;
				left: 0;
				animation-name: bannerMove;
				animation-duration: 8s;
				animation-iteration-count: infinite;
			}
			@keyframes bannerMove {
				0%, 30% {
					left: 0;
				}
				35%, 65% {
					left: -400px;
				}
				70%, 99% {
					left: -800px;
				}
				100% {
					left: -1200px;
				}
			}
			.banner li {
				float: left;
				width: 400px;
				height: 200px;
			}
		</style>
	</head>
	<body>
		<div class="banner-box">
			<ul class="banner">
				<li style="background-color:#f90;"></li>
				<li style="background-color:#f00;"></li>
				<li style="background-color:#9f0;"></li>
				<li style="background-color:#333;"></li>
			</ul>
		</div>
	</body>
</html>
```