# css filter effect #
----------

> 之前项目开发中遇到要把图片模糊的需求，于是google了一把，采用了`filter-blur`来做，后发现`filter`是个好家伙啊，能处理很多图片特效，不仅仅是blur(敢情浏览器是想把自己做成图片处理器了)。再于是从Mozilla的[web技术文档](https://developer.mozilla.org/zh-CN/docs/Web/CSS/filter%E6%BB%A4%E9%95%9C)（尝试翻译成了中文，英文不好请别拍砖）上进一步了解了下filter这个css3新内容，注意此filter非CSS1里的filter属性，而是filter-effects，对应的[W3C规范](http://www.w3.org/TR/filter-effects/)。

## 初探filter特效之灰度 ##
废话不多说，先甩个图来看下效果：

 ![](https://raw.githubusercontent.com/lzf0402/css-filter/master/demo/show1.png)

上图展示的是filter**众多效果中的一种**，即灰度滤镜效果。左边的图是原图，右边的图设置了`filter：grayscale(1)`这一属性（目前还需要加浏览器前缀来使用，关于浏览器支持度[戳这里](https://developer.mozilla.org/zh-CN/docs/Web/CSS/filter%E6%BB%A4%E9%95%9C#Browser_compatibility)），如你所见，图片变成了一张灰度图像。这一功能是否立马触动了你的脑洞，在某些举国悲痛的日子里，需要全站一夜变灰以示哀悼的，就可以用这个属性轻松实现啦。当然，你不得不考虑兼容性，那么问题来了，兼容技术哪家强？

**CSS兼容：**

	.gray { 
	    -webkit-filter: grayscale(100%);
	    -moz-filter: grayscale(100%);
	    -ms-filter: grayscale(100%);
	    -o-filter: grayscale(100%);
	    filter: grayscale(100%);
	    filter: gray; /* IE6\7\8\9 */
	}
css的兼容方式，已基本能兼容绝大多数浏览器了。只是像IE10这种，向上不支持`grayscale`这个新的属性值，向下又抛弃了兼容旧的`filter`，那这种情况，就需要尝试用JS来兼容啦~

**JS兼容：**

	// 引入james大神的灰度处理脚本
	<script src="http://james.padolsey.com/demos/grayscale/grayscale.js"></script>
	// 调用grayscale方法处理图片
	grayscale(imgNodes); //or 处理整个文档：grayscale(document.body)

实现原理：获取图像的base64数据并对每个像素进行灰度转换;如果是整页处理，会把整个页面生成一张灰度图作为body的background-image。

关于灰度滤镜，想了解更多，可以阅[此文](http://www.zhangxinxu.com/wordpress/2012/08/%E5%B0%8Ftip-%E4%BD%BF%E7%94%A8css%E5%B0%86%E5%9B%BE%E7%89%87%E8%BD%AC%E6%8D%A2%E6%88%90%E9%BB%91%E7%99%BD%E7%9A%84/)。

## 认识filter ##
CSS滤镜属性，可以在元素呈现之前，为元素的渲染提供一些效果，如模糊、颜色转移之类的。滤镜常用于调整图像、背景、边框的渲染。目前`Filter Effects Module`还只是W3C的一个草案，浏览器还不完全支持，在使用时需要加浏览器前缀。


#### filter语法 ####
	
	/* 设置滤镜函数（可多个，空格分开） */
	filter: <filter-function> [<filter-function>]* | none
	/* 引入定义了filter效果的svg资源，且可设置特定id的效果 */
	filter: url(svg-url#element-id)

以上的语法，展示了设置filter属性的方式。 filter标准定义了一些已实现预设效果的函数（如`grayscale`、`blur`等）。你也可以自定义特效，将设置了SVG滤镜的xml文件，用URL引入，且可以包含一个锚点来指定一个具体的滤镜效果。filter属性默认值为none,可应用于图像和容器元素，没有继承性。

#### SVG Filter Sources ####
SVG滤镜资源是指以xml文件格式定义的
http://www.w3.org/TR/filter-effects-1/#FilterElement

#### filter-function ####


`grayscale`只是filter滤镜里预置的一个特效函数。



[查看完整demo](http://sandbox.runjs.cn/show/ichzytmc)


【参考资料】



- [http://www.w3.org/TR/filter-effects-1/](http://www.w3.org/TR/filter-effects-1/)
- [http://www.zhangxinxu.com/wordpress/2013/11/%E5%B0%8Ftip-%E4%BD%BF%E7%94%A8css%E5%B0%86%E5%9B%BE%E7%89%87%E8%BD%AC%E6%8D%A2%E6%88%90%E6%A8%A1%E7%B3%8A%E6%AF%9B%E7%8E%BB%E7%92%83%E6%95%88%E6%9E%9C/](http://www.zhangxinxu.com/wordpress/2013/11/%E5%B0%8Ftip-%E4%BD%BF%E7%94%A8css%E5%B0%86%E5%9B%BE%E7%89%87%E8%BD%AC%E6%8D%A2%E6%88%90%E6%A8%A1%E7%B3%8A%E6%AF%9B%E7%8E%BB%E7%92%83%E6%95%88%E6%9E%9C/)
- [http://css-tricks.com/almanac/properties/f/filter/](http://css-tricks.com/almanac/properties/f/filter/)
- [http://www.w3cplus.com/css3/ten-effects-with-css3-filter](http://www.w3cplus.com/css3/ten-effects-with-css3-filter)