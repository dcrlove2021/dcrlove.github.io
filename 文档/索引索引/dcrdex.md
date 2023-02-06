# decred社区资助开发的去中心化【原子交换】交易所

## 1.自托管：硬币始终托管在您的本地钱包。
## 2.隐私：交易环节隐私
## 3.开源：交易所代码完全开源
## 4.公平：不会像中心化交易所有大量内幕交易和虚假交易!


---
这是dcrdex官网
https://dex.decred.org/ 

## 相关开发人员的介绍视频
<iframe src="//player.bilibili.com/player.html?aid=968306370&bvid=BV1Lp4y1X7ED&cid=193748971&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>

# <img src="docs/images/logo_wide_v1.svg" alt="DCRDEX" width="250">


# 下面引用的是开源项目的自述文件（机器翻译的)

[![构建状态](https://github.com/decred/dcrdex/workflows/Build%20and%20Test/badge.svg)](https://github.com/decred/dcrdex/actions)
[![ISC 许可证](https://img.shields.io/badge/license-Blue_Oak-007788.svg)](https://blueoakcouncil.org/license/1.0.0)
[![GoDoc](https://img.shields.io/badge/go.dev-reference-blue.svg?logo=go&logoColor=lightblue)](https://pkg.go.dev/decred.org/ dcrdex）

## 什么是 DEX？

Decred 去中心化交易所 (DEX) 是一个支持无信任的系统
通过熟悉的基于市场的方式交换不同类型的区块链资产
应用程序接口。DEX是一种非托管的跨链交换解决方案，基于
原子交换技术。DEX匹配交易方并促进价格
交换细节的发现和交流。

匹配是通过熟悉的交易界面进行的，市场和
限价订单和订单簿。结算发生在链上。DEX 的 epoch-based
匹配算法和社区行为规则确保订单簿
您看到的动作是真实的，而不是机器人大军。

用户之间通过链上合约直接进行交易，无需
对 DEX 的实际依赖，尽管必须将交换详细信息报告为
礼貌并证明遵守交易规则。交易结算
纯粹的 4 笔交易原子互换，仅此而已。因为 DEX 不收
交易费用，没有中介代币，也没有费用交易。

虽然不收取交易手续费，但DEX确实需要一次性
注册费在链上支付。原子交换技术保护所有交易，
但客户端软件仍必须遵守一套策略以确保有序
比赛结算。DEX 可施加的最高处罚是交易损失
特权和没收注册费。

＃＃ 内容

- [入门](#getting-started)
- [重要事项](#important-stuff-to-know)
- [费用](#fees)
- [DEX 规范](#dex-specification)
- [贡献](#contribute)
- [来源](#source)

＃＃ 入门

要开始使用 DEX 进行交易，您需要客户端应用程序。有一个
获取软件的几个简单选项：

1. 下载适用于您的操作系统的独立 DEX 客户端
   [GitHub 上的最新版本](https://github.com/decred/dcrdex/releases)。
2. [使用Decrediton](https://docs.decred.org/wallets/decrediton/decrediton-setup/),
   官方图形化 Decred 钱包，集成了 DEX 客户端，然后去
   到 DEX 选项卡。
3. 使用 Decred 命令行应用程序安装程序，[**dcrinstall**](https://docs.decred.org/wallets/cli/cli-installation/)，
   使用 `--dcrdex` 开关。
4. [来自源代码](https://github.com/decred/dcrdex/wiki/Client-Installation-and-Configuration#advanced-client-installation) 构建独立客户端。

参见【客户端安装配置】(https://github.com/decred/dcrdex/wiki/Client-Installation-and-Configuration)
wiki 上的页面以获取更多信息和初始设置的详细演练。

几乎每个人都只希望客户在现有市场上进行交易，但如果
你想设置一个新的 DEX 服务器和你选择的托管市场，请参阅
[服务器安装](https://github.com/decred/dcrdex/wiki/Server-Installation)。

## 重要事项

交易在链上结算并需要区块确认。交易不会立即结算。
在某些情况下，它们可能需要几个小时才能解决。
**在您完全确定您的交易已经结算之前，不应关闭客户端软件**。

**客户必须在整个交易结算期间保持连接**。
失去连接几分钟是可以的，但不要推动它。
贸易结算期间互联网连接中断超过 20 小时有可能导致资金损失。
仅仅失去与 DEX 服务器的连接不会使资金面临风险。
您将不得不失去与整个区块链网络的连接。

**最初您可以订购的数量有限制**。
我们很快就会在某个地方显示这些限制，但与此同时，
从一些较小的订单开始，以建立您的声誉。当你完成
订单，您的限额将上升。

**如果您在订单匹配时未能完成掉期**，您的账户
将累积可能导致您的帐户自动成为的罢工
暂停。这些情况并不总是故意的（例如长时间失去
互联网访问、计算机崩溃等），因此如需技术帮助，请
伸手
[关于 Matrix](https://matrix.to/#/!mlRZqBtfWHrcmgdTWB:decred.org?via=decred.org&via=matrix.org)。

＃＃ 费用

DEX 不对交易收取任何费用，但由于所有掉期交易
发生在链上并由用户直接创建，他们将支付网络
交易费用。交易费用因订单匹配方式而异。费用
估计在订单创建期间显示，并显示已实现的费用
在订单详情页面上。

确保链上交易费用不会占用很大一部分
订单数量，订单必须以最小手数为增量指定。
举个例子，如果链上交易费用为 5 美元，并且用户能够
下订单交易 10 美元，他们将损失一半的交易给
交易费用。对于单场比赛费用为 5 美元的连锁店，如果运营商愿意
为了将可能的费用限制在交易的 1% 以下，需要最小手数
将设置为大约 500 美元。

费用最低的场景是整个订单被
单场比赛。如果发生这种情况，用户需要支付两笔交易的费用：一笔
在用户正在出售的资产的链上和一个在资产的链上
用户正在购买。最坏的情况是订单被多次填写
匹配每一手的数量，可能需要与手数一样多的掉期
按顺序。
检查
[dex 规范](https://github.com/decred/dcrdex/blob/master/spec/atomic.mediawiki)
有关原子交换如何工作的更多详细信息。

## 去中心化交易所规范

[DEX 规范](spec/README.mediawiki) 详细介绍了消息传递和交易
使用 Market API 所需的协议。代码不仅在
在 **decred/dcrdex** 存储库开源，但整个协议是
开源。所以原则上任何人都可以编写自己的客户端或基于服务器的
在规范上。这样的努力在这些早期是不明智的
阶段，而协议正在不断变化。

＃＃ 贡献

**希望做出贡献？我们需要您的帮助**才能使 DEX 排名第一。

几乎所有的开发都是用 Go 和 JavaScript 完成的。工作协调
通过[回购问题](https://github.com/decred/dcrdex/issues)，
所以这是最好的起点。
在开始工作之前，请在
[DEX 开发室](https://matrix.to/#/!EzTSRQITaqHuFBDFhM:decred.org?via=decred.org&via=matrix.org&via=zettaport.com)。
现在的发展速度非常快，所以你应该保持
您的拉取请求正在通过审查过程。

查看这些 wiki 页面以获取更多信息。

- [开始贡献](../../wiki/Contribution-Guide)
- [后端开发](../../wiki/Backend-Development)
- [在 simnet 上运行 **dcrdex** 和 **dexc**](../../wiki/Simnet-Testing)。推荐用于开发。
- [在测试网上运行 **dexc**](../../wiki/Testnet-Testing)。推荐四处闲逛。
- [运行测试应用服务器](../../wiki/Test-App-Server)。对于 GUI 开发很有用，或者只是在不需要创建钱包或连接到 **dcrdex** 服务器的情况下尝试一切。

＃＃ 来源

DEX [规范](spec/README.mediawiki) 是根据利益相关者起草的
的批准
[规范提案](https://proposals.decred.org/proposals/a4f2a91c8589b2e5a955798d6c0f4f77f2eec13b62063c5f4102c21913dcaf32)。

DEX 服务器和客户端的源代码正在根据
规范。该承诺通过第二个 DEX 获得批准
[开发提案](https://proposals.decred.org/proposals/417607aaedff2942ff3701cdb4eff76637eca4ed7f7ba816e5c0bd2e971602e1)。

## 常见问题解答

- 如何整合新资产？要添加新资产，请按照 [此处](https://github.com/decred/dcrdex/blob/master/spec/fundamentals.mediawiki/#adding-new-assets) 的说明进行操作，并查看现有实施 [此处](https //github.com/decred/dcrdex/tree/master/server/asset）。
