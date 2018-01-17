# Quantumult

### Quantumult Unofficial Manual
---

## 目录
* [1.前言](#前言)
* [2.FAQ](#FAQ)
    * Quantumult有什么优势，我有其它工具为什么要买这个？
    * Quantumult的规则为何和其它的工具不一样，应该怎么理解规则中的关键字？
    * Quantumult内置的基本策略有什么，出站方式有什么？
    * Quantumult的策略组都是什么含义？
    * Quantumult不用策略组能用节点测速么？
* [3.基础配置方式](#基础配置方式)
    
---

### 前言

本文献给将要购买Quantumult或者已经购买Quantumult使用中遇到问题的人。
    
如果有什么不对的地方还请你不要喷我，毕竟我也仅仅是一个用户而已。
    
如果你使用中有疑问可以请教别人，也可以发issue邮件给作者。但是还是推荐你先自己琢磨一下，没准问题就解决了。

**`注意：本文撰写时是使用的TestFlight版本Build393，如果跟你手上的版本不一样请等待商店正式版`**

---

### FAQ

* Q：Quantumult有什么优势，我有其它工具为什么要买这个？

A：Quantumult稳定性不错，不输于任何其它同类软件。

Quantumult内置了规则订阅机制，可以方便的订阅规则，可以在导入规则的时候完成快速更改分流策略并且不需要借助其它工具（前提是规则配置支持此项操作）。

Quantumult支持多组策略，可以实现多组分流共存，手动选择策略组出站模式。

至于为什么要买，这个就看个人需求吧。

* Q：Quantumult的规则为何和其它的工具不一样，应该怎么理解规则中的关键字？

A：Quantumult的规则关键字其实本质的含义还是和其它工具类似的，我这里列举一下大家可以看一下。

HOST等同于DOMAIN ：匹配请求的域名

例如：HOST，instagram.com，Proxy 匹配instagram.com的域名，走代理。

HOST-SUFFIX 等同于 DOMAIN-SUFFIX ：匹配请求的域名后缀

例如：HOST-SUFFIX，image.instagram.com，Proxy 匹配域名后缀为：image.instagram.com的域名，走代理。

HOST-KEYWORD 等同于 DOMAIN-KEYWORD：匹配域名中包含的关键字。

例如：DOMAIN-KEYWORD， instagram， Proxy 匹配包含 instagram 关键词的域名，走代理。

IP-CIDR：匹配处在给定域内的 IP。

例如 IP-CIDR， 17.0.0.0/8， Proxy 匹配IP域17.0.0.0/8 走代理。

GEOIP： 匹配给定地理区域内的 IP。

例如 GEOIP， CN， DIRECT 匹配中国IP走直连。

USER-AGENT：特殊字符串头匹配（可以理解为应用名）。

例如：USER-AGENT，QQ*，DIRETC 匹配应用名包含QQ关键字的应用，走直连。


* Q：Quantumult内置的基本策略有什么，出站方式有什么？

A：Quantumult内置了三种基本策略

PROXY：走代理服务器

DIRECT：直接连接

REJECT：拒绝访问

Quantumult的出站方式有三种

GLOBAL：全部出站流量走代理服务器，不管你规则怎么写都会走代理服务器。

AUTO：出站流量按照规则配置自动规划出站路径。

DIRECT：全部出站流量走直接连接，不管你规则怎么写都会走直接连接。

* Q：Quantumult的策略组都是什么含义？

A：Service Set Identifier Policy：此组可以给Wi-Fi和流量指定不同的策略(可以是静态策略，也可以是节点测速)或节点或者内置基础策略(PROXY DIRECT REJECT)。也可以针对不同的Wi-Fi SSID名称指定不同配置方式。

Latency Policy：此组是节点测速分组，可以选择多个节点，根据测速结果选择最优节点使用。

Static Policy：此组是静态策略分组，可以选择 SSID分组 Auto分组或者任意节点，也可以选择内置基础策略(PROXY DIRECT REJECT)。使用时，手动选择需要的策略即可。

在规则中，可以指定以上三种策略的名称以应对不同的应用场景。

* Q：Quantumult不用策略组能用节点测速么？

A：可以，Quantumult提供了简易的测速机制，可以在不使用策略组的情况下开启最多10个节点测速并选择最优节点使用。开启方式在Settings→Policy→PROXY→URL Latency Test中配置。这种方式规则中需要走节点服务器的网址配置为PROXY即可，这种配置方式相对简单能满足大部分人的需求，如果不想开启策略组或者对策略组不是很了解的人，推荐使用这种配置方式。

---

### 基础配置方式

   * 初次打开Quantumult所显示的页面
