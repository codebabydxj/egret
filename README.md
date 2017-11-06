# egret
egret白鹭引擎的学习心得总结

1.纹理集实际上就是将一些零碎的小图放到一张大图当中。游戏中也经常使用到纹理集。使用纹理集的好处很多，我们通过将大量的图片拼合为一张图片从而减少网络请求，原先加载数次的图片资源现在加载一次即可。同时，在引擎渲染的时候也会减少IO读取，从而提高性能。

2.只要发生事件，Flash就会调度事件对象。如果事件目标不在显示列表中，则Flash Player或AIR将事件对象直接调度到事件目标。例如，Flash Player将process事件对象直接调度到URLStream对象。但是，如果事件目标在显示列表中，则FlashPlayer将事件对象调度到显示列表，事件对象将在显示列表中穿行，直到到达事件目标。

3.TypeScript基本数据类型：Boolean，Number，String，Array，Enum，Any，Void。

4.Egret GUI系统的特性：

(1).皮肤分离机制:皮肤分离机制就是把GUI控件的外观与逻辑处理分离开来。控件的逻辑代码只负责动态的逻辑处理，如事件监听和数据刷新。而皮肤部件只负责控件的外观，如实例化子项，设置控件的样式和布局等静态的属性。

(2).失效验证机制

(3).自适应流式布局

5.Egret中的事件机制：事件发送者.addEventListener(事件类型，侦听器，this)；

6.Egret命令行介绍

(1)build:构建制定项目，编译制定项目的TypeScript文件

(2)create:创建新项目

(3)create_app：从h5游戏生成app

(4)create_mainfest:在工程目录下生成manifest.json清单文件

(5)info:获取Egret信息

(6)publish:发布项目，使用GooleClosureCompiler压缩代码

(7)startserver:启动HttpServer，并在默认浏览器中打开指定项目。

(8)upgrade:升级项目代码

7.加载游戏资源：

RES.addEventListener(RES.ResourceEvent.CONFIG_COMPLETE,this.onConfigComp,this);

RES.loadConfig("resource/resource.json","resource/");

8.核心显示类

Egret中一共封装了7个显示相关的核心类，一个接口，具体继承结构如下：

(1)DisplayObject：显示对象基类，所有显示对象均继承自此类

(2)Bitmap:位图，用来显示图片

(3)Shap:用来显示矢量图，可以使用其中的方法绘制矢量图形

(4)DisplayObjectContainer:显示对象容器接口，所有显示对象容器均实现此接口

(5)Sprite:轻量级显示容器

(6)Stage:舞台类

(7)TextField:文本类

(8)TextInput:输入文本类

9.显示对象的全部可视属性：

(1)alpha:透明度

(2)width:宽度

(3)height:高度

(4)rotation:旋转角度

(5)scaleX:横向缩放

(6)scaleY:纵向缩放

(7)skewX:横向斜切

(8)skewY:纵向斜切

(9)visible:是否可见

(10)x:X轴坐标值

(11)y:Y轴坐标值

10.var isHit:boolean=shp.hitTestPoint(10,10);

hitTestPoint这个方法是执行一次碰撞检测，检测的对象是当前shp是否与坐标为（10,10）的点发生了碰撞。如果发生碰撞，则方法返回true，如果没有发生碰撞，则返回false。

11.若要确定对象相对于全局舞台坐标的位置，可以使用任何显示对象的globalToLocal（）方法将坐标从全局（舞台）坐标转换为本地（显示对象容器）坐标。同样也可以使用DisplayObject类的localToGlobal()方法将本地坐标转换为舞台坐标。

12.通过触摸来移动显示对象，当手指按到屏幕时监听TOUCH_MOVE事件，然后每次手指移动时都会调用此函数，使拖到的对象跳到手指所在的x，y坐标。当手指离开屏幕后取消监听，对象停止跟随。

13.如果显示对象太大，不能在要显示它的区域中完全显示出来，则可以使用scrollRect属性定义显示对象的可查看区域。此外，通过更改scrollRect属性，可以使内容左右平移或上下移动。

