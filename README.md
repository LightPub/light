# light

自渲染引擎(施工中)

## 渲染流水线

> 划分多个层次拼凑起整个流水线

### Framework层

> ui线程，js实现。包含整个Framework内容

+ 基础组件: text,image,list,scroll
+ 引入前端技术：dom 和 style，例：Vue等dsl技术
+ 动画
+ 手势
+ 键盘/鼠标等输入

### Engine

> 渲染线程，一般也是主线程，C++实现。负责bgfx调用，布局计算等。另外还有一个io线程，进行图片的编解码,上传图片数据到gpu，和主线程共享gpu context

+ 布局: 不同的是android的底层实现，将这部分划分在Framework中，而flutter划分到engin层，目前觉得划分在Framework中最利于实现，但是性能未必最优
+ 调用bgfx渲染

### 嵌入层

> 解决跨平台问题，进行事件对接， Surface 对接，以及 Native 平台接口调用的插件机制。

+ VSync信号：传递到Framework

## 模块

+ 输入管理模块，用来获取用户输入
+ 策略模块，用来执行策略
+ 场景管理模块，用来管理场景和更新场景
+ 渲染模块，用来执行渲染和画面输出
+ 音频音效模块，用来管理声音，混音和播放
+ 网络通信模块，用来管理网络通信
+ 文件I/O模块，用来管理资源的加载和参数的保存回复
+ 内存管理模块，用来调度管理内存上的资源
+ 驱动模块，用来根据时间，事件等驱动其它模块
+ 辅助模块，用来执行调试，log输出等辅助功能
+ 应用程序模块，用来抽象处理配置文件，特定平台的通知，创建窗口等需要与特定平台对接的部分

## 引用wiki上面的模块说明

游戏引擎（狭义）一般来讲包括：图形渲染系统，物理系统，粒子特效系统，角色骨骼系统，动画系统，场景管理，界面模块，脚本接口，音频网络接口，资源管理，模型和纹理动态加载等，AI模块，内存管理，本地化支持，视频嵌入纹理，以及动态更新模块等等。。。。具体见：Game engine - Wikipedia
广义的游戏引擎还包括各种周边编辑器，特效编辑器，粒子编辑器，UI编辑器，场景编辑器，骨骼动画编辑器。如今越来越多的游戏引擎提供了所见即所得的关卡编辑功能。角色一边在里面和真实情况一样奔跑，一边就可以增加关卡内容和触发器。

## ECS 写法

> 所有的模块都是用ECS写法，这样可以带来统一的扩展手段

## 可能使用到的库

+ bgfx:底层渲染库，跨平台
+ yoga：facebook的排版引擎
+ openal-soft:openal的软实现
+ glfw : 窗体事件等
+ glad : 封装opengl，由于bgfx的原因，大概率用不到
+ mio : 内存映射
+ litehtml:html 和 css
+ skia：google的2d渲染库，android就是用他
+ nodejs / nodejs-mobile：脚本引擎
+ ozz-animation：动画库
+ gumbo-parser/node-gumbo-parser：google的html解释库及第三方的nodejs实现

## 参考

+ [跨平台图形渲染引擎bgfx分析](https://www.codenong.com/cs105888060/)
+ [大比拼 | 下一代高性能跨平台UI渲染引擎](https://zhuanlan.zhihu.com/p/75660948)
+ [跨平台渲染引擎之路：拨云见日](https://zhuanlan.zhihu.com/p/58817407)
+ [游戏引擎中的渲染管线](https://zhuanlan.zhihu.com/p/92165837)
+ [跨平台渲染引擎之路](https://www.zhihu.com/column/c_1088434703387643904)
+ [CMake 入门实战](https://www.hahack.com/codes/cmake)
+ [HTML解析库Gumbo简单使用记录](https://www.cnblogs.com/oloroso/p/9667642.html)
+ [Flutter 实战入门](http://laomengit.com/flutter/widgets/widgets_structure.html)
+ [手把手教你实现一个浏览器引擎](https://zhuanlan.zhihu.com/p/106494297)
+ [手把手教你Vue从零撸一个迷你版MVVM框架](https://blog.csdn.net/u012486840/article/details/104972736)
+ [将 Vue 渲染到嵌入式液晶屏](https://zhuanlan.zhihu.com/p/333179202)
+ [手把手教你打造一款轻量级canvas渲染引擎](https://segmentfault.com/a/1190000021297495?_ea=27021986)
+ [由 FlexBox 算法强力驱动的 Weex 布局引擎](https://www.jianshu.com/p/d085032d4788)
+ [将你的 Virtual dom 渲染成 Canvas](https://zhuanlan.zhihu.com/p/39886896)
+ [60 FPS on the mobile web](https://engineering.flipboard.com/2015/02/mobile-web)
+ [A Custom Renderer for Vue 3](https://vuejs-course.com/blog/a-custom-renderer-for-vue-3)

## android 相关参考

+ [Android中使用NativeActivity进行APP开发](https://blog.csdn.net/qq_21071977/article/details/77878252)
+ [Android——NativeActivity - C/C++ Apk开发](https://www.cnblogs.com/chenxibobo/p/6867206.html)

## 安装环境

+ <https://code.visualstudio.com/docs/cpp/config-mingw>
+ <https://www.jianshu.com/p/c3806d2ad1f8>
