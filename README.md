# css-filter详解 #
----------

> 之前项目开发中遇到要把图片模糊的需求，于是google了一把，采用了`filter-blur`来做，后发现`filter`是个好家伙啊，能处理很多图片特效，不仅仅是blur(敢情浏览器是想把自己做成图片处理器了)。再于是从Mozilla的[web技术文档](https://developer.mozilla.org/zh-CN/docs/Web/CSS/filter%E6%BB%A4%E9%95%9C)（尝试翻译成了中文，英文不好请别拍砖）上进一步了解了下filter这个css3新内容，注意此filter非CSS1里的filter属性，而是filter-effects，对应的[W3C规范](http://www.w3.org/TR/filter-effects/)。


废话不多说，先甩个图来看下效果：

 ![](https://raw.githubusercontent.com/lzf0402/css-filter/master/demo/show1.png)

上图展示的是filter众多效果中的一种，即灰度效果。左边的图是原图，右边的图设置了`filter：grayscale(1)`这一属性，如你所见，图片变成了一张灰度图像。



## filter语法 ###





[查看完整demo](http://sandbox.runjs.cn/show/ichzytmc)


【参考资料】



- [http://www.w3.org/TR/filter-effects/#FilterProperty](http://www.w3.org/TR/filter-effects/#FilterProperty)
- [http://www.zhangxinxu.com/wordpress/2013/11/%E5%B0%8Ftip-%E4%BD%BF%E7%94%A8css%E5%B0%86%E5%9B%BE%E7%89%87%E8%BD%AC%E6%8D%A2%E6%88%90%E6%A8%A1%E7%B3%8A%E6%AF%9B%E7%8E%BB%E7%92%83%E6%95%88%E6%9E%9C/](http://www.zhangxinxu.com/wordpress/2013/11/%E5%B0%8Ftip-%E4%BD%BF%E7%94%A8css%E5%B0%86%E5%9B%BE%E7%89%87%E8%BD%AC%E6%8D%A2%E6%88%90%E6%A8%A1%E7%B3%8A%E6%AF%9B%E7%8E%BB%E7%92%83%E6%95%88%E6%9E%9C/)
- [http://css-tricks.com/almanac/properties/f/filter/](http://css-tricks.com/almanac/properties/f/filter/)
- [http://www.w3cplus.com/css3/ten-effects-with-css3-filter](http://www.w3cplus.com/css3/ten-effects-with-css3-filter)