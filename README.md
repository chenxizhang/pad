# PAD (Power Automate for Desktop) 学习和培训
> 陈希章 2022-3-30


## 变量，控制语句

- 一般变量，列表变量
- if,elseif,else
- switch，case， default case
- loop (for), loop condition( while)，exit(break), next(continue)
- for each
- label（flow control)， goto， exit subflow (强制提前退出某个子流程)，stop flow（整个流程停止）
- end （为什么还单独搞这个action）
- run desktop flow, run subflow


## 问题列表

- [ ] PAD 的快捷键列表，尤其是如何快速回到action的那个搜索框，而不是每次都要鼠标点击
- [ ] Action 的名称不能改
- [ ] 如何给子流程传递参数？现在好像只能用全局变量？
- [ ] 为啥不能直接上传图片，而一定要捕捉[这里的图片好像是用于一些特殊的图像识别场景]
- [ ] 英文版如何切换为中文版。
- [ ] 是只有Windows能用吗？
- [ ] Windows10也能装？
- [ ] 如何快速开发并部署、分发自定义action？robin？
- [ ] 在编辑器，如果不用鼠标拖放，action很容易错位，尤其是有if, loop，for each这种容器的情况下，是否有啥好的办法
- [ ] 这些流程文件放在哪里去了？如何复制分享给其他人？导出robin文件？怎么复制部分代码的？我看群里聊
- [ ] 安装了powerautomate 的runtime就可以运行云端流程了？
- [ ] 有没有系统变量的概念，例如获取当前PAD的一些信息
- [ ] PAD 是不是开源的？针对其他产品最大的优势是什么？免费？Roadmap在哪里？
- [ ] 有没有其他比较好的开源产品？
- [ ] 删除if，居然不会自动删除end，需要人工去删
- [x] action的on error的处理程序中，如何get last error，例如根据不同的异常进行不同的处理. 在 on block error这个action也不行。

   :heart: 通过Rule来解决，而且能列出可能的异常类型。

