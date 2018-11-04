# `/pkg`

由外部应用程序使用的库代码(例如,`/pkg/mypubliclib`)。其他项目将导入这些库,并希望它们能工作,所以在你把东西放在这里之前要三思:

当根目录包含许多非 Go 组件和目录时,它还可以将 Go 代码分组到一个地方,从而更容易运行各种 Go 工具(如[`Best Practices for Industrial Programming`](https://www.youtube.com/watch?v=PTE4VJIdHPg)来自 GopHeCon EU 2018).

请注意,这不是一个普遍接受的模式，对于使用它的流行repo,你都不能找到10个。所以由您决定是否要使用此模式。无论它是否是一个好的模式,更多的人会知道这是你自身的想法。对于新的Go开发者来说这有点令人困惑,但这是一个非常基本的疑问，解决它! 而这也是该**project-layout**项目创建的目的之一.

例子:

-   <https://github.com/prometheus/prometheus/tree/master/pkg>
-   <https://github.com/jaegertracing/jaeger/tree/master/pkg>
-   <https://github.com/istio/istio/tree/master/pkg>
-   <https://github.com/google/gvisor/tree/master/pkg>
-   <https://github.com/google/syzkaller/tree/master/pkg>
-   <https://github.com/perkeep/perkeep/tree/master/pkg>
-   <https://github.com/minio/minio/tree/master/pkg>
-   <https://github.com/heptio/ark/tree/master/pkg>
-   <https://github.com/heptio/sonobuoy/tree/master/pkg>
-   <https://github.com/kubernetes/kubernetes/tree/master/pkg>
-   <https://github.com/kubernetes/kops/tree/master/pkg>
-   <https://github.com/moby/moby/tree/master/pkg>
-   <https://github.com/grafana/grafana/tree/master/pkg>
-   <https://github.com/influxdata/influxdb/tree/master/pkg>
-   <https://github.com/cockroachdb/cockroach/tree/master/pkg>
-   <https://github.com/derekparker/delve/tree/master/pkg>
-   <https://github.com/coreos/etcd/tree/master/pkg>
-   <https://github.com/oklog/oklog/tree/master/pkg>
-   <https://github.com/flynn/flynn/tree/master/pkg>
-   <https://github.com/jesseduffield/lazygit/tree/master/pkg>
-   <https://github.com/gopasspw/gopass/tree/master/pkg>
-   <https://github.com/sourcegraph/sourcegraph/tree/master/pkg>
-   <https://github.com/sosedoff/pgweb/tree/master/pkg>