14.被缓存的对象依然可以更新它内部的对象，这时将自动重新创建缓存。将显示对象的cacheAsBitmap属性设置为true就会把显示对象缓存成位图形式。DisplayObject类的scrollRect属性与使用cacheAsBitmap属性的位图缓存有关。只有将cacheAsBitmap设置为true时，才能看到scrollRect属性带来的性能优势。

15.每个显示对象都有blendMode属性，可以将其设置为下了混合模式（egret.BlendMode.NORMAL,egret.BlendMode.ADD,egret.BlendMode.ERASE）之一。

16.如要指明一个显示对象将是另一个显示对象的遮罩，请将遮罩对象设置为被遮罩的显示对象的mask属性。

17.Egret v2.5.0Game扩展库包含下面的API：

(1)egret.MovieClip：影片剪辑，可以通过影片剪辑播放序列动画。

(2)egret.MovieClipData:使用MovieClipData类。

(3)egretl.MovieClipDataFactory:使用MovieClipDataFactory类，可以生成MoiveClipData对象用于创建MovieClip。

(4)egret.MovieClipEvent:当动画的当前侦有事件，将调度MovieClipEvent对象。帧事件类型MovieClipEvent.FRAME_LABEL.

(5)egret.ScrollView:ScrollView是用于滑动的辅助类，将一个显示对象传入构造函数即可。

(6)egret.URLLoader:URLLoader类以文本、二进制数据或URL编码变量的形式从URL下载数据

(7)egert.URLLoaderDataFormat:URLLoaderDataFormat类提供了一些用于指定如何接受已下载数据的值。

(8)egert.URLRequest:URLRequest类可捕获单个HTTP请求中的所有信息。

(9)egret.URLRequestHeader:HRLRequestHeader对象封装了一个HTTP请求标头并由一个名称/值对组成。

(10)egret.URLRequestMethod:URLRequestMethod类提供了一些值，这些值可指定在将数据发送到服务器时,URLRequest对象应使用POST方法还是GET方法

(11)egret.URLVariables:使用URLVariable类可以在应用程序和服务器之间传输变量。

(12)egret.MainContext:是游戏的核心平台接口

18.Egret v2.5.0Tween扩展库API

(1)egret.Ease:缓存函数集合，使用不同的缓存函数使得动画按照对应的方程进行。

(2)egret.Tween:Tween是Egret的动画缓存类

19.粒子系统的主要类职责：

(1)particle：粒子类，定义了粒子的基础参数，如：xy坐标、旋转、缩放等。

(2)ParticleSystem:粒子库基类，包括粒子库所必须的一些方法

(3)GravityParticle:继承自Particle，定义了GravityParticle所需要的各项参数

(4)GravityParticleSystem:继承自ParticleSystem,通过传入的配置实现重力粒子系统

20.egret.Event.COMPLETE:版本控制加载完成时抛出。

21.egret.IOErrorEvent.IO_ERROR 版本控制加载失败时抛出。

22.gret资源加载机制：对于外部资源，就要使用资源加载机制。在Flash中是用Loader或URLoader。Egret中也提供了Loader的类似实现，即：RES.ResourceLoader。（注意ResourceLoader的命令空间是RES，而不是egret）。但Egret得封装更“上层”一些，您甚至都无需直接接触ResourceLoader这个类，而是直接使用Egret提供的，结合外部配置文件的资源管理和加载方式。__define

23.精灵表单：在使用位图时，还经常用到“精灵表单”，即spritesheet,精灵表单就是把若干张小图集合到一张大图上，这样对资源加载，控制，减少请求数等方面都很有益处。制作spritesheet的工具也有很多，比如TexturePacker，FlashCS6也增加了对spritesheet的支持，您可以选择适合自己的工具。在Egret框架中当然也可以使用spritesheet。

24.MoiveClip(动画片段):MoiveClip相当于一个小的动画片段，其中包含了多个单独的帧（图片），在连续播放时，就形成了动画（或小电影片段）的效果。MoiveClip在Flash中经常使用，在Egret中也可以进行使用。

