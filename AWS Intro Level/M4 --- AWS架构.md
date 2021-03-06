M4 --- AWS架构

Architecture

本模块重点介绍了部署或迁移到AWS云环境时架构方面的考量。本模块介绍了架构完善的解决方案的基本知识，讨论了容错和可用性，并在最后介绍了AWS云钟的Web托管功能。

---

AWS架构完善的框架

```
简介：AWS架构完善的框架可以帮助客户：
	· 评估和改进架构
	· 了解设计如何影响业务
	· 了解五大支柱和设计原则

五大支柱：
	- 安全性
	- 可靠性
	- 性能效率
	- 成本优化
	- 卓越运营


```

```
安全性支柱：
	- 身份与访问管理（IAM)
		· AWS Identity and Access Management
		· 非常重要，可以确保只有经过授权和身份验证的用户才能访问特定资源，且只能以预期的方式进行访问。
	- 检测性控制
		· 通过考虑捕获或分析日志以及集成审计控制等方法。检测性控制可以识别潜在的安全事件。
	- 基础设施保护
		· 可以确保架构中的系统和服务受到保护，从而防止意外和未经授权的访问
		· 例： 用户可以创建网络边界，进而强化和修补用户、密钥、访问级别以及应用程序防火墙或网关等。
	- 数据保护
		· 可以考虑采用多种方式和方法实现这一目的， 包括数据分类、加密、保护静态数据和传输中的数据、数据备份以及再需要时复制和恢复。
	- 事件响应
		· 及时采取了所有预防和检测措施，组织仍应创建事件响应流程以便应对和减少任何潜在安全事件。
		· 事件响应应可保证用户的架构得到更新以便为恢复提供及时的调查。

*** 设计原则 ***
	- 在所有层中实施安全性
		· 需要确保基础设施的每一层随时随地都是安全的。
		· 在物理数据中心中，通常只需要考虑外围的安全性；然而在AWS环境中，可以在外围以及资源内部和资源之间实现安全性。
		· 可以确保个人环境和组件都具备独立的安全性。
	- 实现可追踪性
		· 可以对环境中进行的所有操作和更改进行日志记录和审计
	- 遵循最低权限原则
		· 需要确保在环境中授予了适当的权限，并且对AWS资源实施了有力的逻辑访问控制
	- 专注于保护您的系统
		· 借助AWS责任共担模式，您可以集中精力保护应用程序数据和操作系统，而AWS可以提供安全的基础设施和服务
	- 自动化
		· 自动实施安全最佳实践。
		· AWS提供了基于软件的安全机制，让用户能够更快速、更经济高效地实施安全扩展。
******
	
```

```
可靠性支柱：
	- 从问题/故障中恢复
		· 动态获取计算资源以满足要求以及减少中断的能力
	- 在以下方面应用最佳实践：
		- 基础环境
			· 查看基础环境至关重要
			· 在构建任何系统之前，要先满足影响可靠性的基本要求
		- 变更管理
			· 务必要了解变更会对系统造成怎样的影响
			· 如果主动规划并监控系统，就可以快速、可靠地适应这些变更并随之做出调整
		- 故障管理
			· 要确保可靠性，关键是要预测、了解和响应故障并防止再次发生
	- 预测、响应并预防故障
		· 在云环境中可以通过监控使用自动化，可以替换环境中的系统然后再系统仍然可靠的情况下以较低的成本排除故障
		
*** 设计原则 ***
	- 测试恢复流程
		· 在云环境中，用户有能力测试系统如何发生故障， 他们可以验证恢复程序。
		· 用户可以模拟和接触不同的故障案例然后在实际故障发生之前测试他们的反应
	- 自动恢复
		· 借助AWS，用户能够在达到阈值时触发自动响应
		· 可以在出现故障之前进行预测并修复
	- 横向扩展
		· 以便提高聚合系统的可用性
		· 如果用户有一个大型整体式资源，最好用多个小型资源进行代替。这将减少任何单点故障对整个系统的影响。
		· 这条原则的目标是横向扩展，并跨多项小型资源分配需求
	- 无需猜测容量
		· 在云中，开发者可以监控需求和系统使用情况，并自动添加或删除资源。
		· 这将确保开发者达到最佳水平以便满足需求，无论是预置过度还是不足。
	- 管理自动化中的变更
	 	· 开发者应该对自己的架构和基础设施自动实施变更
	 	· 开发者只需要管理对自动化系统的更改，而不需要管理任何单独的系统或资源
******
```

