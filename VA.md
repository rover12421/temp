[![VA banner](https://raw.githubusercontent.com/asLody/VirtualApp/master/Logo.png)](https://github.com/asLody/VirtualApp)

## VA是什么? ##
VirtualApp(简称：VA)是一款运行于Android系统的沙盒产品，可以理解为轻量级的“Android虚拟机”。其产品形态为高可扩展，可定制的集成SDK，您可以基于VA或者使用VA定制开发各种看似不可能完成的项目。VA目前被广泛应用于APP多开、手游境外加速、手游租号、手游手柄免激活、区块链、移动办公安全、军队政府数据隔离、手机模拟信息、脚本自动化、插件化开发、无感知热更新、云控等技术领域。

## VA能做什么？##
1. 可以满足您的**双开/多开**需求    
VA可以让您在同一部手机上安装多个微信/QQ/WhatsApp/Facebook等APP，实现一部手机，多个账号同时登录。  

2. 可以满足您的**移动安全**需求  
VA提供了一整套内部与外部的隔离机制，包括但不限于(文件隔离/组件隔离/进程通讯隔离)，简单的说VA内部就是一个“完全独立的空间”。
通过VA可将工作事务与个人事务安全的隔离，互不干扰。稍作定制即可实现应用行为审计、数据加密、数据采集、数据防泄漏、防攻击泄密等移动安全相关的需求。    
    **2.1 应用行为审计**  
通过VA提供的HOOK能力可以实现实时监测用户使用行为，将违规信息上传到服务器；并能轻易实现诸如时间围栏(在某个时间段内能否使用应用的某个功能)、地理围栏(在某个区域内能否使用应用的某个功能)、敏感关键字过滤拦截等功能需求。  
	**2.2 数据加密**  
通过VA提供的HOOK能力可以实现对应用的全部数据/文件加密，保证数据/文件落地安全。   
	**2.3 数据采集**  
通过VA提供的HOOK能力可以实现应用数据的实时无感上传需求，如聊天记录、转账记录等，防止事后删除无法追溯。  
	**2.4 数据防泄漏**  
通过VA提供的HOOK能力可以实现应用防复制/粘贴、防截屏/录屏、防分享/转发、水印溯源等需求。   
	**2.5 防攻击泄密**  
通过VA提供的应用管控能力可以将APP获取短信/通讯录/通话记录/后台录音/后台拍照/浏览历史/位置信息等隐私相关的行为完全控制在沙盒中，防止木马/恶意APP获取到用户真实的隐私数据，造成泄密等严重后果。  

3. 可以满足您的**免ROOT HOOK**需求  
VA提供了Java与Native的Hook能力，通过VA，您可以轻易实现诸如虚拟定位、改机、APP监控管理、移动安全等各种场景需要的功能。  

4. 可以满足您的**APP静默安装**需求  
VA提供了APP静默安装，静默升级，静默卸载的能力。如应用商店或游戏中心在集成VA后可以避免需要用户手动点击确认安装的操作，做到下载后立即安装到VA内，给用户带来“小程序”搬的体验，彻底避免了应用不易被用户安装上的问题。  

5. 可以满足您的**APP管控**需求  
通过VA提供的应用管控能力，您可以轻易控制VA中APP的运行界面或运行流程，实现如脚本自动化、特定界面插屏弹窗、修改APP界面内容，修改APP与服务器交互内容等需求。  

6. 可以满足您的**海外市场**需求  
VA实现了对Google服务的支持，以支持海外的App运行，比如Twitter、Messenger、WhatsApp、Instagram、FaceBook、Youtube等。  

7. 可以满足您**几乎一切能想到**的需求  
VA对于内部的App具有完全的监管和控制能力，几乎能满足您的一切需求！

8. 同时VA也是该技术领域__唯一一款__对外商业授权的产品    
截止目前已有**上百家**授权客户在付费使用VirtualApp商业版代码，集成VirtualApp代码的APP__日启动__次数__超过2亿次__，众多安卓工程师向我们提供不同场景下的用户反馈，通过我们技术团队不断优化迭代，不断提升产品性能与兼容性！

## VA如何使用？ ##
第1步：在您的Application中调用VA接口```VirtualCore.get().startup()```来启动VA引擎  
第2步:调用VA接口```VirtualCore.get().installPackageAsUser()```将目标APP安装到VA中  
第3步:调用VA接口```VirtualCore.get().installPackageAsUser()```启动您安装到VA中的APP    
**仅通过以上3个API就完成了基础使用，VA已屏蔽了复杂的技术细节，并提供了接口API，让您的开发变得很简单！**

## VA开发文档 ##
VA的详细开发文档请参考：[https://github.com/asLody/VirtualApp-Priv/wiki](https://github.com/asLody/VirtualApp-Priv/wiki)

## VA架构 ##

![](https://github.com/xxxyanchenxxx/temp/blob/master/va1.png)

![](https://github.com/xxxyanchenxxx/temp/blob/master/va2.png)


## VA与其他技术方案对比 ##
如果要实现对APP的管控，以下是所有可能的技术方案：  
<table >
        <tr>
            <th>技术方案</th>
            <th>原理简介</th>
            <th>风险点</th>
            <th>运行性能</th>
            <th>兼容稳定性</th>
            <th>项目维护成本</th>
        </tr>
        <tr  align="left">
            <th>二次打包</th>
            <th>通过反编译目标APP，加入自己的控制代码，重新打包</th>
            <th>1.现在的APP几乎都有加固或防篡改保护，重打包已是一件非常困难的事</br> 2.手机系统也会检测APP是否被重打包，如果重打包，会直接提示用户存在安全风险，甚至不让安装</br>3.针对每一个APP，甚至每一个版本都要深入去逆向分析，耗时耗力，难于维护</th>
            <th>优秀</th>
            <th>差</th>
            <th>非常大</th>
        </tr>
        <tr  align="left">
            <th>定制ROM</th>
            <th>通过定制系统源码，编译刷到指定手机</th>
            <th>只能针对指定的内部手机，无法扩展</br></th>
            <th>优秀</th>	
            <th>优秀</th>
            <th>大</th>
        </tr>
        <tr  align="left">
            <th>ROOT手机</th>
            <th>通过ROOT手机，刷入xposed等类似框架</th>
            <th>1.现在ROOT手机本身已是一件很难的事</br>2.现实中也很难让用户能去ROOT自己的手机</br></br></br></th>
            <th>优秀</th>
            <th>一般</th>
            <th>一般</th>
        </tr>
        <tr  align="left">
            <th>Android虚拟机</th>
            <th>重量级虚拟机，在Android系统上再跑一个定制的Android系统</th>
            <th>1.太过重量级，对手机性能要求很高<br> 2.因为要自己做硬件访问，所以对设备访问不可避免天然存在诸多兼容性问题，也很难解决<br>3.需要维护一套系统源码，并在虚拟机，设备硬件之间做适配</br></br></br></th>
            <th>差</th>
            <th>差</th>
            <th>大</th>
        </tr>
        <tr  align="left">
            <th>VA</th>
            <th>轻量级虚拟机，速度快，设备要求低</th>
            <th>无以上风险点，但是如果未被商业授权使用，将给公司带来法律风险。</br></br></br></th>
            <th>优秀，与原生应用几乎一样的速度</th>
            <th>优秀，有上百家企业在同时测试反馈</th>
            <th>低，VA提供了API并有专业的技术团队保障项目稳定运行</th>
        </tr>
    </table>


## VA的兼容稳定性怎么样？ ##
VA已被**上百家**企业进行了广泛测试，包含**数十家上市公司高标准**的测试及反馈，几乎涵盖了海内外的各种机型设备和场景！
为您的稳定运行提供了充分的保障！  

截止目前，支持的系统版本:

<table>
        <tr>
            <th>系统版本号</th>
            <th>是否支持</th>
        </tr>
        <tr>
            <th>4.1</th>
            <th>支持</th>
        </tr>
        <tr>
            <th>4.2</th>
            <th>支持</th>
        </tr>
        <tr>
            <th>4.3</th>
            <th>支持</th>
        </tr>
        <tr>
            <th>4.4</th>
            <th>支持</th>
        </tr>
        <tr>
            <th>5.0</th>
            <th>支持</th>
        </tr>
        <tr>
            <th>5.1</th>
            <th>支持</th>
        </tr>
        <tr>
            <th>6.0</th>
            <th>支持</th>
        </tr>
        <tr>
            <th>7.0</th>
            <th>支持</th>
        </tr>
        <tr>
            <th>8.0</th>
            <th>支持</th>
        </tr>
        <tr>
            <th>9.0</th>
            <th>支持</th>
        </tr>
        <tr>
            <th>10.0</th>
            <th>支持</th>
        </tr>
        <tr>
            <th>11.0</th>
            <th>支持</th>
        </tr>
        <tr>
            <th>12.0</th>
            <th>该系统还Google还未发布，已在支持准备中</th>
        </tr>
    </table>

支持的APP类型:
<table>
        <tr>
            <th>APP类型</th>
            <th>是否支持</th>
        </tr>
        <tr>
            <th>32位APP</th>
            <th>支持</th>
        </tr>
        <tr>
            <th>64位APP</th>
            <th>支持</th>
        </tr>
    </table>

支持的HOOK类型:
<table>
        <tr>
            <th>Hook类型</th>
            <th>是否支持</th>
        </tr>
        <tr>
            <th>Java Hook</th>
            <th>支持</th>
        </tr>
        <tr>
            <th>Native Hook</th>
            <th>支持</th>
        </tr>
    </table>

## 集成VA遇到问题如何反馈？ ##
购买授权后，会有专门的技术问题反馈群。我们有多名技术工程师随时在线接受问题反馈，会在第一时间处理！