25.Egret文本：文本是创建游戏时的必要要素。要了解Egret文本，需要先了解Egret中“DisplayObject(显示对象)”的概念。

26.Egret显示对象：“显示对象”，是可以在舞台上显示的对象。可以显示的对象，即包括可以直接看见的图像、文字、视频、图片等，也包括不能看见但真实存在的显示对象容器。

27.文本类型

(1)普通文本：能够正常的显示各种文本，文本内容可以被程序设置，是常用的文本类型。

(2)输入文本：可以被用户输入的文本，常用于登陆中的输入框或者游戏中的聊天窗口。

(3)位图文本：使用位图文字来渲染的文本，常用于游戏中需要加特殊字体效果的文本。

28.egret.localStorage.全局函数。

显示继承的公共方法。

(1)clear():void 将所有数据清空

(2)getItem(key:string):string 读取数据

(3)removeItem(key:string):void 删除数据

(4)setItem(key:string,value:string):boolean 保存数据

29.Egret中的物体主要有两种：

(1)显示物体

(2)显示容器：显示容器可以理解为“可见显示物体”的一个载体，显示容器在场景中是不可见的。

30.显示物体属性

(1)alpha:透明度

(2)width:宽度

(3)height:高度

(4)rotation:旋转角度

(5)scaleX:横向缩放

(6)scaleY:纵向缩放

(7)skewX:横向斜切

(8)skewY:纵向斜切

(9)visible:是否可见

(10)x:X轴坐标值

(11)y:Y轴坐标值

31.Egret中可以直接使用程序来绘制一些简单的图形，这些图形在运行时都会进行实时绘图。要进行绘图操作，我们需要使用Graphics这个类。但并非直接使用。一些显示对象中已经包含了绘图方法，我们可以直接调用这些方法来进行绘图。Graphics中提供的绘图方法共有四种:a.绘制矩形，b.绘制圆形C.绘制直线D.绘制曲线。

32.在Egret中，我们有三种类型的文本可以选择，分别为“普通文本”、“输入文本”和“位图文本”。这些不同类型的文本在不同的场景中使用。对于不同类型的文本，其操作方式可能会有所不同。三种类型的文本特点如下：

(1)普通文本:能够正常的显示各种文本，文本内容可以被程序设置，最为常见的文本类型。

(2)输入文本：可以被用户输入的文本，常用于登陆中的输入框或者游戏中的聊天窗口。

(3)文图文本：使用位图文字来渲染的文本，常用于游戏中需要加特殊字体效果的文本。

33.动画：

(1)Tween缓存动画:通常情况下，游戏中或多或少都会带有一些缓存动画。例如界面弹出，或者道具飞入飞出的特效等等。在制作这些缓存动画的时候我们仅仅希望简单的
办法实现这种移动或者变形缩放的效果。Egret中的Tween缓存动画类就为我们提供了相关的功能。

(2)MovieClip序列帧动画：MovieClip又称之为“影片剪辑”，是Egret中提供的一种动画解决方案。我们通常会将MovieClip简写为“mc”。实际上一个mc所实现的功能就是播放序列帧动画。当我们想实现一个任务跑动的动作时，需要将原有的动画制成为能够被Egret识别的动画格式。然后将这些制作好的资源进行加载，最后播放。

34.Egret中的音频系统接种HTML5的Audio系统，这使得Egret的音频兼容绝大多数浏览器。在音频文件格式中Egret仅支持MP3格式。由于音频文件属于资源的一部分，所以在游戏逻辑中，使用音频前需要预先加载音频资源。

35.Egret显示对象：

(1)直接继承自DisplayObject的类都属于非容器。

(2)继承自DisplayObjectContainer的类都属于容器。

36.打开性能面板:egret.Profiler.getInstance().run();

(1)draw:这个参数描述了当前画面渲染时候drawcall的次数

