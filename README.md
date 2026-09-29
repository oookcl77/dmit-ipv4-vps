# IPv4 VPS：先看是否包含独立 IPv4，再按流量、线路和地区选方案

找 IPv4 VPS 时，真正需要先确认的并不是“CPU 有几核”，而是这台 VPS 到底有没有你需要的**独立 IPv4 地址**、流量怎么算、端口速率是多少，以及网络线路是否适合你的用户所在地。

DMIT 当前把 Cloud Instance 按洛杉矶、香港、东京三个节点，以及 Premium、Eyeball、Tier 1 三类网络拆开；官方还提供 AS3、AN4、AN5 三代 AMD EPYC 平台。官网 Cloud Instance 页面明确写着所有方案都提供免费即时开通和完整 root 权限，而具体 IPv4 数量则要结合产品配置确认。

这篇文章的重点就是把“IPv4 VPS”这个需求拆开：什么情况下普通 IPv4 VPS 就够了，什么时候应该为中国大陆线路付更多钱，DMIT 当前有哪些公开方案，以及购买前有哪些容易踩坑的限制。

## IPv4 VPS 到底要看什么

IPv4 VPS 通常指一台带有公网 IPv4 地址的虚拟专用服务器。对实际部署来说，IPv4 本身只是第一层条件。

例如你要部署网站、面板、API、邮件相关服务、远程管理环境，通常首先关心的是：

* 是否提供公网 IPv4；
* IPv4 是独享还是与其他服务共享；
* IPv4 是否有地区限制；
* 流量额度是多少；
* 超出流量后是限速、暂停还是付费重置；
* 网络端口的峰值是多少；
* VPS 所在地区与访问者之间的线路质量；
* 是否可以使用 root 权限自行安装系统和软件。

DMIT 当前的 Cloud Instance 页面将网络分成 Premium、Eyeball 和 Tier 1。Premium 使用包括 China Telecom CN2 GIA 在内的高级线路，Eyeball 使用 CMIN2 等中国运营商相关路由做“合理努力”的中国访问优化，而 Tier 1 更偏向普通全球互联、亚太和美洲之间的低成本高带宽场景。

所以，“有没有 IPv4”解决的是地址问题；“IPv4 VPS 适不适合你”实际上还要看线路。

## DMIT 的 IPv4 VPS 现在是什么配置逻辑

DMIT 目前的产品结构比较容易让第一次购买的人迷路，因为套餐名称背后同时隐藏了三个维度。

第一是地点：LAX（洛杉矶）、HKG（香港）、TYO（东京）。

第二是网络：Premium、Eyeball、Tier 1。

第三是硬件：AS3、AN4、AN5。官方对三代平台的定位也不同：AN5 是 AMD EPYC 9005 系列 Zen 5、DDR5 和 PCIe 5.0 NVMe；AN4 是 AMD EPYC 9004 系列 Zen 4；AS3 则是 AMD EPYC 7003 系列 Zen 3。

对 IPv4 VPS 买家来说，这意味着不能单纯看“一个月多少钱”。

例如同样是 4 vCore、4GB 内存，LAX 的不同网络系列可能分别给出 5TB、10TB、14TB 或其他传输额度，而且价格也不同。当前官方 Pricing 页面同时展示了这些组合，并特别提醒产品和价格可能因调整存在更新滞后。

### IPv4 数量也不是所有方案都完全一样

目前公开可核实的 DMIT 产品资料显示，很多云实例配置提供 **1 IPv4 + 1 个 IPv6 /64**；较高规格的实例则可能配到多个 IPv4。例如当前公开的 LAX AN5 Premium 产品资料中，TINY、Pocket、STARTER、MINI、MICRO 为 1 个 IPv4，而更高规格可能出现 2 个甚至 3 个 IPv4。

