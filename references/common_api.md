AutoDL帮助文档






[跳转至](#api)

[xml version="1.0" encoding="UTF-8"?


形状结合
Created with Sketch.](https://www.autodl.com "AutoDL帮助文档")






AutoDL帮助文档

API文档








正在初始化搜索引擎

[xml version="1.0" encoding="UTF-8"?


形状结合
Created with Sketch.](.. "AutoDL帮助文档")
AutoDL帮助文档

* [简介](..)
* [快速开始](../quick_start/)
* [视频教程](../video/)
* [学术资源加速](../network_turbo/)
* 如何选择GPU



  如何选择GPU
  + [GPU选型](../gpu/)
  + [性能实测](../gpu_perf/)
* 容器实例



  容器实例
  + [概要](../env/)
  + [JupyterLab](../jupyterlab/)
  + [SSH](../ssh/)
  + [升降配置](../update_config/)
  + [转换计费方式](../change_billing_method/)
  + [保存镜像](../save_image/)
  + [重置系统](../reset_instance/)
  + [迁移实例](../migrate_instance/)
  + [迁移实例(同地区)](../migrate_instance_2/)
  + [守护进程(开后台)](../daemon/)
  + [多机多卡并行](../distributed_training/)
  + [远程桌面](../gui/)
* 数据



  数据
  + [概要](../instance_data/)
  + [公网网盘(强推)](../netdisk/)
  + [上传数据](../scp/)
  + [下载数据](../down/)
  + [本地数据盘](../local_disk/)
  + [公开数据](../public_data/)
  + [文件存储](../fs/)
  + [压缩/解压](../arc/)
* 配置环境



  配置环境
  + [概要](../base_config/)
  + [依赖安装](../deps/)
  + [镜像](../image/)
  + [Python3.X](../python/)
  + [CUDA/cuDNN](../cuda/)
  + [Miniconda](../miniconda/)
* 国产芯片



  国产芯片
  + [华为昇腾NPU](../huawei_ascend/)
  + [华为MindIE](../huawei_mindie/)
  + [摩尔线程GPU](../mt_gpu/)
* 最佳实践



  最佳实践
  + [Linux基础](../linux/)
  + [软件源](../source/)
  + [Github](../git/)
  + [Filezilla](../filezilla/)
  + [XShell](../xshell/)
  + [TensorBoard](../tensorboard/)
  + [VSCode](../vscode/)
  + [PyCharm](../pycharm/)
  + [Gromacs](../gromacs/)
  + [Visdom](../visdom/)
  + [KataGo](../katago/)
  + [RStudio](../rstudio/)
  + [OpenCL](../opencl/)
  + [Vulkan](../vulkan/)
  + [HuggingFace](../huggingface/)
  + [MPI](../mpi/)
  + [SSH隧道](../ssh_proxy/)
  + [计算精度](../precision/)
  + [开放端口](../port/)
  + [微信消息](../msg/)
  + [性能篇](../perf/)
  + [省钱绝招](../save_money/)
  + [暴露多个服务](../proxy_in_instance/)
* 企业高级功能



  企业高级功能
  + [弹性部署](../elastic_deploy/)
  + [弹性部署最佳实践](../elastic_deploy_practice/)
  + [弹性部署更新日志](../elastic_deploy_update_log/)
  + [性能指标监控](../metric_monitor/)
  + [子账号](../c_user/)
* [网络](../network/)
* AI服务器



  AI服务器
  + [AI服务器](../ai_server/)
* 常见问题



  常见问题
  + [系统盘空间不足](../qa1/)
  + [JupyterLab打不开](../qa2/)
  + [不能调用GPU](../qa3/)
  + [显存没有释放](../qa4/)
  + [VSCode远程连接失败](../qa5/)
  + [基于SSH的连接异常](../qa6/)
  + [SD作图内存泄露](../qa7/)
  + [其他](../qa/)
* 活动



  活动
  + [代金券](../coupon/)
  + [优惠券](../cp/)
  + [炼丹会员](../member/)
  + [学生认证](../student/)
* [充值与计费](../price/)
* [发票](../invoice/)
* API文档



  API文档
  + API文档
    [API文档](./)



    目录
    - [鉴权](#_1)
    - [获取账户余额](#_2)

      * [请求](#_3)
      * [响应](#_4)
    - [切换专用NFS/文件存储](#nfs)

      * [请求](#_6)
      * [响应](#_7)
  + [容器实例Pro API](../instance_pro_api/)
  + [弹性部署API](../esd_api_doc/)
* [维护与故障](../maintenance/)
* 服务协议



  服务协议
  + [AutoDL服务协议](../agreements/)
  + [网盘服务协议](../nas_agreements/)
  + [实例自定义服务补充协议](../service_agreement/)
  + [实名认证服务协议](../real_name_cert/)
  + [隐私政策](../privacy_policy/)
  + [反挖矿协议](../anti_mining/)
  + [高校先用后付使用须知](../pay_later_agreements/)

目录

* [鉴权](#_1)
* [获取账户余额](#_2)

  + [请求](#_3)
  + [响应](#_4)
* [切换专用NFS/文件存储](#nfs)

  + [请求](#_6)
  + [响应](#_7)

API文档[¶](#api "Permanent link")
===============================

API服务端HOST地址为：`https://api.autodl.com`

鉴权[¶](#_1 "Permanent link")
---------------------------

token获取位置： 控制台 -> 设置 -> 开发者Token

```
headers = {"Authorization": "token"}
```

获取账户余额[¶](#_2 "Permanent link")
-------------------------------

### 请求[¶](#_3 "Permanent link")

POST `/api/v1/dev/wallet/balance`

请求参数：无

### 响应[¶](#_4 "Permanent link")

响应参数：

| 参数 | 数据类型 | 备注 |
| --- | --- | --- |
| code | String | 响应代码，成功时为Success |
| msg | String | 错误信息，成功时为空 |
| data | Response对象 |  |

Response对象参数：

| 参数 | 数据类型 | 备注 |
| --- | --- | --- |
| assets | Int | 当前余额。除以1000等于元 |
| accumulate | Int | 累计消费金额。除以1000等于元 |
| voucher\_balance | Int | 当前代金券可用余额。除以1000等于元 |

样例：

```
{
    "code": "Success",
    "data": {
        "assets": 1000,
        "accumulate": 1000,
        "voucher_balance": 1000,
    },
    "msg": ""
}
```

Python代码

```
import requests
headers = {
    "Authorization": "您的token"
}
url = "https://api.autodl.com/api/v1/dev/wallet/balance"
response = requests.post(url, headers=headers)
print(response.content.decode())
```

[¶](#_5 "Permanent link")
-------------------------

切换专用NFS/文件存储[¶](#nfs "Permanent link")
--------------------------------------

### 请求[¶](#_6 "Permanent link")

POST `/api/v1/dev/exclusive_nfs/mount`

请求参数：

| 参数 | 数据类型 | 备注 |
| --- | --- | --- |
| data\_center | String | 指定地区代码，可查询弹性部署API文档附录 |
| mountable | Int | 设置为1表示挂载专用NFS，即关闭挂载普通文件存储；设置为-1即关闭专用NFS，即切换普通文件存储 |

### 响应[¶](#_7 "Permanent link")

响应参数：

| 参数 | 数据类型 | 备注 |
| --- | --- | --- |
| code | String | 响应代码，成功时为Success |
| msg | String | 错误信息，成功时为空 |

样例：

```
{
    "code": "Success",
    "msg": ""
}
```

Python代码

```
import requests
headers = {
    "Authorization": "您的token"
}
body = {
    "data_center": "westDC2",
    "mountable": 1,
}
url = "https://api.autodl.com/api/v1/dev/exclusive_nfs/mount"
response = requests.post(url, json=body, headers=headers)
print(response.content.decode())
```