(2)cost:这里四个参数，EnterFrame阶段的开销，引擎updateTransform开销，引擎draw开销，HTML5中canvas.draw的开销

(3)FPS：当前画面的帧频。

37.DisplayObject类是所有显示对象的父类。

38.Egret中的显示对象DisplayObject拥有四个派生类，分别为：

(1)Bitmap(2)Shape(3)TextField(4)TextInput
这四个派生类实现了不同的功能:

(1)Bitmap进行位图显示和操作。

(2)Shape是可以进行矢量图绘制的显示对象。

(3)TextField和TextInput都属于文本操作。

39.所谓遮罩就是指定一个显示对象哪些部分可以显示，哪些部分不可以显示。Egret启用遮罩功能非常的简单，在DisplayObject中，我们暴露了一个名称为Mask的属性，该属性就是用来指定遮罩部分的。

40.自定义显示对象类需要继承自DisplayObject的具体子类。

41.每一个显示对象都包含锚点，该锚点默认位于显示对象的左上角。当设置一个显示对象的坐标位置时，我们会以锚点为参考改变显示对象绘图位置。同时，锚点相对于显示对象的位置也是可以改变的。

42.Egret显示列表只是针对于Egret的显示容器物体。

43.Egret中的事件机制是一套业内标准的事件处理架构。Egret中，事件模型定义了一套标准的生成和处理事件消息的方法，使程序中的对象可以相互交互，通信，保持自身状态和相应变化。简单的说，数据的提供者只管发出数据对象，只要确保数据对象是egret.Event类或者子类的实例即可。这种数据对象，称为事件（Event）。数据对象的发出者，称之为事件发送者（Event dispatcher）。同时，接受事件的对象，称为事件侦听者（Event listener）。

44.事件机制包含4个步骤：注册侦听器，发送事件，侦听事件，移除侦听器。这四个步骤是按照顺序来执行的。

45.Event类是所有事件类的基类。当你你要创建一个自定义事件的时候，事件应该继承自Event类。同时Event类也包含一些事件。这些事件通常与显示列表、显示对象的状态有关。

46.事件侦听器也就是事件的处理者，负责接收事件携带的消息，并在接收到该事件后执行特定的代码。创建侦听器，注册侦听器与移除侦听器，检测侦听器。

47.事件是可以设置优先级的，这是一个非常方便而且灵活的功能。我们可以通过制定事件的优先级来确保那个事件侦听器会得到提前处理。你可以在注册侦听器的时候制定事件的优先级。

48.位图的使用离不开纹理的支持，在Egret中，我们默认隐藏了纹理的操作，所有操作针对于显示对象进行。但位图的显示依然基于纹理。在显示一张图片时，我们需要使用Bitmap类。这是egret中的图片类，而纹理则来自于我们加载的资源图片。通常情况下，我们会使用单张图片作为纹理，游戏中也会大量使用纹理集来进行渲染。

49.所有显示对象都可以添加EnterFrame侦听器，用于处理帧事件

private createScene():void {

	var sprite: egret.Sprite = new egret.Sprite();
	
	sprite.addEventListener(egret.Event.ENTER_FRAME,this.onEnterFrame,this);

}

private onEnterFrame()

{

	console.log("aaaa");

}

50.Timer类实现计时器的功能

private createScene():void {
	
	var timer: egret.Timer = new egret.Timer(1000);
	
	timer.addEventListener(egret.TimerEvent.TIMER,this.onTimerHandler,this);
	
	timer.start();

}

51.Tween提供一组缓动算法

private createScene():void {
	
	var sprite: egret.Sprite = new egret.Sprite();
	
	//Tween的所有都以毫秒为单位
	
	egret.Tween.get(sprite).wait(2000).to({ x: 100 },1500).call(this.onComplete);
	
	//egret.Tween.removeTweens(sprite);

}

private onComplete()

{
	
	console.log("aaaa");

}

52.Event类作为创建Event对象的基类，当发生事件时，Event对象将作为参数传递给事件侦听器。

