## v2.2.0

版本上线时间：2022-03-14



### 能力提升

- DCDR特性去除对Rack依赖，优化DCDR链路创建规范，新建链路时可以进行rack选择。
- admin和gateway中 xxx.yml 或者 xxx.properties中配置项port说明不明确。应该指明是http port 还是tcp port。
- 索引删除逻辑优化（索引管理页面新增close和open按钮，作用是打开或者关闭索引，用户可以选择close索引）。
- Elasticsearch元数据集群专项治理（包括增加routing以及索引index sort）。
- GateWay日志优化+Get Node Task记录，整体写入与查询问题。
- 2.3.3 存量ES集群版本全纳管，索引管理模板中check禁用读、禁用写。
- 网关原生模式：支持限流（支持appid粒度）、支持gateway对请求token校验。
- Kibana的DisCover模块代理逻辑（非dsl控制台也要数据隔离，带上物理集群名到gateway查询）。
- 增加Sense管控的集群路由能力。
- 元信息指标读写都在GateWay，网关看板指标保障准确（网关看板添加clientNode视图）。
- 指标看板-topN算法优化。
- 指标看板新增索引模板视图的指标监控。

### 体验优化

- 平台搜索框需要具备记录能力，切换不清空。
- 接入集群端口放开，不限制只能4位。之前是限制4位，后面放开为0-25535。
- 集群版本管理体验优化 ，新增版本标识：滴滴内部、开源。
- 集群名称默认物理名称+集群版本号（输入框加提示，规范用户操作）。
- 平台配置项的说明文档优化，配置说明优化（跳转至github文档说明）。
- 模板管理的操作项将平台能力与索引模板服务区分展示。
- 插件管理定义（物理集群插件管理分为平台能力插件、ES能能力插件）。
- 索引模板详情 Mapping、 Setting  、DCDR TAB页体验页面优化。
- 全平台集群下拉框需要支持搜索能力。
- 检索查询--索引查新--SQL查询页面体验优化。
- 指标配置新增黄金指标配置，点击一键勾选黄金指标。
- 容量规划概念统一为索引RollOver（shard调整和indexRollover 统一，索引模版服务名称由容量规划改为索引规划）。
- 索引模板管理页面加入物理集群筛选项。
- 指标图表可以同类中进行拖拽，指标配置顺序同步修改。
- 接入集群记录主机分为两种模式：自动获取、全量录入。
- LogIEM全平台列表排序支持全局排序。
- 新建集群增加节点规格输入框，物理集群详情-节点划分新增节点规格展示列。
- 筛选分片过多的集群 ：物理集群列表增加一列”活跃分片数“，支持排序。
- 索引模板mapping、setting等更新操作需要保留记录（旧mapping、setting和修改后的mapping setting）。
- 逻辑集群增加等级标识：核心、重要、一般。索引模板支持业务等级与逻辑集群绑定，新建模板时默认与所选集群业务等级一致，支持修改，升降等级均可。
- 集群接入增加所属资源类型：acs、vmware、信创（tce）。
- 检索查询-DSL模板改成查询诊断。
- 总览视图和节点视图中涉及到数量趋势、TASK耗时的指标名称改为（节点）执行任务数量、（节点）执行任务数耗时。

### bug修复

- 修复dcdr采集任务报错，自己的元数据es引擎根本没有DCDR的actionplugin。
- 修复DSL查询切换集群时报错问题（GET  _cluster/health?v）。
- 修复网关看板--查询模板点击事件消失问题（可能是代码未合到主分支导致）。
- 统一集群看板的节点角色概念和物理集群详情中节点划分的角色概念。
- 集群状态statustype 0，1，2统一标准。
索引模板名称不支持大写字母，前端修复。