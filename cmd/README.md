# `/cmd`

本项目的主要应用.

目录名称，应匹配的每个应用程序可执行文件的名字(例如,如果你有你想要的`/cmd/myapp`).

不要在此目录中放置大量代码。如果您认为代码可以导入，并在其他项目中使用,那么它应该存在于`/pkg`目录。如果代码不可重用,或者如果不希望其他人重用它,请将代码放入`/internal`目录。你永远不知道别人会做什么,所以明确你的意图!

有一个简单，常见的`main`函数，它从`/internal`和`/pkg`目录导入和调用代码，然再也没有什么了.

例子:

-   <https://github.com/heptio/ark/tree/master/cmd>(只是一个非常小的`main`函数，与其他的一切)
-   <https://github.com/moby/moby/tree/master/cmd>
-   <https://github.com/prometheus/prometheus/tree/master/cmd>
-   <https://github.com/influxdata/influxdb/tree/master/cmd>
-   <https://github.com/kubernetes/kubernetes/tree/master/cmd>
