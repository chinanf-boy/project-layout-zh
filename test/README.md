# `/test`

额外的外部测试应用程序和测试数据。发挥你的想象，随意构造`/test`。或对于更大的项目来说,有一个数据子目录是有意义的。例如,你可以拥有`/test/data`或`/test/testdata`，如果你需要去忽略那个目录中的内容。注意,Go 还将忽略以`.` or `_`开头的目录或文件,因此在如何命名测试数据目录方面，具有更大的灵活性.

实例:

-   [https://github.com/openshift/origin/tree/master/test](https://github.com/openshift/origin/tree/master/test)(测试数据在`/testdata`子目录)
