# `/build`

包装和持续集成.

把您的云(AMI),容器(Docker),OS(deb,rpm,pkg)包配置和脚本放入`/build/package`目录.

将您的CI(travis,circle,drone)配置和脚本放入`/build/ci`目录.请注意,某些CI工具(例如,Travis CI)对其配置文件的位置非常挑剔.尝试将配置文件放入`/build/ci`目录将它们链接到CI工具所期望的位置(如果可能).

例子:

-   <https://github.com/cockroachdb/cockroach/tree/master/build>
