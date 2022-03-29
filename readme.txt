1. 自定义样式

# 在页面顶部插入
style: |
    section footer{
        margin-left:50px
    }
    
    li>strong{
        font-size:32px;
        padding:5px;
        background-color:#CCCCCC
    }

<!-- _footer: 这是脚标, 只用到当前页面 -->
<!-- footer: 这个页脚会影响当前页面和以后的页面，除非遇到 _footer -->
<!-- _footer: '**粗体文字** ![w:64 h:64](images/msgraph.png)' -->

## <!-- fit --> 大标题
<!-- _color: red -->
<!-- _backgroundColor: green -->

2. 更多语法，请参考 https://marpit.marp.app/directives