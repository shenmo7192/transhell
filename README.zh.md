# transhell
## transhell 是一个bash国际化方案，可以让你的bash脚本拥有国际化的能力

为了使用transhell,请在你的脚本的最上方加入`example`中的 .`load_transhell` 函数并执行之。

### 使用指南
**建议结合本仓库example目录下的例子查看**

1. 将需要国际化的脚本中的文案转为助记变量(推荐为$TRANSHELL_CONTENCT_XXXXXX)



原文：
```
echo "这是一个测试文档"
```

修改后

```
echo “${TRANSHELL_CONTENT_THIS_IS_A_TEST_DOC}”
```

2. 在脚本同位置下新建`transhell`目录，并在其中放置翻译文件

命名为：`脚本文件名_语言代码.transhell`

例如`transhell/test_en_US.transhell`或者`transhell/test_zh_CN.transhell`


```
TRANSHELL_CONTENT_THIS_IS_A_TEST_DOC="这是一个测试文档"
```

> 特性
> 1. load_translate会优先尝试加载`en_US`语言的翻译文件，随后尝试用运行环境的语言的翻译文件来覆盖。这个特性可以保证在缺失全部或部分翻译条目的时候使用英文来fallback.如果你不希望使用英文作为fallback,请更改脚本中的加载顺序
> 2. 除了在脚本所在目录，`load_transhell`还会尝试从`/usr/share/脚本文件名/transhell`下读取。优先级为：脚本所在目录>/usr/share下。