这点非常重要：如果你只是运行个人网站、代理节点、测试环境或 API，1 个 IPv4 一般就已经解决核心问题；如果你需要多个独立出口地址，就不能默认认为“升级 CPU”会自动得到更多 IPv4，应该在订单页面确认最终 IP 数量。

## 当前公开套餐怎么选

为了避免把 Pricing 页面里不同历史组合的重复展示误认为完全不同的产品，我下面优先列出 DMIT 当前 Cloud Instance 页面**有明确产品 ID、规格和价格的公开套餐**。官方这页把它定义为热门配置精选，同时明确提示价格会调整；因此下单前仍应以订单页面显示值为准。

### 全套餐对比表

| 地区 / 产品 | 核心配置 | 存储 | 流量 | 端口 | 当前公开价格 | 购买 |
| --- | --- | ---: | ---: | ---: | ---: | --- |
| LAX.AN5.Pro.MINI | 4 vCore / 4GB | 80GB SSD | 5000GB | 10Gbps | $79.90/月 | [ 查看 LAX AN5 Premium](https://bit.ly/DmiT) |
| LAX.AN5.Pro.MICRO | 4 vCore / 4GB | 160GB SSD | 7000GB | 10Gbps | $110.90/月 | [ 查看 LAX AN5 Micro](https://bit.ly/DmiT) |
| LAX.AN5.Pro.MEDIUM | 6 vCore / 8GB | 160GB SSD | 15000GB | 10Gbps | $289.90/月 | [ 查看 LAX AN5 Medium](https://bit.ly/DmiT) |
| LAX.AN5.EB.MINI | 4 vCore / 4GB | 80GB SSD | 10000GB | 10Gbps | $79.90/月 | [ 查看 LAX AN5 EB](https://bit.ly/DmiT) |
| LAX.AN5.EB.MICRO | 4 vCore / 4GB | 160GB SSD | 14000GB | 10Gbps | $110.90/月 | [ 查看 LAX AN5 EB Micro](https://bit.ly/DmiT) |
| LAX.AN5.EB.MEDIUM | 6 vCore / 8GB | 160GB SSD | 30000GB | 10Gbps | $289.90/月 | [ 查看 LAX AN5 EB Medium](https://bit.ly/DmiT) |
| LAX.AN5.T1.V2C2G | 2 vCore / 2GB | 40GB SSD | 5000GB Max | 10Gbps | $14.90/月 | [ 查看 LAX T1 V2C2G](https://bit.ly/DmiT) |
| LAX.AN5.T1.V2C4G | 2 vCore / 4GB | 80GB SSD | 10000GB Max | 10Gbps | $23.90/月 | [ 查看 LAX T1 V2C4G](https://bit.ly/DmiT) |
| LAX.AN5.T1.V4C4G | 4 vCore / 4GB | 120GB SSD | 20000GB Max | 10Gbps | $36.90/月 | [ 查看 LAX T1 V4C4G](https://bit.ly/DmiT) |
| HKG.AS3.Pro.STARTER | 1 vCore / 2GB | 40GB SSD | 1000GB | 1Gbps | $79.90/月 | [ 查看香港 Premium Starter](https://bit.ly/DmiT) |
| HKG.AS3.Pro.MINI | 2 vCore / 4GB | 60GB SSD | 1500GB | 1Gbps | $126.90/月 | [ 查看香港 Premium Mini](https://bit.ly/DmiT) |
| HKG.AS3.Pro.MICRO | 4 vCore / 4GB | 80GB SSD | 2000GB | 1Gbps | $179.90/月 | [ 查看香港 Premium Micro](https://bit.ly/DmiT) |
| HKG.AS3.EB.STARTERv2 | 1 vCore / 2GB | 40GB SSD | 2000GB | 2Gbps | $59.90/月 | [ 查看香港 EB Starter](https://bit.ly/DmiT) |
| HKG.AS3.EB.MINIv2 | 2 vCore / 2GB | 60GB SSD | 3000GB | 2Gbps | $89.90/月 | [ 查看香港 EB Mini](https://bit.ly/DmiT) |
| HKG.AS3.EB.MICROv2 | 4 vCore / 4GB | 80GB SSD | 4000GB | 4Gbps | $129.90/月 | [ 查看香港 EB Micro](https://bit.ly/DmiT) |
| HKG.AS3.T1.STARTER | 1 vCore / 2GB | 40GB SSD | 4000GB Max | 未在当前页面独立列出 | $12.90/月 | [ 查看香港 T1 Starter](https://bit.ly/DmiT) |
| HKG.AS3.T1.MINI | 2 vCore / 2GB | 60GB SSD | 8000GB Max | 未在当前页面独立列出 | $21.90/月 | [ 查看香港 T1 Mini](https://bit.ly/DmiT) |
| HKG.AS3.T1.MICRO | 4 vCore / 4GB | 80GB SSD | 16000GB Max | 未在当前页面独立列出 | $32.90/月 | [ 查看香港 T1 Micro](https://bit.ly/DmiT) |
| TYO.AS3.Pro.STARTER | 1 vCore / 2GB | 40GB SSD | 1000GB | 1Gbps | $45.90/月 | [ 查看东京 Premium Starter](https://bit.ly/DmiT) |
| TYO.AS3.Pro.MINI | 2 vCore / 4GB | 60GB SSD | 2000GB | 1Gbps | $89.90/月 | [ 查看东京 Premium Mini](https://bit.ly/DmiT) |
| TYO.AS3.Pro.MICRO | 4 vCore / 4GB | 80GB SSD | 4000GB | 1Gbps | $189.90/月 | [ 查看东京 Premium Micro](https://bit.ly/DmiT) |
| TYO.AS3.T1.STARTER | 1 vCore / 2GB | 40GB SSD | 4000GB Max | 未在当前页面独立列出 | $12.90/月 | [ 查看东京 T1 Starter](https://bit.ly/DmiT) |
| TYO.AS3.T1.MINI | 2 vCore / 2GB | 60GB SSD | 8000GB Max | 未在当前页面独立列出 | $21.90/月 | [ 查看东京 T1 Mini](https://bit.ly/DmiT) |
| TYO.AS3.T1.MICRO | 4 vCore / 4GB | 80GB SSD | 16000GB Max | 未在当前页面独立列出 | $32.90/月 | [ 查看东京 T1 Micro](https://bit.ly/DmiT) |

以上配置和价格来自 DMIT 当前 Cloud Instance 页面。页面明确写明这些是精选热门配置，而 Pricing 页面还展示了更多按地点、网络和硬件组合排列的价格区块；官方同时提醒公开价格可能因调整存在滞后，因此购买时应把结算页视为最终价格。

## 想要便宜的 IPv4 VPS，Tier 1 值得先看

单纯搜索“IPv4 VPS”的用户里，有相当一部分并不需要中国大陆专线。

如果服务器主要用于美国本土网站、个人项目、开发测试、CI/CD、监控、备份或者普通全球 API，那么高价 Premium 线路未必有必要。

DMIT 自己对 Tier 1 的定位也很明确：它主要提供亚太、北美和欧洲之间的常规优化路由，不针对中国大陆做专门线路优化，适合备份、归档、DevOps、VPN/中继和成本敏感型计算任务。

以 LAX AN5 Tier 1 为例，当前公开配置里：

**V2C2G 为 $14.90/月**，2 vCore、2GB RAM、40GB SSD、5000GB 双向计量流量上限、10Gbps 端口；V2C4G 为 $23.90/月；V4C4G 为 $36.90/月。

这里有一个很容易忽略的差别：

Premium 的价格更高，换来的不是“IPv4 本身”，而主要是**网络路径**。

所以你买的是 IPv4 VPS，不代表就应该自动选 Premium。

## 什么时候需要 Premium

如果你的用户集中在中国大陆，或者业务需要频繁往返中国大陆与美国、香港、日本，那么线路的重要性会上升。

DMIT 当前对 Premium Network 的定义是使用 Tier 1 传输与高级线路合作伙伴，其中包括自己的骨干网络以及 China Telecom CN2 GIA。官方还给出了针对中国大陆的参考指标，例如洛杉矶位置的平均延迟约 15ms、丢包低于 0.1%，同时强调这些都是参考值，会受到实际访问网络、路线和时间的影响。

这类数据应该怎么理解？

不要把它理解成“我的电脑访问这台服务器一定就是 15ms”。官方自己已经注明，延迟会随访问网络、路由和时间变化。

真正值得关注的是：**DMIT 把不同线路作为不同产品售卖，而不是把所有 VPS 都放进一个普通 BGP 出口里。**

对于跨太平洋业务，这个区别比多 1GB RAM 或多几十 GB SSD 更值得核对。

[👉 查看 DMIT 当前 Premium VPS 配置](https://bit.ly/DmiT)

## 香港和东京的 IPv4 VPS，为什么不能只看月租

香港目前公开的 AS3 Premium 方案从 STARTER、MINI 到 MICRO，价格分别是 $79.90、$126.90 和 $179.90/月；对应 1、2、4 vCore 等不同规格，端口统一为 1Gbps。

东京 Premium 当前公开的 AS3 方案则从 STARTER 的 $45.90/月起，到 MINI 的 $89.90/月和 MICRO 的 $189.90/月；这些方案同样是 1Gbps 端口。

为什么香港比东京贵很多？

至少从官方公开的产品结构来看，香港和东京并不是简单地复制同一个套餐然后换机房名字。不同节点的网络、规格、可用产品以及价格本身就是独立设计的。

因此选择地点时，建议先问自己一个非常实际的问题：

**你的主要访问者在哪？**

美国用户为主，LAX 往往更直观；东亚用户为主，东京或香港可能更合适；中国大陆访问量很高，则应该重点比较 Premium 和 Eyeball，而不能只拿月租最低的 Tier 1 对照价格。

## Eyeball 线路是干什么的

Eyeball 是 DMIT 当前网络分类里一个很有意思的中间选项。

官方把它描述为 Tier 1 加上通过 CMIN2 等中国网络的合理努力路由，在成本和中国访问体验之间做平衡。它并不提供 Premium 那样的路由保障，但定位明显不是“普通国际线路”。

这意味着，如果你的 IPv4 VPS 面向的是“全球用户 + 一定比例中国大陆用户”，Eyeball 有一定现实意义。

不过这里也有一个重要限制：DMIT 当前页面明确说明，**香港 Eyeball 仍处于 Beta**，线路和表现仍在调优，因此对于需要高稳定性的生产环境，官方目前并不建议把它作为生产方案。

这类状态信息比“某个博主说它很快”更值得买家注意。

## IPv4 VPS 的流量限制，比端口速率更值得看

很多 VPS 商品页最醒目的数字是 1Gbps、4Gbps、10Gbps。

但实际长期使用时，流量额度通常更容易成为硬限制。

例如 LAX AN5 Tier 1 的 V2C2G 是 5000GB Max（IN, OUT），V2C4G 是 10000GB，V4C4G 是 20000GB；而 General 系列的流量结构又不同。

同样是 10Gbps 端口，不能简单理解为“一个月就能随便跑 10Gbps”。

官方也明确解释过，页面里的带宽数字是理想条件下的最大聚合能力，并且会根据实际网络运行情况调整。

另外，DMIT 的服务条款写明：如果超过套餐的月度带宽额度，可以选择重置、暂停或者限速；同时 Fair Use Policy 允许 DMIT 在认定用量不符合正常公平使用模式时进行限速、调整带宽价格或者暂停/终止服务。

这对文件分发、下载站、长期大流量代理和备份任务尤其重要。

## 一个 IPv4 VPS 用来跑什么比较合适

### 网站和 API

这是最典型的用途。

如果网站主要面向美国用户，1 个公网 IPv4、2GB 左右内存、2 vCore 级别的方案就能覆盖大量轻量业务场景。真正决定体验的通常是应用本身、数据库配置、缓存和访问线路，而不是单看端口写着多少 Gbps。

### 开发和测试环境

这种场景通常没必要花钱买 Premium。

需要的是稳定 SSH、root 权限、足够 RAM、快一点的存储，以及一个固定公网 IPv4。DMIT 当前 Cloud Instance 页面提供 Ubuntu、Debian、CentOS、CentOS Stream、AlmaLinux、Rocky Linux、Fedora、openSUSE Leap、Arch Linux 和 Alpine Linux 等系统选项，同时支持 SSH Key 登录。

### VPN、代理和中继节点

技术上当然可以使用 VPS 的公网 IPv4，但这里必须注意运营商条款、Fair Use 和具体业务类型。

DMIT 官方目前把 VPN、proxy 和 relay nodes 本身列为 Tier 1 网络的推荐使用场景之一，同时也提醒公平使用政策适用于 VPS。

所以，“能不能部署”与“适不适合长期高流量部署”是两个问题。

### 面向中国大陆用户的应用

这时候更应该关注 Premium 与 Eyeball，而不是只看 IPv4。

DMIT 当前网络说明里明确区分了中国 Telecom、Unicom 和 Mobile 相关互联，以及 CN2 GIA、CMIN2/CMI 等不同线路。

如果你的业务对跨境延迟或丢包敏感，建议把线路类型放在 CPU 之前比较。

## IPv4 VPS 购买前，几个限制必须看

> **不要把“1 IPv4 + IPv6 /64”理解成可以无限申请多个 IPv4。** 当前公开产品资料显示不少方案默认提供 1 个 IPv4，但高规格实例可能拥有多个 IPv4；具体数量必须以目标产品订单页为准。

> **Tier 1 的 IPv4 存在地区可用性限制。** DMIT 当前 Pricing 页面明确提醒，Tier 1 系列分配的 IP 地址不保证在所有国家或地区都可用。

> **AS3 不是所有节点都处于相同状态。** DMIT 当前特别提示 LAX AS3 仍在建设和优化阶段，可能出现较低的磁盘性能和较低的 SLA。

这三个限制，对 IPv4 VPS 用户都非常实际。

尤其是 IP 地理位置。有些应用、服务商和区域访问规则会根据 IPv4 的地理定位做判断。DMIT 的退款 FAQ 也明确把“IP geographic location reason”列为不可退款的情况之一，因此不要默认购买后发现 IP 地理位置不符合预期就一定可以无条件退回。

## DMIT 有优惠码吗

这里反而建议谨慎。

我能确认当前官方价格页面本身明确展示的是实时套餐价格；搜索到的第三方优惠页面确实存在各种所谓的“2026 优惠码”，但其中部分互相冲突，而且无法从当前 DMIT 官方优惠页面独立验证全部代码仍然有效。

因此，**没有在当前官方页面重新验证成功的优惠码，不应该直接写成“当前有效优惠码”**。

这比随便塞一个网上流传的 coupon code 安全得多。

你可以先从当前 AFF 入口进入购买页面，再在结算阶段检查是否有官方可用促销或折扣字段：

[👉 查看当前 DMIT IPv4 VPS 价格](https://bit.ly/DmiT)

## DMIT 的退款和支持政策，也值得一起看

DMIT 当前退款 FAQ 比许多 VPS 比较文章写得更明确。

官网写明，符合条件时可以在购买后 3 天内申请全额退款，前提包括 VM 流量使用不超过 30GB；30 天内则可能适用按剩余价值计算的部分退款。退款还会扣除支付网关交易费用。

同时存在一些不退款情形，例如曾经在同一产品系列退款达到规定次数、遭遇 DDoS、网络质量问题、IP 地理位置原因，以及部分其他情况。

支持方面，DMIT 文档目前说明普通工单通常在 24 小时内处理，最大可能达到 72 小时；节假日和需要深入调查的技术问题可能更久。

这意味着它更像一个**自助式 VPS/云实例服务**，而不是替你维护 Linux 环境的托管主机。

## 第三方评价怎么看

这一部分尤其需要克制。

目前能查到的公开评价数量并不算多，而且评价之间差异很明显。例如 Trustpilot 当前显示 DMIT 的 TrustScore 为 2.6/5，共 4 条评价，其中 3 条来自最近 12 个月；近期评价中有人提到网络中断、UDP 连接问题和退款争议，但样本非常小，Trustpilot 自己也明确提醒这些评价可能不具代表性。

另一方面，部分 2026 年第三方测评文章对 DMIT 的关注点主要集中在其跨太平洋线路、AMD EPYC 平台和区域选择上。也有评测明确提醒，应该把实际产品、地区、路由、资源和退款条件逐项确认，而不要把线路名称本身当成实际性能保证。

所以这里最稳妥的做法不是简单计算“好评率”，而是看评价与你的场景是否一致。

一个需要中国大陆访问优化的业务，应该重点看网络路线；

一个只需要美国 IPv4 和固定公网地址的小项目，则没必要因为某条跨境线路的评价而做完全相同的判断。

## 买哪种 IPv4 VPS，可以这样判断

如果你的核心需求是“**一台有公网 IPv4 的 VPS，主要服务美国或全球用户**”，可以先从 Tier 1 看起。当前 LAX AN5 Tier 1 的 V2C2G 月租 $14.90，已经提供 2 vCore、2GB RAM、40GB SSD 和 5000GB Max 流量。

如果你的核心需求变成“**IPv4 + 更关注中国大陆访问质量**”，再比较 Premium 与 Eyeball。

如果你的需求是“**香港或东京本地部署**”，则应该直接比较 HKG/TYO 的具体产品，不要拿 LAX 的月租横向判断。

如果你只是做测试，甚至不确定自己未来需要多少流量，那么月付比直接锁定长期周期更容易控制风险。特别是 DMIT 的价格页自己就注明数据可能因调整而延迟，先确认目标产品的实际价格、IPv4 数量和地区可用性，比追求一个看起来很漂亮的长期折扣更重要。

## 最后，真正购买 IPv4 VPS 时只确认这 6 件事

**公网 IPv4 数量。** 不要只看标题，要看目标 SKU 的具体 IP 数量。

**IPv4 地理位置。** 尤其是需要固定国家/地区出口时。

**流量计算方式。** `Max (IN, OUT)` 与普通月度流量不是完全一样的表达方式。

**线路类型。** Premium、Eyeball、Tier 1 对跨境业务的意义不同。

**超额后的处理。** DMIT 条款允许重置、暂停或限速，并保留 Fair Use 下进一步处理的权利。

**退款窗口。** 购买后 3 天、30GB 以内的全额退款条件，以及其他不退款情形，都应该在付款前看清。

对于“IPv4 VPS”这个关键词来说，真正需要买的不是一个漂亮的参数表，而是一台**IPv4 数量、地区、流量和线路都与你的实际用途匹配的服务器**。

DMIT 当前产品线最值得核对的地方，恰恰就是这几个维度。先确定访问者在哪，再确定线路；先确定每月需要多少流量，再决定 CPU 和内存；最后才看月租差多少。这样选出来的 IPv4 VPS，通常比单纯盯着“最低价格”更不容易买错。

[👉 从 DMIT 当前 AFF 入口查看可购买的 IPv4 VPS 方案](https://bit.ly/DmiT)
