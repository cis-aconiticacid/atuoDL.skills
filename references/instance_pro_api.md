AutoDL帮助文档






[跳转至](#pro-api)

[xml version="1.0" encoding="UTF-8"?


形状结合
Created with Sketch.](https://www.autodl.com "AutoDL帮助文档")






AutoDL帮助文档

容器实例Pro API








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
  + [API文档](../common_api/)
  + 容器实例Pro API
    [容器实例Pro API](./)



    目录
    - [鉴权](#_1)
    - [创建实例](#_2)
    - [获取实例详情](#_3)
    - [获取实例状态](#_4)
    - [获取实例列表](#_5)
    - [开机实例](#_6)
    - [关机实例](#_7)
    - [释放实例](#_8)
    - [附录](#_9)
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
* [创建实例](#_2)
* [获取实例详情](#_3)
* [获取实例状态](#_4)
* [获取实例列表](#_5)
* [开机实例](#_6)
* [关机实例](#_7)
* [释放实例](#_8)
* [附录](#_9)

容器实例Pro API[¶](#pro-api "Permanent link")
=========================================

API服务端HOST地址为：`https://api.autodl.com`

鉴权[¶](#_1 "Permanent link")
---------------------------

Token获取位置：请登录 [www.AutoDL.com](www.autodl.com) 访问控制台 → 账号 → 设置 → [开发者Token](https://www.autodl.com/console/center/settings/token)

使用Token方式：

```
headers = {"Authorization": "填写您的token"}
```

创建实例[¶](#_2 "Permanent link")
-----------------------------

POST `/api/v1/dev/instance/pro/create`

请求Body示例：

```
// 默认以按量计费方式创建实例，暂不支持选择其他计费方式创建实例
{
    "data_center_list": ["westDC3", "beijingDC2"],  // [选填] 默认系统自动选择地区，westDC3：西北区，beijingDC2：北京区
    "req_gpu_amount":1,  // [必填] GPU数量, 最小值=1，最大值4
    "expand_system_disk_by_gb":0, // [必填] 系统盘扩容大小 单位:GB, 取值范围: 0-500
    "gpu_spec_uuid":"pro6000-p",  // [必填] 算力规格ID，请参考文末附录中不同GPU型号的规格ID
    "image_uuid":"image-xxxxxxxxx", // [必填] 镜像的UUID，可打开私有镜像列表查看
    "cuda_v_from": 113,  // [必填] 调度时主机驱动支持的cuda版本需要满足您设置的cuda版本下限，113代表cuda>=11.3
    "instance_name":"API创建的实例", // [选填] 实例备注名
    "start_command":"sleep 1" // [选填] 实例开机后执行此命令，该命令执行成功与否不影响实例开机运行，不会因命令执行失败而关机
}
```

返回Body示例：

```
{
    "code": "Success",
    "data": "pro-76419909953e",  // 创建出的实例ID
    "msg": "",
    "request_id": "983edb8c8c8553db1115d51fb2758ae8"
}
```

获取实例详情[¶](#_3 "Permanent link")
-------------------------------

GET `/api/v1/dev/instance/pro/snapshot`

请求Body示例：

```
{
    "instance_uuid":"pro-76576c61fdf1"  // [必填] 实例ID
}
```

返回Body示例：

```
{
    "code": "Success",
    "data": {
        "region_sign": "bj-B1",
        "payg_price": 1970,  // 折扣后的按量计费价格
        "origin_pay_price": 3030,  // 折扣前的按量计费价格
        "snapshot_gpu_alias_name": "NVIDIA RTX PRO 6000",
        "chip_corp": "nvidia",
        "cpu_arch": "x86",
        "usage_info": {
            "container_id": "autodl-pro-76576c61fdf1",
            "valid_at": "2025-12-15T18:35:52.137127391+08:00",
            "cpu_usage_percent": 3.34,
            "mem_usage_percent": 1.26,
            "mem_usage": 270528512,
            "mem_limit": 21474836480,
            "root_fs_used_size": 54435840,
            "root_fs_total_size": 31526391808,
            "data_disk_total_size": 0,
            "data_disk_used_size": 0,
            "storage_fs_usage": "",
            "pull_image_progress": 1,
            "download_image_progress": 1,
            "download_oss_file_progress": 0,
            "sys_fs_last_block_size": 0,
            "is_new": false,
            "valid": false
        },
        "expand_system_disk_size": 32212254720,
        "system_init_disk_size": 32212254720,
        "ssh_command": "ssh -p 34222 root@connect.xxx.autodl.com",
        "proxy_host": "connect.xxx.autodl.com",  // ssh地址
        "root_password": "jbeOXgTWUxq+",  // ssh密码
        "ssh_port": 34222,  // ssh 端口
        "jupyter_token": "xxx",  // jupyterlab token
        "jupyter_domain": "a1-765793a1f226.xxx.autodl.com:8443", // jupyterlab的访问地址
        "service_6006_domain": "u1-h1tr7dnhvxyvm4uacvq9.xxx.autodl.com:8443", // 6006端口服务对应的访问地址
        "service_6006_port_protocol": "http",
        "service_6008_domain": "uu1-yufv2v0fcxtvr5lv4j80.xxx.autodl.com:8443",  // 6008端口服务对应的访问地址
        "service_6008_port_protocol": "http"
    },
    "msg": "",
    "request_id": "b717410bb575336654fcc2ad79c72675"
}
```

获取实例状态[¶](#_4 "Permanent link")
-------------------------------

GET `/api/v1/dev/instance/pro/status`

请求Body示例：

```
{
    "instance_uuid":"pro-76576c61fdf1"  // [必填] 实例ID
}
```

返回Body示例：

```
{
    "code": "Success",
    "data": "running",  // 实例状态
    "msg": "",
    "request_id": "2159c05b9b675c731c2334b88d6be8aa"
}
```

获取实例列表[¶](#_5 "Permanent link")
-------------------------------

POST `/api/v1/dev/instance/pro/list`

请求Body示例：

```
{
    "page_index":1,
    "page_size":1
}
```

返回Body示例：

```
{
    "code": "Success",
    "data": {
        "list": [
            {
                "created_at": "2025-12-15T17:30:54+08:00",
                "uuid": "pro-76576c61fdf1",
                "machine_id": "4d67438b4f",
                "machine_alias": "",
                "region_sign": "neimeng-C",
                "region_name": "内蒙C区",
                "status": "running",
                "sub_status": "",
                "status_at": "2025-12-15T17:31:05+08:00",
                "start_mode": "gpu",    // 有卡模式：gpu
                "charge_type": "payg",  // 计费方式
                "req_gpu_amount": 1,  // GPU数量
                "expired_at": {
                    "Time": "0001-01-01T00:00:00Z",
                    "Valid": false
                },
                "started_at": {
                    "Time": "2025-12-15T17:31:05+08:00",
                    "Valid": true
                },
                "stopped_at": {
                    "Time": "0001-01-01T00:00:00Z",
                    "Valid": false
                },
                "name": "zqAPI创建",
                "timed_shutdown_at": {
                    "Time": "0001-01-01T00:00:00Z",
                    "Valid": false
                },
                "gpu_spec_uuid": "pro6000-p"  // 算力规格ID
            }
        ],
        "page_index": 1, // 第几页
        "page_size": 1,  // 每页记录数量
        "offset": 0,
        "max_page": 22,  // 总页数
        "result_total": 22,  // 总记录数
        "page": 1
    },
    "msg": "",
    "request_id": "c53a6dc29de7c65ff2798dac12d8fe78"
}
```

开机实例[¶](#_6 "Permanent link")
-----------------------------

POST `/api/v1/dev/instance/pro/power_on`

请求Body示例：

```
{
    "instance_uuid": "pro-759127a8714f", // [必填] 实例ID
    "payload":"gpu", // [必填] gpu：有卡开机, 暂不支持API以无卡模式开机
    "start_command":"sleep 1" // [选填] 实例开机后执行此命令，该命令执行成功与否不影响实例开机运行，不会因命令执行失败而关机。会覆盖创建时设置的命令
}
```

返回Body示例：

```
{
    "code": "Success",
    "data": null,
    "msg": "",
    "request_id": "2a8504ac55fece996ace6deeb98e7fe5"
}
```

关机实例[¶](#_7 "Permanent link")
-----------------------------

POST `/api/v1/dev/instance/pro/power_off`

请求Body示例：

```
{
    "instance_uuid": "pro-759127a8714f" // [必填] 实例ID
}
```

返回Body示例：

```
{
    "code": "Success",
    "data": null,
    "msg": "",
    "request_id": "20114f6ef29ab403cc421489bb6e5539"
}
```

释放实例[¶](#_8 "Permanent link")
-----------------------------

在释放实例前请先关机实例，否则可能无法释放

POST `/api/v1/dev/instance/pro/release`

请求Body示例：

```
{
    "instance_uuid": "pro-759127a8714f" // [必填] 实例ID
}
```

返回Body示例：

```
{
    "code": "Success",
    "data": null,
    "msg": "",
    "request_id": "20114f6ef29ab403cc421489bb6e5539"
}
```

附录[¶](#_9 "Permanent link")
---------------------------

GPU型号和算力规格ID对应表

| 前台网页显示GPU型号 | 前台网页显示的规格名称 | API中使用的算力规格ID |
| --- | --- | --- |
| H800-80G | 通用型 | h800 |
| 4090-48G | 通用型 | v-48g |
| PRO6000-96G | 性能型 | pro6000-p |
| 4080(S)-32G | 性能型 | v-32g-p |
| 3090-48G | 通用型 | v-48g-350w |
| 5090-32G | 性能型 | 5090-p |