```
性能效率支柱：
	- 选择可自定义解决方案
		· 重要的是要选择可优化开发者架构的最佳解决方案
		· 选择适合任务的工具
		· 解决方案会因工作负载类型而异
		· 借助AWS，开发者可以虚拟化资源并自定义多种不同类型和配置的解决方案
	- 进行审核以持续创新
		· 开发者可以不断实施解决方案创新
		· 可以利用更新的技术和方法来实现这一点
	- 监控AWS服务
		· 在实施架构以后，开发者需要监控性能以确保在客户收到影响并发现任何问题之前进行修复
		· 借助AWS，可以使用自动化功能，还可以使用多种工具监控框架，比如Amazon CloudWatch/Amazon Kinesis...
	- 考虑权衡
		· 权衡了一致性、持久性以及空间与时间或延迟以便确保开发者能够实现最高性能
		
*** 设计原则 ***
	- 普及先进技术
		· 对于难以实施地技术，通过将相关知识和复杂性纳入云供应商地纳管范围，从而使用户可以轻松地利用这些技术。
		· IT团队无需了解如何托管和运行全新技术，只需将它当作一种服务使用
	- 数分钟内实现全球化部署
		· 借助AWS，开发者能够在全球多个区域轻松地部署系统，同时以最低成本为客户提供延迟更低体验更好的服务
	- 使用无服务器架构
		· 在AWS中，开发者无需运行和维护用于计算活动的传统服务器。
		· 可以消除运维负担同时降低事务性成本
	- 更频繁地进行试验
		· 提高试验频率
		· 借助虚拟化，开发者可以执行测试以便提高效率
	- 了解技术
		· 实现软硬件协同技术
		· 建议开发者使用最符合预期目标的技术方法
******
```

```
成本优化支柱
	- 使用经济高效的资源
		· 确保系统使用适当的服务、资源和配置。这是实现成本节约的重要一环
		· 需要关注的细节：预置、规模调整、购买选项和其他具体信息，以便确保采用的是最符合需求的架构
	- 供需相符
		· 借助AWS，开发者可以利用云架构的弹性来满足不断变化的需求
		· 可以自动扩展，也可以接受其他服务的通知以便根据需求变化调整供应量
	- 增强支出意识
		· 充分了解业务支出以及成本驱动因素至关重要
		· 如果开发者能够查看、了解和分析当前成本，预测未来成本以及制定相应计划，便能够改进开发者在AWS上的架构的成本优化
	- 持续不断优化
		· 借助所有工具和各种各样的方法，开发者可以根据通过AWS平台收集的数据测量、监控并改善架构

*** 设计原则 ***
	- 采用消耗模型
		· 开发者只需为实际使用的计算资源付费，还可以根据业务需求增加或减少资源
	- 衡量总体效率
		· 衡量系统的业务成果以及与交付成果相关的成本非常重要
		· 开发者需要通过衡量结果了解如何通过增加成果和降低成本来获得收益
	- 减少数据中心运营支出
		· 借助AWS，开发者无需再处理服务器的机架、堆栈和供电等繁重工作
		· 开发者可以完全专注于客户和业务项目而不必再为IT基础设施忧心
	- 分析置出和确定支出归属
		· 借助云，开发者可以更简单、轻松地准确确定系统的使用情况和成本
		· 客户可以衡量他们的投资回报率，借此优化资源并降低成本
	- 使用托管服务
		· 降低成本
******
```

```
卓越运营支柱：
	- 管理和自动执行变更
	- 响应事件
	- 定义标准
```



---

容错能力和高可用性：

```
容错能力:
	- 系统保持运行的能力
	- 应用程序组件内置冗余
```

```
高可用性：
	- 系统普遍运行正常并且可以访问
	- 最大程度地减少停机时间
	- 需要极少的认为干预
	- 最少的前期资金投入
```

```
高可用性：本地与AWS对比

传统（本地）
	- 成本高
	- 仅限任务关键型的应用程序
AWS
	- 多个服务器
	- 可用区
	- 区域
	- 具备容错能力的服务
```

```
高可用性服务工具
· Elastic Load Balancer
	- 分配传入流量（负载）
	- 将指标发送到Amazon CloudWatch
	- 触发/通知
		· 高延迟
		· 使用过度
· 弹性IP地址
	- 是静态IP地址
	- 屏蔽故障（如果发生）
	- 在实例故障时继续访问应用程序
· Amazon Route 53
	- 授权型DNS服务
		· 将域名转换为IP地址
	- 支持：
		· 简单路由
		· 基于延迟的路由
		· 运行状况检查
		· DNS故障转移
		· 地理位置路由
· Auto Scaling
	- 终止和启动实例
	- 协助调整或修改容量
	- 按需创建新资源
· Amazon CloudWatch
	- 分布式统计信息收集系统
	- 跟踪基础设施指标
	- 创建和使用开发者自己的自定义指标
	- 与Auto Scaling配合使用
```

```
容错工具：
	- Amazon Simple Queue Service
		· 容错应用程序的主干
	- Amazon Simple Storage Service
		· 高度持久且具备容错能力的数据存储
	- Amazon Relational Database Service
		· Web服务工具，用于设置、操作和扩展关系数据库
	
```

---

Web 托管

```
AWS上的Web托管：
	· 快速
	· 简单
	· 成本低
	
可以在AWS上托管的网站：
	公司网站、内容管理系统、社交媒体应用程序等
	
如何用经济有效的方式应对高峰？
	- 借助AWS，按需配置启动额外的服务器以便开发者可以调整容量来满足需求并且只需按实际使用量付费
	
测试资源？
	- AWS可以让开发者仅在需要时预置测试机群，测试完成后，可以快速从预生产环境迁移到生产环境，最大限度地减少中断
```



---

Quiz： 哪项不是AWS架构完善的框架的支柱？

A: 持久性