### 3D动画旋转样式
<ul>
  <li>
    -webkit-transform-style:preserve-3d;//支持子元素的3D效果
  </li>
  <li>
    -webkit-backface-visibiity:hidden;//当元素不面向屏幕时隐藏
  </li>
  <li>
    -webkit-transform:translate(0px,0px) rotateY(180deg);//定义位移以及沿着Y轴旋转
  </li>
  <li>
    onselectstart="return false;";onselectstart的作用是取消鼠标选中蓝色框选效果
  </li>
  <li>
    transiton:
    property:规定设置过度效果的css属性的名称
    duration:规定完成过度效果需要多少秒或者毫秒；
    timing-function:规定速度效果的速度曲线，默认ease；
    delay：定义过度效果延迟多久开始，默认0；
   </li>
</ul>
