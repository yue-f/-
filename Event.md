1. 事件流
   1. js  当中的一个特性：`事件冒泡`
      1. 当点击子元素的事件是，如果父级有响应的时候也会执行（称为事件冒泡），
      2. `事件冒泡`顺序 是由 小 -->大 执行事件
      3. 事件流是 事件执行的顺序
   2. 事件捕获
      1. AddEventListener('ev', fn [Boolean, {}])
         1. 第三个参数Boolean： 如果是布尔值： true 是进行捕获执行 ；false 不捕获，默认是false
         2. `事件捕获`顺序是： 由 大 --> 小 执行事件
         3. 第三个参数 还可以传递对象：
            1. Capture: true/false  是否再捕获阶段开启
            2. once： true/false    只给元素绑定一次事件
            3. passive： true/false   阻止取消默认事件， true（不允许阻止）false（允许阻止）
      
      2. removeEventListener('ev', fn [Boolean, {}]) 取消事件监听，绑定的事件函数 --- 必须是命名函数！！! 
   
2. Event 事件对象

   1. Event.target 目标元素、Event.currentTarget 事件源
   2. 事件委托（事件代理）
      1. 事件委托的有点
         1. 可减少需要添加事件绑定的元素
         2. 可给新增DOM元素添加事件（再不刷新页面的情况下）
      2. 事件委托的缺点
         1. 事件处理函数中需要判断事件源增加逻辑复杂度
         2. 祖父级和事件源之间不能有阻止冒泡
   3. mouseenter/mouseleave
      1. Mouseover/mouseout 如果鼠标移入或者移出 子元素 范围也会触发
      2. mouseenter/mouseleave 不受子级元素范围干扰
   4. 事件冒泡
      1. 元素本身有事件，不想执行父级身上的事件 （取消事件冒泡）
         1. Event.cancelBubble=true （ie支持）
         2. Event.stopPropagation()
   5. Event.clientX、Event.clientY 获取鼠标点击的位置（相对于显示区域（可视化区域）的位置）
   6. Event.pageX、Event.PageY 获取鼠标点击的相对于页面的位置
   7. contextmenu  鼠标右键事件
      1. 清除事件默认行为
         1. return false; 只能在直接添加事件的写法下使用，低版本浏览器起作用，高版本不起作用
         2. Event.preventDefault() 阻止浏览器默认行为 -- 标准方法
   8. 键盘事件 
      1. keydown 键盘按下
      2. keyup 键盘抬起
      3. keyCode 键码
      4. key 键值
      5. ctrlKey 判断是否按下ctrl键
   9. 鼠标滚动事件
      1. mouseWheel 事件支持谷歌和ie（-120 滚轮向上， 120 滚轮向下）
      2. DOMMouseScroll 事件支持火狐 （-3 滚轮向上， 3  滚轮向下）
         1. Event.wheelDelta 和 Event.detail 滚轮方向获取
      3. 