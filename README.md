# PAD (Power Automate for Desktop) 学习和培训
> 陈希章 2022-3-30

## 变量（用 **%xxxx%** 表示）

- 输入变量（Input)，输出变量 (Output)，都可以有多个
- 变量类型（List，DataTable, Custom Object)

   ```
   列表变量，成员访问方式 List[0]
   数据表变量，成员访问方式 DataTable[0][1]，特别适合于Excel
   自定义对象,可以从JSON转换过来，{ "firstName": "John", "lastName": "Michael" } 属性访问方式：Object["PropertyName"]，或 Object.PropertyName
   ```

- 变量属性, 如 **%Files.Count%**
- 变量计算是在 % 里面，例如 **%a-1*2%**


## 控制语句

- 一般变量，列表变量
- if,elseif,else
- switch，case， default case
- loop (for), loop condition( while)，exit(break), next(continue)
- for each
- label（flow control)， goto， exit subflow (强制提前退出某个子流程)，stop flow（整个流程停止）
- end （为什么还单独搞这个action）
- run desktop flow, run subflow


## 问题列表

- [x] PAD 的快捷键列表，尤其是如何快速回到action的那个搜索框，而不是每次都要鼠标点击
   
   目前没有

- [x] Action 的名称不能改

   目前不能改，同时可以加注释 comment。或者用 if (1=1) 的语句块来解决。


- [x] 如何给子流程传递参数？现在好像只能用全局变量？

   - 目前只有通过命名上面做一定的区分。
   - 或者做一个统一的大流程，然后通过参数决定调用哪个子流程，然后外部调用这个大流程。这倒是一个有意思的封装方式。类似于一个工具类。

- [x] 为啥不能直接上传图片，而一定要捕捉

   这里的图片好像是用于一些特殊的图像识别场景

- [x] 英文版如何切换为中文版。

   要确保windows的默认语言是中文。Flow Designer可以自动适应，但Console还是英文的。

- [x] 是只有Windows能用吗？

   是的，是基于.net framework，目前没有基于.net core

- [x] Windows10也能装？

   - 是的，亲测可装。Windows7不可以。windows 10 要64位
   - windows 11自带的，是从store安装的，程序文件在 C:\Program Files\WindowsApps\Microsoft.PowerAutomateDesktop_10.0.3444.0_x64__8wekyb3d8bbwe 
   - windows 10 单独安装的，程序文件会在 


- [ ] 如何快速开发并部署、分发自定义action？robin？
- [ ] 在编辑器，如果不用鼠标拖放，action很容易错位，尤其是有if, loop，for each这种容器的情况下，是否有啥好的办法
- [ ] 这些流程文件放在哪里去了？如何复制分享给其他人？导出robin文件？怎么复制部分代码的？我看群里聊
- [x] 安装了powerautomate 的runtime就可以运行云端流程了？

   不对，是反过来的。云端可以执行桌面的流程。但需要Premium的license才行。

- [x] 有没有系统变量的概念，例如获取当前PAD的一些信息，例如当前流程是自己运行的呢，还是别别的流程调用的？

- [x] PAD 是不是开源的？针对其他产品最大的优势是什么？免费？Roadmap在哪里？

   不开源

   Roadmap，在这里 <https://docs.microsoft.com/en-us/power-platform-release-plan/>

- [x] 有没有其他比较好的开源产品？

   RPAStudio，基于.NET

- [x] 删除if，居然不会自动删除end，需要人工去删

   这是by design。end也是一个组件。

- [x] action的on error的处理程序中，如何get last error，例如根据不同的异常进行不同的处理. 在 on block error这个action也不行。

   :heart: 通过Rule来解决，而且能列出可能的异常类型。

- [ ] 网页捕捉太难用且麻烦。有些右键菜单，跟元素选择又重叠，经常点错。有啥好办法和经验。例如这个读取汇率的例子 https://www.msn.com/en-us/money/tools/currencyconverter


   > 感觉用Powershell，Python脚本之类简单多了。如果是有一些什么特殊的操作，也可以在网页中执行Javascript来实现吧。（Run javascript function on web page）
   截取快照，读取网页元数据倒是挺好用的。



- [x] 不联网估计还是不行的，我偶尔发现如下的错误。 在创建一个新的流程时

   ```
   Make sure that you have an active internet connection and that access to the required cloud services isn't blocked. Run the Windows internet connections troubleshooter and if the issue persists contact your network administrator
   ```

- [x] 桌面流程如何自动化运行，例如定时运行？例如我定时要对某个网页做个截屏，这个怎么实现呢？



- [ ] python 脚本仅支持2.0




