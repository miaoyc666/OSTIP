# 开源威胁情报平台

威胁情报管理平台（Threat Intelligence Platform）是指一种技术解决方案，可从采集多种来源和异构数据、并汇总、组织、关联分析情报资源。

威胁情报管理平台的情报来源应当包含：    
- 主动情报源
  - 蜜罐
  - 流量设备
  - 内生情报
  - 被动情报源

国家监管机构分布

开源情报分享

商业威胁情报（花钱买的）

威胁报告（安全厂商提供），而且可信度较高

安全厂家/安全分析师的社交媒体

暗网监控



威胁情报管理平台也分为商业版本和开源版本，本文介绍的是开源威胁情报管理平台（OSTIP），包括：

MISP，本项目实现更有效的威胁情报利用过程。重点是共享结构化的威胁指标。

OpenCTI，专注于网络威胁情报知识和可观察窗口的管理，专注于威胁建模。

DocIntel，侧重于实现技术指标的信息和知识信息。



传统巨头MISP
MISPOpenSourceThreatIntelligencePlatform&OpenStandardsForThreatInformationSharing(misp-project.org)

MISP是一款开源的威胁情报管理平台，用于收集，存储，分发和共享有关网络安全事件分析和恶意软件分析的网络安全指标和威胁。MISP 由事件分析师、安全和 ICT 专业人员设计，专为其日常运营而设计，以有效共享结构化信息。目标是促进安全社区内外结构化信息的共享。MISP提供的功能支持信息交换，但也支持网络入侵检测系统（NIDS），LIDS以及日志分析工具SIEM对所述信息的消费。

MISP，恶意软件信息共享平台和威胁共享，核心功能是：



高效的IOC数据库，可以存储有关恶意软件样本，事件，攻击者和情报的结构化数据。



自动关联查找恶意软件、攻击活动或分析的属性和指标之间的关系。关联引擎包括属性之间的关联和更高级的关联，如模糊哈希关联（例如 ssdeep）或 CIDR 块匹配。



一种灵活的数据模型，其中可以表达复杂的对象并将其链接在一起。



内置共享功能，可简化使用不同分布模型的数据共享。



直观的用户界面。



导出：生成纯文本，CSV，STIX 1和2或JSON输出；导入 ：STIX 1.1/2.0 导入。



数据共享：使用MISP与其他方和信任组自动交换和同步。


开源威胁情报管理平台（OSTIP）概览

开源威胁情报管理平台（OSTIP）概览

该项目由来自CIRCL，比利时国防部，北约和NCIRC的开发团队开发，由欧盟（通过连接欧洲设施）和卢森堡计算机事件响应中心资助。



感兴趣的朋友们可以访问这两个链接进一步了解：

威胁情报的最佳实践 (misp-project.org)

User stories · User guide of MISP intelligence sharing platform (circl.lu)









中流砥柱OpenCTI
Filigran-OpenCTI-Openplatformforcyberthreatintelligence

OpenCTI 是一个开源威胁情报管理平台，允许组织管理其网络威胁情报，OpenCTI 即 Open Cyber Threat Intelligence Platform，开源网络威胁情报平台。它的创建是为了构建、存储、组织和可视化有关网络威胁的技术和非技术信息。它使用基于 STIX 2 标准的知识模式来执行数据的结构化。并被设计为现代 Web 应用程序，包括 GraphQL API 和面向 UX的前端。此外，OpenCTI 可以与其他工具和应用程序集成，如 AlienVault，CrowdStrike，Mandiant，MISP，MITRE ATT&CK，TAXII，VirusTotal，Shodan，Elastic，Splunk，STIX，Malego等。

OpenCTI 是由法国国家网络安全机构 (ANSSI)、CERT-EU 和 Luatix 非营利组织合作开发的产品，2021年变更为Filigran进行维护。

OpenCTI是当前开源情报管理平台（TIP）的中流砥柱。

开源威胁情报管理平台（OSTIP）概览

系统数据
OpenCTI 的数据存储采用的是 Graph Model，图模型有两个物理类型：



节点（Node）：就是之前提到的 IoC 都属于 Node



边（Edge）：表达恶意IOC与某APT组织的关系，即节点之间的关系




为了更容易表达不同威胁情报之间的关系，数据采用的是 STIX 2.1 格式储存，又可以分成：


Stix Domain Object （SDO）：攻击模式、TTPs、攻击组织、来源



Stix Cyber Observable （SCO）：就是 IoC，有 hash， email， domain， ip， email， cve， filename等等



Stix Relationship Object （SRO）：描述关系，观察窗口信息或关联内容



STIX bundle：可以理解为扩充字段，STIX的任意集合





开源威胁情报管理平台（OSTIP）概览

开源威胁情报管理平台（OSTIP）概览

OpenCTI的数据模型

系统配置
OpenCTI 其实算是多个服务的集合， 官方的最低要求。


CPU: 6 cores



RAM: 16GB



Disk: SSD



Disk Space: > 32GB


其他依赖服务Elastic Search


CPU: 2 cores



RAM: 8GB



Disk: Normal



Disk Space: > 16GB


MinIO


CPU: 1 cores



RAM: 128 MB



Disk: Normal



Disk Space: 1 GB


Redis


CPU: 1 cores



RAM: 512 MB



Disk: Normal



Disk Space: > 128 MB


RabbitMQ


CPU: 1 cores



RAM: 512 MB



Disk: Normal



Disk Space: 128MB


Workers and connectors


CPU: 1 cores



RAM: 128 MB



Disk: Normal



Disk Space: 128 MB


数据连接器
OpenCTI可以与AlienVault，CrowdStrike，Mandiant，MISP，MITRE ATT&CK，TAXII，VirusTotal，Shodan，Elastic，Splunk，STIX，Malego进行数据对接，不过需要数据连接器（Connector）， github 上放了写好的 connectorhttps://github.com/OpenCTI-Platform/connectors/tree/master/external-import

情报协作扩展DocIntel
Organizeyourthreatreports,leverageintelligence-DocIntel

DocIntel是一个以上下文为中心的威胁情报平台，用于存储所有威胁报告。它用于收集，存储，处理，组织，搜索和传播威胁情报报告。

它不专注于技术指标或威胁建模。它侧重于实现技术指标的信息和知识信息。DocIntel可提供CTI团队使用的信息。它补充了其他威胁情报平台，提供必要的材料以执行后续步骤。DocIntel不使用属性、对象和连接或构建威胁时间线。

DocIntel不支持外部共享信息组织。但是，DocIntel可以对接MISP项目，并在DocIntel中导入警告列表、分类规则和关系拓扑。也不专注于数据模型。DocIntel将帮助分析师管理。分析所需的知识。它还将有助于找到包含所有详细信息的原始威胁报告，没有抽象或过滤。

GitHub：docintelapp/DocIntel: Open Source Platform for storing, organizing, and searching documents related to cyber threats (github.com)

2022年的网络威胁情报峰会上关于DocIntel介绍，B站视频链接：

【【TIP】DocIntel- A Context-Centric Threat Intelligence Platform】 https://www.bilibili.com/video/BV15m4y1c7kv/?share_source=copy_web&vd_source=44f9a94593a8685f9329e7e5be45623f
