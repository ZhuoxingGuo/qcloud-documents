## 设置容器集群与IDC互通
目前容器集群与用户IDC互通主要通过两种方式：**专线**和**IPsec VPN**,

> 注意：  
> 1.前提：已经**创建集群**并已添加节点（点击了解[**创建集群**](https://cloud.tencent.com/document/product/457/11741)）  
> 2.请先确保成功容器服务所在的VPC和您IDC机房通过专线或VPN连接，（点击了解[**VPN打通**]()）子机间能互通，若通道未连接，可以参考[**详情**](https://cloud.tencent.com/document/product/215/17010)排查。
> 
> 
### 专线打通

1. [申请物理专线](https://cloud.tencent.com/document/product/216/19244)
2. [申请通道](https://cloud.tencent.com/document/product/216/19250)
3. [创建专线网关](https://cloud.tencent.com/document/product/216/19256)
4. 验证容器节点与IDC互通。（**请保证本步骤验证通过**）
6. 准备地域，appId，集群Id，vpcId，专线网关Id信息，[提交工单](https://console.qcloud.com/workorder/category?level1_id=6&level2_id=350&source=0&data_title=%E5%AE%B9%E5%99%A8%E6%9C%8D%E5%8A%A1TKE&step=1)打通容器网络。
7. 若IDC使用的是BGP协议，容器网段路由将自动同步。若是其他协议，需在IDC内配置访问容器网段下一跳路由到专线网关。
8. 验证容器与与IDC互通。

### VPN打通
#### 步骤1
1. 登录 [**腾讯云容器服务控制台**](https://console.cloud.tencent.com/ccs) 【云产品】找到【私有网络】单击左侧导航栏中的 【VPN连接】的 【VPN通道】
![](https://main.qcloudimg.com/raw/ffaf709b5d36e54cd416a03c25ea203e.png)
2. 点击【VPN通道ID】进入详情页，在【SPD策略】下方点击编辑 添加容器网段 
![腾讯云配置SPD策略](https://main.qcloudimg.com/raw/07d18b2dd62d06025c0818537dae0e1a.png) 

同理您对端VPN通道也需要SPD策略 添加腾讯云容器所在网段

#### 步骤2
单击左侧导航栏中【路由表】找到之前的vpn添加对端子机路由的那张路由表，追加容器网段， 并关联子机所在的子网。
![腾讯云](https://main.qcloudimg.com/raw/fe58e868249a7730c1aa9913f49ee55f.png)  
同理您对端的路由设备上，添加腾讯云容器所在网段

> 注意：一个子网只能绑定一个路由表，若关联多个路由表，将被替换成最后一个绑定的路由表


#### 步骤3 
测试腾讯云一个容器 和 对端子机是否互通
![](https://main.qcloudimg.com/raw/118676ef1a435f250ad1a92f11f4cf96.png)
可以看到容器间与vpn对端子机已经实现互通。  
总结：云上容器与IDC机房通过ipsec vpn 互通，设置主要就是**SPD策略**和**路由表**两部分配置。