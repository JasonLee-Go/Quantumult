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
    * 为什么我Quantumult点击启动时会有提示?
* [3.基础配置方式](#基础配置方式)
    * 添加节点
    * 订阅及更新节点
    * 订阅及更新规则
    * 订阅及更新Rejection
    * 开启MitM
* [4.进阶教程](#进阶教程)
    * Policy介绍与配置
    * 切换节点(暂未添加)
    * 规则分流(暂未添加)
    * 查看节点生效情况(暂未添加)
    * 服务器ping测试(暂未添加)
    
---

### 前言

本文献给将要购买Quantumult或者已经购买Quantumult使用中遇到问题的人。
    
如果有什么不对的地方还请你不要喷我，毕竟我也仅仅是一个用户而已。
    
如果你使用中有疑问可以请教别人，也可以发issue邮件给作者。但是还是推荐你先自己琢磨一下，没准问题就解决了。

作者邮箱 [quantumult@gmail.com](quantumult@gmail.com) 有问题反馈可以给作者发邮件.

申请TF需要附上购买收据,并在邮件标题注明申请TF。

**`注意：本文撰写时是使用的TestFlight版本Build400，如果跟你手上的版本不一样请等待商店正式版`**

---

### FAQ

* **Q**：Quantumult有什么优势，我有其它工具为什么要买这个？

    **A**：Quantumult稳定性不错，不输于任何其它同类软件。

    Quantumult内置了规则订阅机制，可以方便的订阅规则，可以在导入规则的时候完成快速更改分流策略并且不需要借助其它工具（前提是规则配置支持此项操作）。

    Quantumult支持多组策略，可以实现多组分流共存，手动选择策略组出站模式。

    Quantumult支持UDP Relay 及 UDP代理转发,有玩外服手游的小伙伴应该知道这个功能的重要性。

    至于为什么要买，这个就看个人需求吧。

* **Q**：Quantumult的规则为何和其它的工具不一样，应该怎么理解规则中的关键字？

    **A**：Quantumult的规则关键字其实本质的含义还是和其它工具类似的，我这里列举一下大家可以看一下。

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


* **Q**：Quantumult内置的基本策略有什么，出站方式有什么？

    **A**：Quantumult内置了三种基本策略

    PROXY：走代理服务器

    DIRECT：直接连接

    REJECT：拒绝访问

    Quantumult的出站方式有三种

    GLOBAL：全部出站流量走代理服务器，不管你规则怎么写都会走代理服务器。

    AUTO：出站流量按照规则配置自动规划出站路径。

    DIRECT：全部出站流量走直接连接，不管你规则怎么写都会走直接连接。

* **Q**：Quantumult的策略组都是什么含义？

     **A**：Service Set Identifier Policy：此组可以给Wi-Fi和流量指定不同的策略(可以是静态策略，也可以是节点测速)或节点或者内置基础策略(PROXY DIRECT REJECT)。也可以针对不同的Wi-Fi SSID名称指定不同配置方式。

    Latency Policy：此组是节点测速分组，可以选择多个节点，根据测速结果选择ping值最低的节点使用(注意Latency Policy并不能检测节点带宽,只能检测节点ping值,建立此组时请根据自身节点实际情况自行添加)。

     Static Policy：此组是静态策略分组，可以选择 SSID分组 Auto分组或者任意节点，也可以选择内置基础策略(PROXY DIRECT REJECT)。使用时，手动选择需要的策略即可。

     在规则中，可以指定以上三种策略的名称以应对不同的应用场景。

* **Q**：Quantumult不用策略组能用节点测速么？

    **A**：可以，Quantumult提供了简易的测速机制，可以在不使用策略组的情况下开启最多10个节点测速并选择最优节点使用。开启方式在Settings→Policy→PROXY→URL Latency Test中配置。这种方式规则中需要走节点服务器的网址配置为PROXY即可，这种配置方式相对简单能满足大部分人的需求，如果不想开启策略组或者对策略组不是很了解的人，推荐使用这种配置方式。

* **Q**:为什么我Quantumult点击启动时会有提示?

<div align=center><img src="https://raw.githubusercontent.com/JasonLee-Go/Quantumult/master/IMG_2923.JPG"/></div>

   **A**:这个提示是因为你没有信任证书,可以参考本手册的 **开启MitM(HTTPS)** 章节开启证书信任.
   还有一种提示是没有安装证书,同样可以在 **开启MitM(HTTPS)** 章节中找到答案.

---

### 基础配置方式

* 首页 

   初次打开Quantumult所显示的页面

<div align=center><img src="https://raw.githubusercontent.com/JasonLee-Go/Quantumult/master/IMG_2845.JPG"/></div>


**本页面各选项卡说明**

    Home (主页面 显示连接状态 连接时间 流量使用情况 节点信息等信息)
    Settings (设定页面 添加节点 订阅设定 规则列表 UDP Relay等)
    Statistics (状态显示页面 显示浏览历史 详细流量使用情况 策略组状态 服务器延迟统计等)
    More (更多选项 显示其它信息 联系作者 备份 辅助设定等)

* 添加节点
	 
   添加节点共有4种方式 扫码添加 URL添加 手动添加 节点订阅

   本结只讲前三种方式,节点订阅放于订阅界面说明。

   添加节点请选择Settings界面 Server选项 如下图所示

<div align=center><img src="https://raw.githubusercontent.com/JasonLee-Go/Quantumult/master/IMG_2844.JPG"/></div>

   在Server页面有三种添加节点的方式 下图中红色方框标识的为手动添加 蓝色方框标识的为二维码扫码导入 绿色方框标识的为从URL导入

<div align=center><img src="https://raw.githubusercontent.com/JasonLee-Go/Quantumult/master/IMG_2854.JPG"/></div>

   本节主要讲手动添加节点,二维码扫码和URL添加方式相对简单,就不再介绍了。

   **通过URL添加节点的时候可以一次导入多个节点,如果你的服务商提供了多节点导入连接,那么你可以用URL一次添加所有节点。**
   
   选择手动添加选项会弹出下图

<div align=center><img src="https://raw.githubusercontent.com/JasonLee-Go/Quantumult/master/IMG_2881.JPG"/></div>

   默认为添加SS节点 

   从上往下分别为 接点名 服务器地址 端口号 密码 加密方式 请根据自己的节点情况自行填写,填写完毕后点击Save保存。
   
   图中蓝色方框为开启SS节点 obfs的开关,如果有需要请自行开启。

   如果想要添加SSR节点,请点击图中的红色方框标识处,点击后会弹出如下界面

<div align=center><img src="https://raw.githubusercontent.com/JasonLee-Go/Quantumult/master/IMG_2882.JPG"/></div>

   点击OK进入SSR手动添加界面 点击Cancel留在本页面

   添加SSR节点界面如下图

<div align=center><img src="https://raw.githubusercontent.com/JasonLee-Go/Quantumult/master/IMG_2883.JPG"/></div>

   从上往下分别为 接点名 服务器地址 端口号 密码 加密方式 协议类型 混淆类型 协议参数 混淆参数 请根据自己的节点情况自行填写,填写完毕后点击Save保存。

* 订阅节点信息 规则列表 Https Rejection 
   
   添加节点请选择Settings界面 Favorites选项 如下图所示

<div align=center><img src="https://raw.githubusercontent.com/JasonLee-Go/Quantumult/master/IMG_2912.JPG"/></div>

   点击图中红色方框标识处会弹出选项,选择需要添加的订阅信息

<div align=center><img src="https://raw.githubusercontent.com/JasonLee-Go/Quantumult/master/IMG_2910.JPG"/></div>

   图中绿色方框标出的为添加节点订阅信息 蓝色方框标出的为添加基本规则订阅 红色方框标出的为HTTPS Rejection规则订阅

    节点信息订阅 点击Server选项弹出如下画面

<div align=center><img src="https://raw.githubusercontent.com/JasonLee-Go/Quantumult/master/IMG_2914.JPG"/></div>

   图中 Name填写名字自己随便填写方便识别即可 URL填写节点订阅链接(请咨询你的服务商)

   下方的三个可选框的做用

    Update Option 如果勾选该选项,在更新节点信息时只会更新本地已经添加的节点,新的节点信息不会被更新进来

    Delete Option 如果勾选该选项,在更新节点信息时如果服务器已经将某些节点删除那么本地节点也会被删除

    Additional Option 如果勾选该选项,在更新节点信息时,不会更新本地节点名称
    
   **本页推荐只勾选Delete Option选项其它保持原样不变**

   添加完毕后点击Save保存.

   保存完毕后,在Favorites页面会出现你刚才命名过的节点订阅信息,在订阅信息上向左滑动会有如下提示

<div align=center><img src="https://raw.githubusercontent.com/JasonLee-Go/Quantumult/master/IMG_2899.JPG"/></div>

   图中Remove Server为从本地移除该组订阅的所有节点信息 Update为更新或添加节点订阅 Delete为删除本条订阅(删除本条订阅不会删除已经订阅的节点信息)

   选择Update订阅节点信息,成功后会弹出如下提示,至此节点订阅完成.

<div align=center><img src="https://raw.githubusercontent.com/JasonLee-Go/Quantumult/master/IMG_2907.JPG"/></div>

    基础规则订阅 点击Filter选项弹出如下画面

<div align=center><img src="https://raw.githubusercontent.com/JasonLee-Go/Quantumult/master/IMG_2915.JPG"/></div>

   图中 Name填写订阅名称方便识别即可 URL添加规则地址

   下方复选框作用
    
    Filter Action替换提示说明
    如果你的规则支持Quantumult的替换说明,那么勾选后在应用时会弹出说明,方便分流处理.

   **本页推荐勾选 Filter Action选项**

   推荐订阅规则地址 
[https://raw.githubusercontent.com/lhie1/Surge/master/Quantumult.conf](https://raw.githubusercontent.com/lhie1/Surge/master/Quantumult.conf)

   添加完毕后点击Save保存.

   保存完毕后,在Favorites页面会出现你刚才命名过的规则订阅信息,在订阅信息上向左滑动会有如下提示

<div align=center><img src="https://raw.githubusercontent.com/JasonLee-Go/Quantumult/master/IMG_2909.JPG"/></div>

   图中Append为添加规则(及订阅规则与本地规则合并) Replace为替换规则(及替换本地规则为订阅规则) Delete为删除本条订阅信息
   
   选择Replace会弹出如下图片

<div align=center><img src="https://raw.githubusercontent.com/JasonLee-Go/Quantumult/master/IMG_2913.JPG"/></div>

   图中选项请根据自己的实际情况选择,选择好后点击OK,至此基础规则添加完毕.

    HTTPS Rejection订阅 点击Rejection选项弹出如下画面

<div align=center><img src="https://raw.githubusercontent.com/JasonLee-Go/Quantumult/master/IMG_2916.JPG"/></div>

   图中 Name填写订阅名称方便识别即可 URL添加规则地址

   下方复选框作用

    Including Host Names 添加Rejection规则时同时添加Host Name 列表(如果你订阅的Rejection列表包含Host Name)

   **本页推荐勾选 Including Host Names**

   推荐订阅Rejection地址 
[https://raw.githubusercontent.com/lhie1/Surge/master/Quantumult_URL.conf](https://raw.githubusercontent.com/lhie1/Surge/master/Quantumult_URL.conf)

   添加完毕后点击Save保存.

   保存完毕后,在Favorites页面会出现你刚才命名过的Rejection订阅信息,在订阅信息上向左滑动会有如下提示

<div align=center><img src="https://raw.githubusercontent.com/JasonLee-Go/Quantumult/master/IMG_2908.JPG"/></div>

   图中Append为添加规则(及订阅规则与本地规则合并) Replace为替换规则(及替换本地规则为订阅规则) Delete为删除本条订阅信息
   
   选择Replace 完成后会弹出如下图片,至此Rejection订阅完毕.

<div align=center><img src="https://raw.githubusercontent.com/JasonLee-Go/Quantumult/master/IMG_2906.JPG"/></div>

* 开启MitM(HTTPS)

   选择Settings页面的HTTPS选项卡下图红色方框标出部分

<div align=center><img src="https://raw.githubusercontent.com/JasonLee-Go/Quantumult/master/IMG_2839.JPG"/></div>

   选择后会弹出如下画面

未创建证书如下图

<div align=center><img src="https://raw.githubusercontent.com/JasonLee-Go/Quantumult/master/IMG_2920.JPG"/></div>

已创建未安装证书如下图

<div align=center><img src="https://raw.githubusercontent.com/JasonLee-Go/Quantumult/master/IMG_2919.JPG"/></div>

已安装未信任证书如下图

<div align=center><img src="https://raw.githubusercontent.com/JasonLee-Go/Quantumult/master/IMG_2921.JPG"/></div>

已安装证书并信任如下图

<div align=center><img src="https://raw.githubusercontent.com/JasonLee-Go/Quantumult/master/IMG_2867.JPG"/></div>

   图中红色方框标识处显示当前是否安装并信任了HTTPS证书,我的这个已经安装过了显示的是Root CA Installed&Trusted. 如果是没有安装的话这个地方显示不太一样,下面我讲一下如何安装和信任证书.

   未创建证书的用户需要先创建证书

   首先点击图中蓝色方框标识出的位置(Generate Key&Root Certificate),创建一个新的证书(如果你已经有Surge的证书不想创建新的证书也可以,后面我会讲如何使用Suege的证书.)
   
   然后点击Install CA Root按照系统提示操作安装证书

   如果你已经创建了证书直接安装证书即可

   信任证书 依次点击手机设置 通用 关于本机 证书信任设置 选择你的证书信任即可

<div align=center><img src="https://raw.githubusercontent.com/JasonLee-Go/Quantumult/master/IMG_2922.JPG"/></div>

**注意如果你已经创建了证书并安装,请不要再次点击创建证书,重新创建一个证书原来的证书会失效**

    如何使用Surge已经信任过的证书

    使用Surge已经信任过的证书可以在系统中少创建一个证书,具体操作流程如下

    点击P12-passphraes复制Surge证书的ca-passphraes编号到这里

<div align=center><img src="https://raw.githubusercontent.com/JasonLee-Go/Quantumult/master/IMG_2917.JPG"/></div>

    然后点击P12复制Surge证书的ca-p12到这里

<div align=center><img src="https://raw.githubusercontent.com/JasonLee-Go/Quantumult/master/IMG_2918.JPG"/></div>

### 进阶教程

* Policy介绍与配置
  
   Quantumult里有四种不同的Policy(策略组)

    PROXY Latency Test(默认分组URL Test,在默认PROXY中选择不同的节点进行URL Test选取ping值最低的节点使用.此分组最多只能添加10个节点.)此分组的好处在于,处于测试间隔期间你可以手动选择任何节点使用,到下一次测速周期到来会切换回测速ping值最低的节点.
    
    SSID Policy (SSID策略,可以根据不同的SSID名称选择不同代理方式,直连 拒绝 单独节点 Latency Policy 或 Static Policy)

    Latency Policy (独立URL Test分组,与PROXY Latency Test的机制类似,但是在这个分组中不限制节点数量)此分组不能手动选择节点,只能自动选择Ping值最低的节点使用.

    Static Policy(静态分组,此分组可以添加所有的策略方式,但是在使用时需要手动切换,此分组的主要作用是在不更改配置文件的情况下切换部分网站的代理方式)

   Policy配置实例
   
   **PROXY Latency Test配置**
   
   点击Settings页面 Policy选项进入配置页面

<div align=center><img src="https://raw.githubusercontent.com/JasonLee-Go/Quantumult/master/IMG_2926.JPG"/></div>

   选择红色方框所标识的选项卡,弹出配置界面

<div align=center><img src="https://raw.githubusercontent.com/JasonLee-Go/Quantumult/master/IMG_2930.JPG"/></div>

   点击开关,开始配置,选择好节点后点击Save保存

<div align=center><img src="https://raw.githubusercontent.com/JasonLee-Go/Quantumult/master/IMG_2928.JPG"/></div>

   **SSID Policy配置**

   在Policy页面点击右上角的➕会弹出配置选项,选择下图中红色方框标示处即可
    
<div align=center><img src="https://raw.githubusercontent.com/JasonLee-Go/Quantumult/master/IMG_2929.JPG"/></div>

   进入配置页面后,填写策略名称,然后选择对应的策略.(此策略组可选内置策略(DIRECT REJECT PROXY) Latency Policy 或者 Static Policy 或单独节点)

   Wi-Fi对应在SSID列表以外的无线网络下该策略组走哪个策略

   Celluar对应的是在蜂窝网络环境下该策略组走哪个策略

   点击下方Add SSID Action按钮,会弹出对话框让你填写Wi-Fi名称(默认是你当前已经连接的Wi-Fi名称),填写好后,选择策略即可.(可以添加多个SSID名称)

   配置好后点击Save保存.

<div align=center><img src="https://raw.githubusercontent.com/JasonLee-Go/Quantumult/master/IMG_2925.JPG"/></div>

   **Latency Policy**

   在Policy页面点击右上角的➕会弹出配置选项,选择下图中蓝色方框标示处即可

<div align=center><img src="https://raw.githubusercontent.com/JasonLee-Go/Quantumult/master/IMG_2931.JPG"/></div>

   进入配置页面后,填写策略名称,然后点击Add Server添加需要的服务器节点即可.

   配置好后点击Save保存.

   **Static Policy配置**

   在Policy页面点击右上角的➕会弹出配置选项,选择下图中绿色方框标示处即可

<div align=center><img src="https://raw.githubusercontent.com/JasonLee-Go/Quantumult/master/IMG_2932.JPG"/></div>   

   
   进入配置页面后,填写策略名称,然后点击Add Policy OR Server添加需要的策略或服务器节点.(此策略组可选内置策略(DIRECT REJECT PROXY) Latency Policy 或者 Static Policy 或 单独节点 或 SSID Policy)
   
   配置好后点击Save保存.

**使用策略**

   当你所需要的策略配置完成以后,你需要配置规则列表使策略组生效.

   如果使用PROXY Latency Test那么你的规则列表中代理选项需要选PROXY.

   如果使用其它Policy那么你的规则列表中的代理选项需要选择成相应的策略名.

   替换规则可以使用规则订阅列表Replace替换也可以在Settings页面Filter选项卡里替换.

   在Filter中替换方法为点击进入Filter列表,点击下图中红色方框标识出,弹出替换选项

<div align=center><img src="https://raw.githubusercontent.com/JasonLee-Go/Quantumult/master/IMG_2933.JPG"/></div>  

   在Old Action处填写原来的策略名称,New Action处填写新的策略名称,然后点击OK,替换完成会弹出提示.替换好后,新的策略方式生效.


   