private createScene():void {
	
	var eventDispatcher: egret.EventDispatcher = new egret.EventDispatcher();
	
	//注册和删除侦听的时候一定要传入this，这里和Flash区别
	
	eventDispatcher.addEventListener("MyEvent",this.onEventHandler,this);
	
	eventDispatcher.dispatchEvent(new egret.Event("MyEvent",false,false));

}

private onEventHandler(event:egret.Event):void

{
	
	var type: string = event.type;
	
	console.log("------" + type);//------MyEvent
	
	event.stopImmediatePropagation();
	
	event.stopPropagation();

}

53.TextField是egret的文本渲染类，采用浏览器/设备的API进行渲染，在不同的浏览器/设备中由于字体渲染方式不一，可能会有渲染差异。

54.URLLoader类以文本、二进制数据或URL编码变量的形式从URL下载数据。在下载文本文件、XML或其他用于动态数据驱动应用程序的信息时，它很有用。

55.MouseEvent：鼠标事件相关。由于js的this是动态地，所以添加和删除事件的时候，需要传入this参数。

private createScene():void {
	
	var sprite: egret.Sprite = new egret.Sprite();
	
	sprite.addEventListener(egret.TouchEvent.TOUCH_TAP,this.onMouseHandler,this);
	
	sprite.addEventListener(egret.TouchEvent.TOUCH_BEGIN,this.onMouseHandler,this);
	
	sprite.addEventListener(egret.TouchEvent.TOUCH_END,this.onMouseHandler,this);
	
	sprite.addEventListener(egret.TouchEvent.TOUCH_MOVE,this.onMouseHandler,this,true);

}

private onMouseHandler(event: egret.TouchEvent): void {
	
	var stageX: number = event.stageX;
	
	var stageY: number = event.stageY;
	
	var localX: number = event.stageX;
	
	var localY: number = event.localY;
	
	var target: any = event.target;
	
	var currentTarget: any = event.currentTarget;
	
	console.log("======");

}

56.egret.全局函数

显示继承的公共方法

(1)callLater(method:Function,thisObject:any,...args):void 延迟函数到屏幕重绘前执行

(2)clearInterval(key:number):void 清除制定延迟后运行的函数

(3)clearTimeout(key:number):void 清除制定延迟后运行的函数

(4)getDefinitionByName(name:string):any 返回name参数制定的类的类对象引用

(5)getOption(key:string):string:获取浏览器或者Runtime参数，如果没有设置返回空字符串在浏览器中相当于获取url中参数，在Runtime获取对应setOption参数。

(6)getQualifiedSuperclassName(value:any):string 返回value参数制定的对象的基类的完全限定类名

(7)getTimer():number 用于计算相对时间

(8)hasDefinition(name:string):boolean 检查指定的应用程序域之内是否存在一个公共定义

(9)is(instance:any,typeName:string):boolean 检查制定对象是否为Egret框架内制定接口或类或其子类的实例

(10)registerClass(classDefinition:any,className:string,interfaceNames:string[]):void 为一个类定义注册运行时类信息，用此方法往类定义上注册它自身以及所有接口对应的字符串。

(11)setInterval(listener:Function,this,Object:any,delay:number,...args):number 在指定的延迟（以毫秒为单位）间接循环调用指定的函数。

(12)setTimeout(listener：Funtion，thisObject：any，delay：number，...args):number 在指定的延迟（以毫秒为单位）后运行指定的函数。

(13)startTick(callBack:(timeStamp:number)=>boolean,thisObject:any):void 注册并启动一个计时器，通常会以60FPS的速率触发回调方法，并传入当前时间戳

(14)stopTick(callBack:(timeStamp:number)=>boolean,thisObject:any):void 停止之前用starTick()方法启动的计时器

(15)superGetter(currentClass：any,thisObj:any,type:string):any 获取父类的getter属性值

(16)superSetter(currentClass:any,thisObj:any,type:string,...values)调用父类的setter属性，代替其他语言的写法，如super.alpha=1；

(17)toColorString(value:number):string转换数字为颜色字符串



