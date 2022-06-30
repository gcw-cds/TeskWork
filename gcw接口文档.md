# 桌面相关
---

# 1. QueryTask

Action: QueryTask
描述: 获取任务信息
请求地址: [cdsapi.capitalonline.net/gcw](http://cdsapi.capitalonline.net/gcw)
请求方法: GET

请求参数：

| 名称      | 类型   | 是否必须 | 示例                                 | 描述         |
| --------- | ------ | -------- | ------------------------------------ | ------------ |
| taskId    | string | 是       | 6bca6bbd-58f2-427e-acdc-2eeb4c7328c7 | 任务id       |
| requestId | string | 是       | 6ca9ed98-27c8-4431-995f-59cc6d743dab | 请求标识uuid |

返回数据：

| 名称       | 类型   | 示例                                   | 描述                              |
| ---------- | ------ | -------------------------------------- | --------------------------------- |
| Code       | string | Success                                | 返回状态码: Success: 成功         |
| Message    | string | null                                   | 返回信息                          |
| Data       | object | {}                                     | 返回数据                          |
| taskId     | string | “35304122-8504-400c-a61c-56ba244c5dda” | 任务id                            |
| status     | string | “Completed”                            | 任务状态 Running Failed Completed |
| failReason | string | “”                                     | 失败原因                          |
| requestId  | string | “6ca9ed98-27c8-4431-995f-59cc6d743dab” | 请求uuid                          |

错误码：

| 错误码 | 错误信息           | 描述                 |
| ------ | ------------------ | -------------------- |
| 10003  | 传入参数不符合要求 | 传入参数不符合要求   |
| 10006  | 参数错误           | 参数错误，任务不存在 |

返回示例

```json
{
    "Code": "Success",
    "Data": {
        "failReason": "失败子任务名称：关闭云桌面,失败子任务id:194c8fd2-d03e-41ce-a10d-53ef714fc0cd,失败流程名称:关闭云桌面,失败流程id：14695198-f1bc-454a-b464-b4b55eb9f7d7,失败原因:平台关机的云桌面不存在",
        "requestId": "6ca9ed98-27c8-4431-995f-59cc6d743dab",
        "status": "Failed",
        "taskId": "6bca6bbd-58f2-427e-acdc-2eeb4c7328c7"
    },
    "Message": ""
}

```

代码调用示例

```python

def queryTask():
    '''
    获取任务信息
    :return:
    '''
    action = "QueryTask"
    method = "GET"
    param = {"taskId": "a78a642b-7ee0-4c7e-9d45-62cd040cb910", "requestId": "6ca9ed98-27c8-4431-995f-59cc6d743dab"}
    url = getUrl(action, AK, AccessKeySecret, method, CCS_URL, param=param)
    res = requests.get(url)
    result = json.loads(res.content)
    print(result)
    if result.get("Code") != "Success":
        print ("request error: %s" % result.get("Message"))
    return result

```



# 2. QuerySites

Action: QuerySites
描述: 查询可用区域信息
请求地址: [cdsapi.capitalonline.net/gcw](http://cdsapi.capitalonline.net/gcw)
请求方法: Get

请求参数：

| 名称   | 类型   | 是否必须 | 示例                                 | 描述   |
| ------ | ------ | -------- | ------------------------------------ | ------ |
| siteId | string | 否       | 09a38804-c1ee-11ec-bd22-4641dfd57315 | 站点id |

返回数据：

| 名称       | 类型   | 示例                                   | 描述                      |
| ---------- | ------ | -------------------------------------- | ------------------------- |
| Code       | string | Success                                | 返回状态码: Success: 成功 |
| Message    | string | null                                   | 返回信息                  |
| Data       | list   | []                                     | 返回数据                  |
| siteId     | string | “d318e1a2-9bab-11ec-875a-2a8d1f4e167e” | 站点ID’                   |
| podName    | string | “POD210”                               | ‘站点名称’                |
| siteName   | string | “襄阳A”                                | ‘站点name’                |
| regionName | string | “中国大陆”                             | ‘区域name’                |
| regionId   | string | “408fd19e-fa78-11e6-bd9a-30b49e091019” | ‘区域id’                  |
| cityName   | string | “襄阳”                                 | ‘城市name’                |
| cityId     | string | “32e6fd62-9bac-11ec-875a-2a8d1f4e167e” | ‘城市id’                  |

错误码：

| 错误码 | 错误信息 | 描述 |
| ------ | -------- | ---- |
|        |          |      |

返回示例

```json

{
    "Code": "Success",
    "Data": [
        {
            "cityId": "d318e1a2-9bab-11ec-875a-2a8d1f4e167e",
            "cityName": "襄阳",
            "podName": "POD210",
            "regionId": "408fd19e-fa78-11e6-bd9a-30b49e091019",
            "regionName": "中国大陆",
            "siteId": "32e6fd62-9bac-11ec-875a-2a8d1f4e167e",
            "siteName": "襄阳A"
        },
        {
            "cityId": "39c6ed64-8d5f-11ec-9247-5293695d0ddd",
            "cityName": "宿迁",
            "podName": "POD203",
            "regionId": "408fd19e-fa78-11e6-bd9a-30b49e091019",
            "regionName": "中国大陆",
            "siteId": "f7c3c7a6-8d5f-11ec-9311-5293695d0ddd",
            "siteName": "宿迁A"
        }
    ],
    "Message": ""
}

```

代码调用示例

```python
def querySites():
    '''
    查询可用区域信息
    :return:
    '''
    action = "QuerySites"
    method = "GET"
    param = {}
    url = getUrl(action, AK, AccessKeySecret, method, CCS_URL, param=param)
    res = requests.get(url)
    result = json.loads(res.content)
    print(result)
    if result.get("Code") != "Success":
        print ("request error: %s" % result.get("Message"))
    return result

```



# 3. QueryProducts

Action: QueryProducts
描述: 查询商品信息
请求地址: [cdsapi.capitalonline.net/gcw](http://cdsapi.capitalonline.net/gcw)
请求方法: Get

请求参数：

| 名称   | 类型   | 是否必须 | 示例                                 | 描述   |
| ------ | ------ | -------- | ------------------------------------ | ------ |
| siteId | string | 否       | 09a38804-c1ee-11ec-bd22-4641dfd57315 | 站点id |

返回数据：

| 名称           | 类型   | 示例                                   | 描述                             |
| -------------- | ------ | -------------------------------------- | -------------------------------- |
| Code           | string | Success                                | 返回状态码: Success: 成功        |
| Message        | string | null                                   | 返回信息                         |
| Data           | list   | []                                     | 返回数据                         |
| siteId         | string | “ebbfcb70-a98f-11ec-926b-8aaa763f849e” | 站点ID’                          |
| productId      | string | “e0997510-1b69-4de8-85a8-cc44b2dd28f8” | 商品规格id                       |
| cpuCores       | int    | 14                                     | cpu 核数                         |
| memorySize     | int    | 25                                     | 内存                             |
| gpuModel       | string | “NVIDIA A5000”                         | gpu型号                          |
| gpuRam         | int    | 24                                     | gpu显存                          |
| systemDiskSize | int    | 150                                    | 系统盘大小                       |
| os             | string | “windows”                              | 操作系统                         |
| goodsId        | int    | 15264                                  | 商品id                           |
| requirePrice   | double | 0.1868333333                           | 按需价格，每分钟所需的人民币数值 |
| monthPrice     | double | 3364                                   | 包月价格，每月所需的人民币数值   |

错误码：

| 错误码 | 错误信息             | 描述                 |
| ------ | -------------------- | -------------------- |
| 12000  | 查询商品规格信息失败 | 查询商品规格信息失败 |

返回示例

```json
{
    "Code": "Success",
    "Data": [
        {
            "cpuCores": 14,
            "goodsId": 15264,
            "gpuModel": "NVIDIA A5000",
            "gpuRam": 24,
            "memorySize": 25,
            "monthPrice": 3364,
            "os": "windows",
            "productId": "e0997510-1b69-4de8-85a8-cc44b2dd28f8",
            "requirePrice": 0.1868333333,
            "siteId": "ebbfcb70-a98f-11ec-926b-8aaa763f849e",
            "systemDiskSize": 150
        },
        {
            "cpuCores": 14,
            "goodsId": 15264,
            "gpuModel": "NVIDIA A5000",
            "gpuRam": 24,
            "memorySize": 25,
            "monthPrice": 3364,
            "os": "windows",
            "productId": "e0997510-1b69-4de8-85a8-cc44b2dd28f8",
            "requirePrice": 0.1868333333,
            "siteId": "9efa59c0-a0db-11ec-aefa-1efd5a8f8465",
            "systemDiskSize": 150
        }
    ],
    "Message": ""
}

```

代码调用示例

```python
def queryProducts():
    '''
    查询商品信息
    :return:
    '''
    action = "QueryProducts"
    method = "GET"
    param = {}
    url = getUrl(action, AK, AccessKeySecret, method, CCS_URL, param=param)
    res = requests.get(url)
    result = json.loads(res.content)
    print(result)
    if result.get("Code") != "Success":
        print ("request error: %s" % result.get("Message"))
    return result

```



# 4. QueryImages

Action: QueryImages
描述: 查询可用镜像信息
请求地址: [cdsapi.capitalonline.net/gcw](http://cdsapi.capitalonline.net/gcw)
请求方法: Get

请求参数：

| 名称      | 类型   | 是否必须 | 示例                                 | 描述       |
| :-------- | :----- | :------- | :----------------------------------- | :--------- |
| siteId    | string | 否       | 09a38804-c1ee-11ec-bd22-4641dfd57315 | 站点id     |
| productId | string | 否       | 56a38804-cdee-1aec-bd22-3141dfd57235 | 商品规格id |

返回数据：

| 名称          | 类型   | 示例                                   | 描述                                                         |
| :------------ | :----- | :------------------------------------- | :----------------------------------------------------------- |
| Code          | string | Success                                | 返回状态码: Success: 成功                                    |
| Message       | string | null                                   | 返回信息                                                     |
| Data          | list   | []                                     | 返回数据                                                     |
| productId     | string | "745f6546-dc5f-492f-82d1-9eb47cd9fa2d" | 商品规格id                                                   |
| productName   | string | "图形处理型"                           | 商品规格名称                                                 |
| publicImages  | list   | []                                     | 共有镜像                                                     |
| privateImages | list   | []                                     | 私有镜像                                                     |
| imageId       | string | "0e0f9143-35c5-4368-8c62-4bab440a9b9d" | 镜像Id                                                       |
| imageName     | string | "Windows10-公共镜像-图像处理型"        | 镜像名称                                                     |
| detailName    | string | ""                                     | 镜像详细名称                                                 |
| imageType     | string | "Public"                               | 镜像类型 public(公有) private（私有）                        |
| osType        | string | "windows"                              | 操作系统类型                                                 |
| imageSize     | Double | 72                                     | 镜像大小（G）                                                |
| message       | string | ""                                     | 描述信息                                                     |
| imageSites    | list   | []                                     | 镜像所在站点信息                                             |
| imageSiteId   | string | "nd206602-7f44-1343-a36f-32tyf61c1"    | 镜像站点ID                                                   |
| siteId        | string | "9efa59c0-a0db-11ec-aefa-1efd5a8f8     | 站点ID                                                       |
| siteName      | string | "保定A"                                | 站点名称                                                     |
| status        | string | "Available"                            | 状态 Creating(创建中)，Available(可用),Synchronizing(同步中), Error(错误), Deleting(删除中), Using(使用中) ，Deleted(已删除) ， 只有Available(可用)与Using(使用中)的镜像可用来创建与重装云桌面 |

错误码：

| 错误码 | 错误信息 | 描述                                   |
| :----- | :------- | :------------------------------------- |
| 10006  | 参数错误 | 1、无对应商品规格信息2、无对应站点信息 |

返回示例

```json
{
    "code": "Success",
    "msg": null,
    "data": [
        {
            "productId": "745f6546-dc5f-492f-82d1-9eb47cd9fa2d",
            "productName": "图形处理型",
            "publicImages": [
                {
                    "imageId": "0e0f9143-35c5-4368-8c62-4bab440a9b9d",
                    "imageName": "Windows10-公共镜像-图像处理型",
                    "detailName": "",
                    "imageType": "Public",
                    "osType": "windows",
                    "imageSize": 0.0,
                    "message": "",
                    "imageSites": [
                        {
                            "imageSiteId": "nd206602-7f44-1343-a36f-32tyf61c1",
                            "siteId": "9efa59c0-a0db-11ec-aefa-1efd5a8f8465",
                            "siteName": "保定A",
                            "status": "Available"
                        },
                        {
                            "imageSiteId": "bc205502-7y54-1893-a36f-325af61c1",
                            "siteId": "ebbfcb70-a98f-11ec-926b-8aaa763f849e",
                            "siteName": "娄底A",
                            "status": "Available"
                        },
                        {
                            "imageSiteId": "c37f559f-f1c0-47f4-9c5a-0df4af0b0e1b",
                            "siteId": "f7c3c7a6-8d5f-11ec-9311-5293695d0ddd",
                            "siteName": "宿迁A",
                            "status": "Available"
                        },
                        {
                            "imageSiteId": "0c380796-ecd5-4e16-b829-328710f68ddb",
                            "siteId": "09a38804-c1ee-11ec-bd22-4641dfd57315",
                            "siteName": "宿迁B",
                            "status": "Available"
                        }
                    ]
                }
            ],
            "privateImages": [
                {
                    "imageId": "e363df6f-2916-4efd-a243-50de5fb8928d",
                    "imageName": "定制模板",
                    "detailName": "dass-E2129298-windows10-Geforce-1655190089526",
                    "imageType": "Private",
                    "osType": "windows",
                    "imageSize": 32.0,
                    "message": "",
                    "imageSites": [
                        {
                            "imageSiteId": "3797fe64-4a5f-4791-8a10-65838134c898",
                            "siteId": "9efa59c0-a0db-11ec-aefa-1efd5a8f8465",
                            "siteName": "保定A",
                            "status": "Available"
                        },
                        {
                            "imageSiteId": "a2714dec-471e-426c-82e7-4f63f976ec2d",
                            "siteId": "ebbfcb70-a98f-11ec-926b-8aaa763f849e",
                            "siteName": "娄底A",
                            "status": "Available"
                        },
                        {
                            "imageSiteId": "4f2e0e22-9d8d-4aa7-9226-b5961ea5aa2d",
                            "siteId": "f7c3c7a6-8d5f-11ec-9311-5293695d0ddd",
                            "siteName": "宿迁A",
                            "status": "Available"
                        }
                    ]
                }
            ]
        }
    ],
    "requestId": null,
    "status": 0
}

```

代码调用示例

```python
def queryImages():
    '''
    查询可用镜像信息
   :return:
    '''
    action = "QueryImages"
    method = "GET"
    param = {
       ## "productId":"745f6546-dc5f-492f-82d1-9eb47cd9fa2d"
    }
    url = getUrl(action, AK, AccessKeySecret, method, CCS_URL, param=param)
    res = requests.get(url)
    result = json.loads(res.content)
    print(result)
    if result.get("Code") != "Success":
        print ("request error: %s" % result.get("Message"))
    return result
```



# 5. QueryVmPrice

Action: QueryVmPrice
描述: 查询云桌面价格信息
请求地址: [cdsapi.capitalonline.net/gcw](http://cdsapi.capitalonline.net/gcw)
请求方法: Post

请求参数：

| 名称      | 类型   | 是否必须 | 示例                                   | 描述                                                         |
| --------- | ------ | -------- | -------------------------------------- | ------------------------------------------------------------ |
| requestId | string | 是       | “e0997510-1b69-4de8-85a8-cc44b2dd28f8” | 请求uuid                                                     |
| siteId    | string | 是       | “ebbfcb70-a98f-11ec-926b-8aaa763f849e” | 节点id                                                       |
| duration  | string | 否       | ”1“                                    | 包月周期数，billCtcle的值是mounth时为包月，3个月传3,5个月传5；按需无需传，默认为1 |
| isToMonth | string | 否       | ”1“                                    | 费用是否为计算到月底(1:是,0:否) ,如:7月20号购买到月底7-31号,则is_to_month=1,duration=1 ， 默认为0（包月使用） 如：包月开始时间为 2022.6.22 12:19:08isToMonth为1，duration为1，则包月到2022.7.1 00:00:00isToMonth为0，duration为1，则包整月到2022.7.22 12:19:08isToMonth为1，duration为6，则包整月到2022.12.1 12:19:08 isToMonth为0，duration为6，则包整月到2022.12.22 12:19:08 |
| billCycle | string | 否       | “minute”                               | 计费周期 month是按月，minute是按需计费， 默认为minute        |
| num       | string | 否       | “1”                                    | 购买数量 ， 默认为1                                          |
| goodsId   | string | 是       | “15273”                                | 商品id                                                       |

返回数据：

| 名称           | 类型   | 示例                                 | 描述                                                         |
| -------------- | ------ | ------------------------------------ | ------------------------------------------------------------ |
| code           | string | Success                              | 返回状态码: Success: 成功                                    |
| msg            | string | null                                 | 返回信息                                                     |
| data           | object | {}                                   | 返回数据                                                     |
| tradeAmount    | double | 0.11                                 | 最终总价格（元） 1、按需：返回结果为每小时的价格2、包月：返回的结果为所要计算的总价格 |
| areaId         | string | CN                                   | 币种                                                         |
| requestId      | string | e0997510-1b69-4de8-85a8-cc44b2dd28f8 | 请求uuid                                                     |
| requestContent | string | {}                                   | 请求参数                                                     |

错误码：

| 错误码 | 错误信息           | 描述                                                    |
| ------ | ------------------ | ------------------------------------------------------- |
| 12505  | 查询云桌面价格失败 | 查询云桌面价格失败                                      |
| 10003  | 传入参数不符合要求 | 传入参数不符合要求，计费周期可选值为minute、month或year |
| 10006  | 参数错误           | 参数错误，无对应站点信息                                |

返回示例

```json

{
    "Code": "Success",
    "Data": {
        "areaId": "CN",
        "requestContent": "{\"billCycle\":\"minute\",\"billMethod\":0,\"customerId\":\"E2129298\",\"duration\":1,\"funParam\":{\"billCycle\":\"minute\",\"billMethod\":0,\"customer_id\":\"E2129298\",\"duration\":1,\"goodsId\":15273,\"isToMonth\":0,\"num\":1,\"siteId\":\"ebbfcb70-a98f-11ec-926b-8aaa763f849e\",\"user_id\":\"713367\"},\"goodsId\":15273,\"isToMonth\":0,\"num\":1,\"requestId\":\"e0997510-1b69-4de8-85a8-cc44b2dd28f8\",\"siteId\":\"ebbfcb70-a98f-11ec-926b-8aaa763f849e\",\"userFrom\":\"cdsapi\",\"userId\":\"713367\"}",
        "requestId": "e0997510-1b69-4de8-85a8-cc44b2dd28f8",
        "tradeAmount": 0.11
    },
    "Message": ""
}

```

代码调用示例

```python
def queryVmPrice():
    '''
    获取vm价格
    :return:
    '''
    action = "QueryVmPrice"
    method = "POST"
    body = {
        "requestId": "e0997510-1b69-4de8-85a8-cc44b2dd28f8",
        "siteId": "ebbfcb70-a98f-11ec-926b-8aaa763f849e",
        "duration": "1",
        "isToMonth": "1",
        "billCycle": "minute",
        "num": "1",
        "goodsId": "15273"
    }
    url = getUrl(action, AK, AccessKeySecret, method, CCS_URL, param={})
    res = requests.post(url,json=body)
    result = json.loads(res.content)
    print(result)
    if result.get("Code") != "Success":
        print ("request error: %s" % result.get("Message"))
    return result

```

# 6. UpdateOrder

Action: UpdateOrder
描述: 按需转包年包月(批量)
请求地址: [cdsapi.capitalonline.net/gcw](http://cdsapi.capitalonline.net/gcw)
请求方法: Post

请求参数：

| 名称          | 类型   | 是否必须 | 示例                                     | 描述                                                         |
| ------------- | ------ | -------- | ---------------------------------------- | ------------------------------------------------------------ |
| requestId     | string | 是       | “ebbfcb70-a98f-11ec-926b-8aaa763f849e”   | 请求uuid                                                     |
| vmIds         | array  | 是       | [“1f08cc62-c24b-46dd-b190-bf139d00ee82”] | vm ids                                                       |
| isToMonth     | string | 否       | ”0“                                      | 包月是否到月底 1是到月底，0否，默认为0 如：包月开始时间为 2022.6.22 12:19:08isToMonth为1，duration为1，则包月到2022.7.1 00:00:00isToMonth为0，duration为1，则包整月到2022.7.22 12:19:08isToMonth为1，duration为6，则包整月到2022.12.1 12:19:08 isToMonth为0，duration为6，则包整月到2022.12.22 12:19:08 |
| duration      | string | 否       | ”1“                                      | 包月周期数，3个月传3,5个月传5；默认为1                       |
| isAutoRenewal | string | 否       | ”0“                                      | 包月是否续约 1是0否 ， 默认为0                               |

返回数据：

| 名称           | 类型   | 示例                                     | 描述                      |
| -------------- | ------ | ---------------------------------------- | ------------------------- |
| code           | string | Success                                  | 返回状态码: Success: 成功 |
| msg            | string | null                                     | 返回信息                  |
| data           | object | {}                                       | 返回数据                  |
| successVmIds   | array  | [“1f08cc62-c24b-46dd-b190-bf139d00ee82”] | 按需转包年包月成功 vmIds  |
| failedVmIds    | array  | []                                       | 按需转包年包月失败 vmIds  |
| failedMsg      | string | “”                                       | 失败信息                  |
| requestId      | string | “ebbfcb70-a98f-11ec-926b-8aaa763f849e”   | 请求uuid                  |
| requestContent | string | “”                                       | 请求参数                  |

错误码：

| 错误码 | 错误信息                                                     | 描述                                                         |
| ------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 12503  | 该接口只能修改按需计费为包年包月，不可修改包年包月状态，修改包年包月请调用续约接口 | 该接口只能修改按需计费为包年包月，不可修改包年包月状态，修改包年包月请调用续约接口 |
| 12501  | 当前用户包月购买已达配额上限，请修改计费方式或联系销售人员增加包月配额 | 当前用户包月购买已达配额上限，请修改计费方式或联系销售人员增加包月配额 |
| 12506  | 云桌面订按需转包年包月失败                                   | 云桌面订按需转包年包月失败                                   |
| 10003  | 传入参数不符合要求                                           | 传入参数不符合要求，包月购买时长需大于等于1                  |
| 10006  | 参数错误                                                     | 参数错误，对应云桌面不存在                                   |

返回示例

```json

{
    "Code": "Success",
    "Data": {
        "failedMsg": "",
        "failedVmIds": [],
        "requestContent": "{\"billCycle\":\"month\",\"customerId\":\"E2129298\",\"duration\":1,\"isAutoRenewal\":0,\"isToMonth\":1,\"requestId\":\"ebbfcb70-a98f-11ec-926b-8aaa763f849e\",\"userFrom\":\"cdsapi\",\"userId\":\"713367\",\"vmIds\":[\"1f08cc62-c24b-46dd-b190-bf139d00ee82\"]}",
        "requestId": "ebbfcb70-a98f-11ec-926b-8aaa763f849e",
        "successVmIds": [
            "1f08cc62-c24b-46dd-b190-bf139d00ee82"
        ]
    },
    "Message": ""
}

```

代码调用示例

```python
def updateOrder():
    '''
    按需转包年包月(批量)
    :return:
    '''
    action = "UpdateOrder"
    method = "POST"
    body = {
        "requestId": "ebbfcb70-a98f-11ec-926b-8aaa763f849e",
        "vmIds": ["1f08cc62-c24b-46dd-b190-bf139d00ee82"],
        "isToMonth": "1",
        "duration": "1",
        "isAutoRenewal": "0"
    }
    url = getUrl(action, AK, AccessKeySecret, method, CCS_URL, param={})
    res = requests.post(url,json=body)
    result = json.loads(res.content)
    print(result)
    if result.get("Code") != "Success":
        print ("request error: %s" % result.get("Message"))
    return result

```

# 7. RenewalOrder

Action: RenewalOrder
描述: 包年包月续约(批量)
请求地址: [cdsapi.capitalonline.net/gcw](http://cdsapi.capitalonline.net/gcw)
请求方法: Post

请求参数：

| 名称          | 类型   | 是否必须 | 示例                                     | 描述                                                         |
| ------------- | ------ | -------- | ---------------------------------------- | ------------------------------------------------------------ |
| requestId     | string | 是       | “ebbfcb70-a98f-11ec-926b-8aaa763f849e”   | 请求uuid                                                     |
| vmIds         | array  | 是       | [“1f08cc62-c24b-46dd-b190-bf139d00ee82”] | vm ids                                                       |
| duration      | string | 否       | ”1“                                      | 包月周期数，3个月传3,5个月传5；默认为1                       |
| priceToMonth  | string | 否       | ”0“                                      | 包月到月底，不足整月时是否按整月收费 0：否 1:是 默认为0      |
| isToMonth     | string | 否       | ”0“                                      | 包月是否到月底 1是到月底，0否 ， 默认为0  如：包月开始时间为 2022.6.22 12:19:08isToMonth为1，duration为1，则包月到2022.7.1 00:00:00isToMonth为0，duration为1，则包整月到2022.7.22 12:19:08isToMonth为1，duration为6，则包整月到2022.12.1 12:19:08 isToMonth为0，duration为6，则包整月到2022.12.22 12:19:08 |
| isAutoRenewal | string | 否       | ”1“                                      | 包月是否续约 1是0否 ， 默认为1                               |

返回数据：

| 名称           | 类型   | 示例                                     | 描述                      |
| -------------- | ------ | ---------------------------------------- | ------------------------- |
| code           | string | Success                                  | 返回状态码: Success: 成功 |
| msg            | string | null                                     | 返回信息                  |
| data           | object | {}                                       | 返回数据                  |
| successVmIds   | array  | [“1f08cc62-c24b-46dd-b190-bf139d00ee82”] | 续约成功 vmIds            |
| failedVmIds    | array  | []                                       | 续约失败 vmIds            |
| failedMsg      | string | “”                                       | 失败信息                  |
| requestId      | string | “ebbfcb70-a98f-11ec-926b-8aaa763f849e”   | 请求uuid                  |
| requestContent | string | “”                                       | 请求参数                  |

错误码：

| 错误码 | 错误信息                                                     | 描述                                                         |
| ------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 12504  | 该接口只用于续约包年包月，按需转包年包月请调用修改计费方案接口 | 该接口只用于续约包年包月，按需转包年包月请调用修改计费方案接口 |
| 12500  | 订单更新续约失败                                             | 订单更新续约失败                                             |
| 10003  | 传入参数不符合要求                                           | 传入参数不符合要求，包月是否续约可选值为0或1,1是续约,0是不续约 |
| 10006  | 参数错误                                                     | 参数错误，对应云桌面不存在                                   |

返回示例

```json

{
    "Code": "Success",
    "Data": {
        "failedMsg": "",
        "failedVmIds": [],
        "requestContent": "{\"billCycle\":\"month\",\"customerId\":\"E2129298\",\"duration\":1,\"isAutoRenewal\":1,\"isToMonth\":1,\"priceToMonth\":1,\"requestId\":\"ebbfcb70-a98f-11ec-926b-8aaa763f849e\",\"userFrom\":\"cdsapi\",\"userId\":\"713367\",\"vmIds\":[\"1f08cc62-c24b-46dd-b190-bf139d00ee82\"]}",
        "requestId": "ebbfcb70-a98f-11ec-926b-8aaa763f849e",
        "successVmIds": [
            "1f08cc62-c24b-46dd-b190-bf139d00ee82"
        ]
    },
    "Message": ""
}

```

代码调用示例

```python
def renewalOrder():
    '''
    包年包月续约(批量)
    :return:
    '''
    action = "RenewalOrder"
    method = "POST"
    body = {
        "requestId": "ebbfcb70-a98f-11ec-926b-8aaa763f849e",
        "vmIds": ["1f08cc62-c24b-46dd-b190-bf139d00ee82"],
        "duration": "1",
        "priceToMonth": "1",
        "isToMonth": "1",
        "isAutoRenewal": "1"
    }
    url = getUrl(action, AK, AccessKeySecret, method, CCS_URL, param={})
    res = requests.post(url,json=body)
    result = json.loads(res.content)
    print(result)
    if result.get("Code") != "Success":
        print ("request error: %s" % result.get("Message"))
    return result

```



# 8. QuerySubAccounts

Action: QuerySubAccounts
描述: 查询子账户集合
请求地址: [cdsapi.capitalonline.net/gcw](http://cdsapi.capitalonline.net/gcw)
请求方法: Get

请求参数：

| 名称   | 类型   | 是否必须 | 示例                            | 描述       |
| ------ | ------ | -------- | ------------------------------- | ---------- |
| email  | string | 否       | “cds@[163.com](http://163.com)” | 用户邮箱   |
| name   | string | 否       | “cds”                           | 用户的名称 |
| remark | string | 否       | “cds”                           | 备注       |

返回数据：

| 名称      | 类型   | 示例                                   | 描述                                                         |
| --------- | ------ | -------------------------------------- | ------------------------------------------------------------ |
| code      | string | Success                                | 返回状态码: Success: 成功                                    |
| msg       | string | null                                   | 返回信息                                                     |
| data      | list   | []                                     | 返回数据                                                     |
| accountId | string | “7e7ba91e-4357-470a-9609-ce60d9d7e38f” | 用户id                                                       |
| name      | string | “miao123”                              | 用户的名称                                                   |
| email     | string | “”                                     | 邮箱                                                         |
| remark    | string | “miao123”                              | 备注                                                         |
| bindNum   | int    | 0                                      | 已绑定云桌面的数量                                           |
| status    | string | “create”                               | 账户状态，creating(创建中)，create(创建完成),error(创建失败) |

错误码：

| 错误码 | 错误信息 | 描述 |
| ------ | -------- | ---- |
|        |          |      |

返回示例

```json
{
    "Code": "Success",
    "Data": [
        {
            "accountId": "7e7ba91e-4357-470a-9609-ce60d9d7e38f",
            "bindNum": 0,
            "email": "17716313367@163.com",
            "name": "miao123",
            "remark": "miao123"
        }
    ],
    "Message": ""
}

```

代码调用示例

```python
def querySubAccounts():
    '''
    查询子账户集合
    :return:
    '''
    action = "QuerySubAccounts"
    method = "GET"
    param = {}
    url = getUrl(action, AK, AccessKeySecret, method, CCS_URL, param=param)
    res = requests.get(url)
    result = json.loads(res.content)
    print(result)
    if result.get("Code") != "Success":
        print ("request error: %s" % result.get("Message"))
    return result

```

# 9. CreateSubAccount

Action: CreateSubAccount
描述: 创建子账户
请求地址: [cdsapi.capitalonline.net/gcw](http://cdsapi.capitalonline.net/gcw)
请求方法: Post

请求参数：

| 名称      | 类型   | 是否必须 | 示例                                    | 描述                                                         |
| --------- | ------ | -------- | --------------------------------------- | ------------------------------------------------------------ |
| requestId | string | 是       | “ebbfcb70-a98f-11ec-926b-8aaa763f849e”  | 请求uuid                                                     |
| email     | string | 是       | “17716313367@[163.com](http://163.com)” | 用户邮箱                                                     |
| name      | string | 是       | miao123                                 | 用户的名称                                                   |
| remark    | string | 否       | “miao123”                               | 备注，，子账户备注长度应长度不大于30位，支持汉字、英文、数字、符号 |

返回数据：

| 名称 | 类型   | 示例    | 描述                      |
| ---- | ------ | ------- | ------------------------- |
| code | string | Success | 返回状态码: Success: 成功 |
| msg  | string | null    | 返回信息                  |
| data | obejct | {}      | 返回数据                  |

错误码：

| 错误码 | 错误信息           | 描述               |
| ------ | ------------------ | ------------------ |
| 10003  | 传入参数不符合要求 | 传入参数不符合要求 |
| 10005  | 账户数据异常       | 账户数据异常       |
| 11000  | 创建用户错误       | 创建用户错误       |

返回示例

```json
{
    "Code": "Success",
    "Data": null,
    "Message": ""
}

```

代码调用示例

```python
def createSubAccount():
    '''
    创建子账户
    :return:
    '''
    action = "CreateSubAccount"
    method = "POST"
    body = {
        "requestId": "ebbfcb70-a98f-11ec-926b-8aaa763f849e",
        "name": "miao123",
        "email": "17716313367@163.com",
        "remark": "miao123"
    }
    url = getUrl(action, AK, AccessKeySecret, method, CCS_URL, param={})
    res = requests.post(url,json=body)
    result = json.loads(res.content)
    print(result)
    if result.get("Code") != "Success":
        print ("request error: %s" % result.get("Message"))
    return result

```

# 10. CreateSubAccounts

Action: CreateSubAccounts
描述: 批量创建子账户
请求地址: [cdsapi.capitalonline.net/gcw](http://cdsapi.capitalonline.net/gcw)
请求方法: Post

请求参数：

| 名称                | 类型   | 是否必须 | 示例                                    | 描述                                                         |
| ------------------- | ------ | -------- | --------------------------------------- | ------------------------------------------------------------ |
| requestId           | string | 是       | “ebbfcb70-a98f-11ec-926b-8aaa763f849e”  | 请求uuid                                                     |
| createAccountParams | list   | 是       | []                                      | 账户参数                                                     |
| email               | string | 是       | “17716313367@[163.com](http://163.com)” | 用户邮箱                                                     |
| name                | string | 是       | “miao123”                               | 用户的名称                                                   |
| remark              | string | 否       | “miao123”                               | 备注，子账户备注长度应长度不大于30位，支持汉字、英文、数字、符号 |

返回数据：

| 名称       | 类型   | 示例                                                       | 描述                      |
| ---------- | ------ | ---------------------------------------------------------- | ------------------------- |
| code       | string | Success                                                    | 返回状态码: Success: 成功 |
| msg        | string | null                                                       | 返回信息                  |
| data       | obejct | {}                                                         | 返回数据                  |
| failedNum  | int    | 0                                                          | 失败数量                  |
| successNum | int    | 1                                                          | 成功数量                  |
| failedMsgs | list   | [ ]                                                        | 失败错误信息              |
| name       | string | miao1233333                                                | 用户的名称                |
| email      | string | [3121111111@163.com](mailto:3121111111@163.com)            | 用户邮箱                  |
| remark     | string | miao123aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa                   | 备注                      |
| messsage   | string | 子账户备注长度应长度不大于30位，支持汉字、英文、数字、符号 | 错误信息                  |

错误码：

| 错误码 | 错误信息           | 描述               |
| ------ | ------------------ | ------------------ |
| 10003  | 传入参数不符合要求 | 传入参数不符合要求 |
| 10005  | 账户数据异常       | 账户数据异常       |
| 11003  | 批量创建用户失败   | 批量创建用户失败   |

返回示例

```json
{
    "Code": "Success",
    "Data": {
        "failedNum": 1,
        "successNum": 0,
        "failedMsgs": [
           {
               "name": "miao1233333",
               "email": "3121111111@163.com",
               "remark": "miao123aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
                "messsage": "子账户备注长度应长度不大于30位，支持汉字、英文、数字、符号"
            }
         ]
    },
    "Message": ""
}

```

代码调用示例

```python
def createSubAccounts():
    '''
    批量创建子账户
    :return:
    '''
    action = "CreateSubAccounts"
    method = "POST"
    body = {
        "requestId": "ebbfcb70-a98f-11ec-926b-8aaa763f849e",
        "createAccountParams":[
            {
                "name": "miao123",
                "email": "17716313367@163.com",
                "remark": "miao123"
            }
        ]
    }
    url = getUrl(action, AK, AccessKeySecret, method, CCS_URL, param={})
    res = requests.post(url,json=body)
    result = json.loads(res.content)
    print(result)
    if result.get("Code") != "Success":
        print ("request error: %s" % result.get("Message"))
    return result

```

# 11. ChangeSubAccountName

Action: ChangeSubAccountName
描述: 修改子账名字
请求地址: [cdsapi.capitalonline.net/gcw](http://cdsapi.capitalonline.net/gcw)
请求方法: Post

请求参数：

| 名称      | 类型   | 是否必须 | 示例                                    | 描述     |
| --------- | ------ | -------- | --------------------------------------- | -------- |
| requestId | string | 是       | “ebbfcb70-a98f-11ec-926b-8aaa763f849e”  | 请求uuid |
| email     | string | 是       | “17716313367@[163.com](http://163.com)” | 账户邮箱 |
| name      | string | 是       | “miao23456”                             | 用户名   |

返回数据：

| 名称      | 类型   | 示例    | 描述                      |
| --------- | ------ | ------- | ------------------------- |
| code      | string | Success | 返回状态码: Success: 成功 |
| msg       | string | null    | 返回信息                  |
| data      | obejct | {}      | 返回数据                  |
| requestId | string |         | “”                        |

错误码：

| 错误码 | 错误信息           | 描述                |
| ------ | ------------------ | ------------------- |
| 10003  | 传入参数不符合要求 | 传入参数不符合要求  |
| 10211  | 修改用户名失败     | 修改用户名失败      |
| 10006  | 参数错误           | 参数错误,无对应账户 |

返回示例

```json
{
    "Code": "Success",
    "Data": null,
    "Message": ""
}

```

代码调用示例

```python
def changeSubAccountName():
    '''
    修改子账名字
    :return:
    '''
    action = "ChangeSubAccountName"
    method = "POST"
    body = {
        "requestId": "ebbfcb70-a98f-11ec-926b-8aaa763f849e",
        "email":"17716313367@163.com",
        "name": "miao23456"
    }
    url = getUrl(action, AK, AccessKeySecret, method, CCS_URL, param={})
    res = requests.post(url,json=body)
    result = json.loads(res.content)
    print(result)
    if result.get("Code") != "Success":
        print ("request error: %s" % result.get("Message"))
    return result

```

# 12. ChangeSubAccountRemark

Action: ChangeSubAccountRemark
描述: 修改子账户备注 (批量)
请求地址: [cdsapi.capitalonline.net/gcw](http://cdsapi.capitalonline.net/gcw)
请求方法: Post

请求参数：

| 名称      | 类型   | 是否必须 | 示例                                      | 描述                                                         |
| --------- | ------ | -------- | ----------------------------------------- | ------------------------------------------------------------ |
| requestId | string | 是       | “ebbfcb70-a98f-11ec-926b-8aaa763f849e”    | 请求uuid                                                     |
| emails    | array  | 是       | [“17716313367@[163.com](http://163.com)”] | 账户邮箱集合                                                 |
| remark    | string | 是       | “miao23456”                               | 备注，子账户备注长度应长度不大于30位，支持汉字、英文、数字、符号 |

返回数据：

| 名称      | 类型   | 示例    | 描述                      |
| --------- | ------ | ------- | ------------------------- |
| code      | string | Success | 返回状态码: Success: 成功 |
| msg       | string | null    | 返回信息                  |
| data      | obejct | {}      | 返回数据                  |
| requestId | string |         | “”                        |

错误码：

| 错误码 | 错误信息           | 描述                 |
| ------ | ------------------ | -------------------- |
| 10003  | 传入参数不符合要求 | 传入参数不符合要求   |
| 11013  | 修改用户备注失败   | 修改用户备注失败     |
| 10006  | 参数错误           | 参数错误，无对应账户 |

返回示例

```json

{
    "Code": "Success",
    "Data": null,
    "Message": ""
}

```

代码调用示例

```python

def changeSubAccountRemark():
    '''
    修改子账户备注 (批量)
    :return:
    '''
    action = "ChangeSubAccountRemark"
    method = "POST"
    body = {
        "requestId": "ebbfcb70-a98f-11ec-926b-8aaa763f849e",
        "emails":["17716313367@163.com"],
        "remark": "miao23456"
    }
    url = getUrl(action, AK, AccessKeySecret, method, CCS_URL, param={})
    res = requests.post(url,json=body)
    result = json.loads(res.content)
    print(result)
    if result.get("Code") != "Success":
        print ("request error: %s" % result.get("Message"))
    return result

```



# 13. CreateDefaultNet

Action: CreateDefaultNet
描述: 创建vpc与虚拟出网网关资源
请求地址: [cdsapi.capitalonline.net/gcw](http://cdsapi.capitalonline.net/gcw)
请求方法: POST

请求参数：

| 名称      | 类型   | 是否必须 | 示例                                 | 描述         |
| --------- | ------ | -------- | ------------------------------------ | ------------ |
| siteId    | string | 是       | 35304122-8504-400c-a61c-56ba244c5dda | 站点id       |
| requestId | string | 是       | 6ca9ed98-27c8-4431-995f-59cc6d743dab | 请求标识uuid |

返回数据：

| 名称           | 类型   | 示例                                   | 描述                      |
| -------------- | ------ | -------------------------------------- | ------------------------- |
| Code           | string | Success                                | 返回状态码: Success: 成功 |
| Message        | string | null                                   | 返回信息                  |
| Data           | object | {}                                     | 返回数据                  |
| requestId      | string | “6ca9ed98-27c8-4431-995f-59cc6d743dab” | 请求标识uuid              |
| taskId         | string | “d460f799-6896-4d93-b037-02ee2efb3adb” | 任务id                    |
| requestContent | string | “”                                     | 请求参数                  |

错误码：

| 错误码 | 错误信息           | 描述                         |
| ------ | ------------------ | ---------------------------- |
| 10003  | 传入参数不符合要求 | 传入参数不符合要求           |
| 10005  | 账户数据异常       | 用户账户数据查询失败         |
| 13500  | 一键创建失败       | 一键创建失败                 |
| 10007  | 当前账户权限不足   | 当前账户权限不足             |
| 10006  | 参数错误           | 参数错误，对应站点信息不存在 |

返回示例

```json
{
    "Code": "Success",
    "Data": {
        "requestContent": "{\"customerId\":\"CDS01555\",\"requestId\":\"6ca9ed98-27c8-4431-995f-59cc6d743dab\",\"siteId\":\"32e6fd62-9bac-11ec-875a-2a8d1f4e167e\",\"userFrom\":\"cdsapi\",\"userId\":\"715923\"}",
        "requestId": "6ca9ed98-27c8-4431-995f-59cc6d743dab",
        "taskId": "d460f799-6896-4d93-b037-02ee2efb3adb"
    },
    "Message": ""
}

```

代码调用示例

```python
def createDefaultNet():
    '''
    创建vpc与虚拟出网网关资源
    :return:
    '''
    action = "CreateDefaultNet"
    method = "POST"
    body = {
        "siteId": "32e6fd62-9bac-11ec-875a-2a8d1f4e167e",
        "requestId": "6ca9ed98-27c8-4431-995f-59cc6d743dab"
    }
    url = getUrl(action, AK, AccessKeySecret, method, CCS_URL, param={})
    res = requests.post(url,json=body)
    result = json.loads(res.content)
    print(result)
    if result.get("Code") != "Success":
        print ("request error: %s" % result.get("Message"))
    return result

```

# 14. SupplyDefaultNet

Action: SupplyDefaultNet
描述: 一键补全vpc的子网与虚拟出网网关
请求地址: [cdsapi.capitalonline.net/gcw](http://cdsapi.capitalonline.net/gcw)
请求方法: POST

请求参数：

| 名称      | 类型   | 是否必须 | 示例                                 | 描述         |
| --------- | ------ | -------- | ------------------------------------ | ------------ |
| siteId    | string | 是       | 35304122-8504-400c-a61c-56ba244c5dda | 站点id       |
| requestId | string | 是       | 6ca9ed98-27c8-4431-995f-59cc6d743dab | 请求标识uuid |

返回数据：

| 名称           | 类型   | 示例                                   | 描述                      |
| -------------- | ------ | -------------------------------------- | ------------------------- |
| Code           | string | Success                                | 返回状态码: Success: 成功 |
| Message        | string | null                                   | 返回信息                  |
| Data           | object | {}                                     | 返回数据                  |
| requestId      | string | “6ca9ed98-27c8-4431-995f-59cc6d743dab” | 请求标识uuid              |
| taskId         | string | “d460f799-6896-4d93-b037-02ee2efb3adb” | 任务id                    |
| requestContent | string | “”                                     | 请求参数                  |

错误码：

| 错误码 | 错误信息           | 描述                         |
| ------ | ------------------ | ---------------------------- |
| 10003  | 传入参数不符合要求 | 传入参数不符合要求           |
| 10005  | 账户数据异常       | 用户账户数据查询失败         |
| 13506  | 补全vpc网络失败    | 补全vpc网络失败              |
| 10007  | 当前账户权限不足   | 当前账户权限不足             |
| 10006  | 参数错误           | 参数错误，对应站点信息不存在 |

返回示例

```json
{
    "Code": "Success",
    "Data": {
        "requestContent": "{\"customerId\":\"CDS01555\",\"requestId\":\"6ca9ed98-27c8-4431-995f-59cc6d743dab\",\"siteId\":\"32e6fd62-9bac-11ec-875a-2a8d1f4e167e\",\"userFrom\":\"cdsapi\",\"userId\":\"715923\"}",
        "requestId": "6ca9ed98-27c8-4431-995f-59cc6d743dab",
        "taskId": "d460f799-6896-4d93-b037-02ee2efb3adb"
    },
    "Message": ""
}

```

代码调用示例

```python
def supplyDefaultNet():
    '''
    一键补全vpc的子网与虚拟出网网关
    :return:
    '''
    action = "SupplyDefaultNet"
    method = "POST"
    body = {
        "siteId": "32e6fd62-9bac-11ec-875a-2a8d1f4e167e",
        "requestId": "6ca9ed98-27c8-4431-995f-59cc6d743dab"
    }
    url = getUrl(action, AK, AccessKeySecret, method, CCS_URL, param={})
    res = requests.post(url,json=body)
    result = json.loads(res.content)
    print(result)
    if result.get("Code") != "Success":
        print ("request error: %s" % result.get("Message"))
    return result

```

# 15. GetDefaultNet

Action: GetDefaultNet
描述: 查询vpc与虚拟出网网关资源(调用CreateDefaultNet创建的默认网络配置)
请求地址: [cdsapi.capitalonline.net/gcw](http://cdsapi.capitalonline.net/gcw)
请求方法: Get

请求参数：

| 名称      | 类型   | 是否必须 | 示例                                 | 描述         |
| --------- | ------ | -------- | ------------------------------------ | ------------ |
| siteId    | string | 是       | 32e6fd62-9bac-11ec-875a-2a8d1f4e167e | 站点id       |
| requestId | string | 是       | 6ca9ed98-27c8-4431-995f-59cc6d743dab | 请求标识uuid |

返回数据：

| 名称        | 类型    | 示例                                 | 描述                                                         |
| ----------- | ------- | ------------------------------------ | ------------------------------------------------------------ |
| Code        | string  | Success                              | 返回状态码: Success: 成功                                    |
| Message     | string  | null                                 | 返回信息                                                     |
| Data        | object  | {}                                   | 返回数据                                                     |
| id          | Integer | 112                                  | 主键id                                                       |
| vpcRecordId | string  | c382a49c-942f-4389-af2b-7a81a7fee4d0 | vpc记录 id                                                   |
| cityId      | string  | 30044852-a985-11ec-82c4-bec056b60a5c | vpc所属区域Id                                                |
| vpcId       | string  | 3da4a818-80df-11ec-8c71-9291e2ce70c4 | vpc id                                                       |
| vpcName     | string  | 云桌面默认VPC                        | vpc名字                                                      |
| vpcSegment  | string  | 10.0.0.0/8                           | cidr规则的vpc网段                                            |
| customerId  | string  | E888825                              | 客户ID                                                       |
| userId      | string  | 571085                               | 用户ID                                                       |
| createTime  | Date    | 2022-01-29 16:41:34                  | 创建时间                                                     |
| updateTime  | Date    | 2022-01-29 16:41:34                  | 更新时间                                                     |
| deleteFlag  | boolean | false                                | 删除标识                                                     |
|             |         |                                      |                                                              |
| subnets     | list    | [ ]                                  | 子网集合                                                     |
| vGateways   | list    | [ ]                                  | 虚拟网关集合                                                 |
|             |         |                                      |                                                              |
| status      | string  | ok                                   | 状态 , ok ,erro ,creating ,deleting ,updating ,deleted ,shutdown ,stopping , starting |
| status_str  | string  | 正常                                 | 状态name, 正常 , 错误 , 创建中 , 删除中 , 更新中 , 已删除 , 等待删除 , 禁用中 , 启用中 |
| name        | string  | 子网1                                | 名称                                                         |
| not_used    | Integer | 65521                                | 未使用ip数量                                                 |
| used_num    | Integer | 15                                   | 已使用ip数量                                                 |
| mask        | Integer | 16                                   | 掩码                                                         |
| id          | String  | 3dabf76c-80df-11ec-8c71-9291e2ce70c4 | id                                                           |
| dns         | String  | [“8.8.8.8”,“8.8.4.4”]                | dns                                                          |
| ip_type     | String  | subnet                               | 网络类型：pubnet(“公网”), subnet( “子网”),virtual_gateway( “虚拟出网网”) |
| ip_address  | String  | "10.1.0.0                            | ip                                                           |
| gateway     | String  | 10.1.0.1                             | 网关                                                         |
| vlan_id     | String  | 2911                                 | vlan id                                                      |
| conf_id     | String  | 1216                                 | 带宽类型 id                                                  |
| conf_name   | String  | 电信                                 | 带宽类型名字                                                 |

错误码：

| 错误码 | 错误信息                | 描述                    |
| ------ | ----------------------- | ----------------------- |
| 13502  | 查询vpc与可用区信息失败 | 服务错误查询失败        |
| 10003  | 传入参数不符合要求      | 传入参数不符合要求      |
| 10006  | 参数错误                | 参数错误,无对应站点信息 |

返回示例

```json
{
    "Code": "Success",
    "Data": {
        "cityId": "30044852-a985-11ec-82c4-bec056b60a5c",
      "createTime": "2022-05-07 14:03:44",
        "customerId": "E2129298",
        "deleteFlag": false,
        "id": 476,
        "subnets": [
            {
                "dns": "[\"119.29.29.29\",\"114.114.114.114\"]",
                "gateway": "10.1.0.1",
                "id": "73d2c7ec-cdcb-11ec-a318-ee97882ecf7d",
                "ip_address": "10.1.0.0",
                "ip_type": "subnet",
                "mask": 16,
                "name": "子网1",               
                "not_used": 65520,
                "used_num": 16,
            "status": "ok",
                "status_str": "正常",
                "vlan_id": "1704"
            }
        ],
        "updateTime": "2022-05-07 14:04:35",
        "userId": "713367",
        "vgateways": [
            {
                "conf_id": "10289",
                "conf_name": "电信",
                "dns": "[\"119.29.29.29\",\"114.114.114.114\"]",
                "gateway": "10.2.0.1",
                "id": "8054ab84-cdcb-11ec-a318-ee97882ecf7d",
                "ip_address": "10.2.0.0",
                "ip_type": "virtual_gateway",
                "mask": 16,
                "name": "电信默认网关",                
                "not_used": 65520,
                "used_num": 16,
            "status": "ok",
                "status_str": "正常",
                "vlan_id": "1431"
            },
            {
                "conf_id": "10298",
                "conf_name": "移动",
                "dns": "[\"119.29.29.29\",\"114.114.114.114\"]",
                "gateway": "10.3.0.1",
                "id": "80587138-cdcb-11ec-a318-ee97882ecf7d",
                "ip_address": "10.3.0.0",
                "ip_type": "virtual_gateway",
                "mask": 16,
                "name": "移动默认网关",                
                "not_used": 65520,
                "used_num": 16,
           "status": "ok",
                "status_str": "正常",
                "vlan_id": "1767"
            }
        ],
        "vpcId": "73cbf764-cdcb-11ec-a318-ee97882ecf7d",
        "vpcName": "娄底-云桌面默认VPC",
        "vpcRecordId": "201bda0c-7cea-420b-b812-91a76aacfbd1",
        "vpcSegment": "10.0.0.0/8"
    },
    "Message": ""
}

```

代码调用示例

```python
def getDefaultNet():
    '''
    查询vpc与虚拟出网网关资源
    :return:
    '''
    action = "GetDefaultNet"
    method = "GET"
    param = {"siteId": "ebbfcb70-a98f-11ec-926b-8aaa763f849e", "requestId": "6ca9ed98-27c8-4431-995f-59cc6d743dab"}
    url = getUrl(action, AK, AccessKeySecret, method, CCS_URL, param=param)
    res = requests.get(url)
    result = json.loads(res.content)
    print(result)
    if result.get("Code") != "Success":
        print ("request error: %s" % result.get("Message"))
    return result

```



# 16. GetCustomNet

Action: GetCustomNet
描述: 查询vpc与虚拟出网网关资源(该账户下所有的自定义网络配置)
请求地址: [cdsapi.capitalonline.net/gcw](http://cdsapi.capitalonline.net/gcw)
请求方法: Get

请求参数：

| 名称      | 类型   | 是否必须 | 示例                                 | 描述         |
| --------- | ------ | -------- | ------------------------------------ | ------------ |
| siteId    | string | 是       | 32e6fd62-9bac-11ec-875a-2a8d1f4e167e | 站点id       |
| requestId | string | 是       | 6ca9ed98-27c8-4431-995f-59cc6d743dab | 请求标识uuid |

返回数据：

| 名称       | 类型    | 示例                                 | 描述                                                         |
| ---------- | ------- | ------------------------------------ | ------------------------------------------------------------ |
| Code       | string  | Success                              | 返回状态码: Success: 成功                                    |
| Message    | string  | null                                 | 返回信息                                                     |
| Data       | list    | [ ]                                  | 返回数据                                                     |
| vpcId      | string  | 3da4a818-80df-11ec-8c71-9291e2ce70c4 | vpc id                                                       |
| vpcName    | string  | 云桌面默认VPC                        | vpc名字                                                      |
| vpcSegment | string  | 10.0.0.0/8                           | cidr规则的vpc网段                                            |
| customerId | string  | E888825                              | 客户ID                                                       |
| userId     | string  | 571085                               | 用户ID                                                       |
|            |         |                                      |                                                              |
| subnets    | List    | [ ]                                  | 子网集合                                                     |
| vGateways  | List    | [ ]                                  | 虚拟网关集合                                                 |
|            |         |                                      |                                                              |
| status     | string  | ok                                   | 状态 , ok ,erro ,creating ,deleting ,updating ,deleted ,shutdown ,stopping , starting |
| status_str | string  | 正常                                 | 状态name, 正常 , 错误 , 创建中 , 删除中 , 更新中 , 已删除 , 等待删除 , 禁用中 , 启用中 |
| name       | string  | 子网1                                | 名称                                                         |
| not_used   | Integer | 65521                                | 未使用ip数量                                                 |
| used_num   | Integer | 15                                   | 已使用ip数量                                                 |
| mask       | Integer | 16                                   | 掩码                                                         |
| id         | String  | 3dabf76c-80df-11ec-8c71-9291e2ce70c4 | id                                                           |
| dns        | String  | [“8.8.8.8”,“8.8.4.4”]                | dns                                                          |
| ip_type    | String  | subnet                               | 网络类型：pubnet(“公网”), subnet( “子网”),virtual_gateway( “虚拟出网网”) |
| ip_address | String  | "10.1.0.0                            | ip                                                           |
| gateway    | String  | 10.1.0.1                             | 网关                                                         |
| vlan_id    | String  | 2911                                 | vlan id                                                      |
| conf_id    | String  | 1216                                 | 带宽类型 id                                                  |
| conf_name  | String  | 电信                                 | 带宽类型名字                                                 |

错误码：

| 错误码 | 错误信息                | 描述                    |
| ------ | ----------------------- | ----------------------- |
| 13502  | 查询vpc与可用区信息失败 | 服务错误查询失败        |
| 10003  | 传入参数不符合要求      | 传入参数不符合要求      |
| 10006  | 参数错误                | 参数错误,无对应站点信息 |

返回示例

```json
{
    "Code": "Success",
    "Data": [
        {
            "customerId": "CDS01555",
            "subnets": [
                {
                    "dns": "[\"119.29.29.29\",\"114.114.114.114\"]",
                    "gateway": "10.1.0.1",
                    "id": "2c93fcac-d749-11ec-9fb4-ca91557d24a6",
                    "ip_address": "10.1.0.0",
                    "ip_type": "subnet",
                    "mask": 16,
                    "name": "子网1",                   
                    "not_used": 65520,
                    "used_num": 16,
              "status": "ok",
                    "status_str": "正常",
                    "vlan_id": "1768"
                }
            ],
            "userId": "715923",
             "vgateways": [
            {
                "conf_id": "10289",
                "conf_name": "电信",
                "dns": "[\"119.29.29.29\",\"114.114.114.114\"]",
                "gateway": "10.2.0.1",
                "id": "8054ab84-cdcb-11ec-a318-ee97882ecf7d",
                "ip_address": "10.2.0.0",
                "ip_type": "virtual_gateway",
                "mask": 16,
                "name": "电信默认网关",                
                "not_used": 65520,
                "used_num": 16,
           "status": "ok",
                "status_str": "正常",
                "vlan_id": "1431"
            },
            {
                "conf_id": "10298",
                "conf_name": "移动",
                "dns": "[\"119.29.29.29\",\"114.114.114.114\"]",
                "gateway": "10.3.0.1",
                "id": "80587138-cdcb-11ec-a318-ee97882ecf7d",
                "ip_address": "10.3.0.0",
                "ip_type": "virtual_gateway",
                "mask": 16,
                "name": "移动默认网关",                
                "not_used": 65520,
                "used_num": 16,
            "status": "ok",
                "status_str": "正常",
                "vlan_id": "1767"
            }
        ],
            "vpcId": "2c869a08-d749-11ec-9fb4-ca91557d24a6",
            "vpcName": "襄阳-云桌面默认VPC",
            "vpcSegment": "10.0.0.0/8"
        }
    ],
    "Message": ""
}

```

代码调用示例

```python
def getCustomNet():
    '''
    查询vpc与虚拟出网网关资源
    :return:
    '''
    action = "GetCustomNet"
    method = "GET"
    param = {"siteId": "32e6fd62-9bac-11ec-875a-2a8d1f4e167e", "requestId": "6ca9ed98-27c8-4431-995f-59cc6d743dab"}
    url = getUrl(action, AK, AccessKeySecret, method, CCS_URL, param=param)
    res = requests.get(url)
    result = json.loads(res.content)
    print(result)
    if result.get("Code") != "Success":
        print ("request error: %s" % result.get("Message"))
    return result

```



# 17. GetLineBillingScheme

Action: GetLineBillingScheme
描述: 获取线路及其计费方案
请求地址: [cdsapi.capitalonline.net/gcw](http://cdsapi.capitalonline.net/gcw)
请求方法: Get

请求参数：

| 名称      | 类型   | 是否必须 | 示例                                 | 描述         |
| --------- | ------ | -------- | ------------------------------------ | ------------ |
| siteId    | string | 是       | 35304122-8504-400c-a61c-56ba244c5dda | 站点id       |
| requestId | string | 是       | 6ca9ed98-27c8-4431-995f-59cc6d743dab | 请求标识uuid |

返回数据：

| 名称                | 类型   | 示例                                   | 描述                             |
| ------------------- | ------ | -------------------------------------- | -------------------------------- |
| Code                | string | Success                                | 返回状态码: Success: 成功        |
| Message             | string | null                                   | 返回信息                         |
| Data                | list   | []                                     | 返回数据                         |
| conf_id             | int    | 1069                                   | 方案id                           |
| conf_name           | string | “电信”                                 | 方案名称 电信/联通…              |
| billing_scheme      | list   | []                                     | 计费方案                         |
| goods_id            | Sting  | "16319"                                | 商品id                           |
| billing_method      | string | “0”                                    | 计费方式 0：按需计费 1：包年包月 |
| billing_type        | string | “number”                               | 计费类型                         |
| billing_scheme_id   | string | “8f8527f0-c74b-11eb-b7f6-ea86f8094c7b” | 计费方案id                       |
| billing_scheme_name | string | “VPC公网带宽-固定带宽”                 | 计费方案名字                     |
| billing_cycle_id    | string | “minute”                               | “minute”                         |
| billing_items       | list   | []                                     | 计费项                           |
| key                 | string | “vpc_pubnet”                           | key                              |
| id                  | string | “b76cab5a-c749-11eb-b7f6-ea86f8094c7b” | id                               |
| name                | string | “VPC公网带宽-固定带宽”                 | name                             |

错误码：

| 错误码 | 错误信息           | 描述                        |
| ------ | ------------------ | --------------------------- |
| 10003  | 传入参数不符合要求 | 传入参数不符合要求          |
| 13504  | 获取计费方案失败   | 服务错误查询失败            |
| 10006  | 参数错误           | 参数错误,对应站点信息不存在 |

返回示例

```json
{
    "Code": "Success",
    "Data": [
        {
            "billing_scheme": [
                {
                    "billing_cycle_id": "minute",
                    "billing_items": [
                        {
                            "id": "bd9c7b0a-8a20-11ec-a9e9-dee2642e3814",
                            "key": "Bandwidth",
                            "name": "固定带宽-电信"
                        }
                    ],
                    "billing_method": "0",
                    "billing_scheme_id": "10dc1fe0-8a22-11ec-9537-02f6ca8ca3d2",
                    "billing_scheme_name": "固定带宽EIP电信",
                    "billing_type": "number",
                    "goods_id": "16319"
                }
            ],
            "conf_id": 10289,
            "conf_name": "电信"
        },
        {
            "billing_scheme": [
                {
                    "billing_cycle_id": "minute",
                    "billing_items": [
                        {
                            "id": "9fb925ac-8a20-11ec-a829-dee2642e3814",
                            "key": "Bandwidth",
                            "name": "固定带宽-移动"
                        }
                    ],
                    "billing_method": "0",
                    "billing_scheme_id": "fd81a33e-8a21-11ec-ab1f-dee2642e3814",
                    "billing_scheme_name": "固定带宽EIP移动",
                    "billing_type": "number",
                    "goods_id": "16328"
                }
            ],
            "conf_id": 10298,
            "conf_name": "移动"
        },
        {
            "billing_scheme": [
                {
                    "billing_cycle_id": "minute",
                    "billing_items": [
                        {
                            "id": "8a7cdaf8-8a20-11ec-98fd-dee2642e3814",
                            "key": "Bandwidth",
                            "name": "固定带宽-联通"
                        }
                    ],
                    "billing_method": "0",
                    "billing_scheme_id": "ec0aacae-8a21-11ec-befd-02f6ca8ca3d2",
                    "billing_scheme_name": "固定带宽EIP联通",
                    "billing_type": "number",
                    "goods_id": "16337"
                }
            ],
            "conf_id": 10307,
            "conf_name": "联通"
        }
    ],
    "Message": ""
}

```

代码调用示例

```python

def getLineBillingScheme():
    '''
    获取线路及其计费方案
    :return:
    '''
    action = "GetLineBillingScheme"
    method = "GET"
    param = {"siteId": "32e6fd62-9bac-11ec-875a-2a8d1f4e167e", "requestId": "6ca9ed98-27c8-4431-995f-59cc6d743dab"}
    url = getUrl(action, AK, AccessKeySecret, method, CCS_URL, param=param)
    res = requests.get(url)
    result = json.loads(res.content)
    print(result)
    if result.get("Code") != "Success":
        print ("request error: %s" % result.get("Message"))
    return result

```

# 18. GetEipPrice

Action: GetEipPrice
描述: 获取弹性ip价格
请求地址: [cdsapi.capitalonline.net/gcw](http://cdsapi.capitalonline.net/gcw)
请求方法: Get

请求参数：

| 名称            | 类型   | 是否必须 | 示例                                   | 描述         |
| --------------- | ------ | -------- | -------------------------------------- | ------------ |
| size            | string | 是       | “1”                                    | eip数量(个)  |
| bandwidthConfId | string | 是       | “1069”                                 | 带宽conf_id  |
| siteId          | string | 是       | “35304122-8504-400c-a61c-56ba244c5dda” | 站点id       |
| qos             | string | 是       | “5”                                    | 带宽值(mbps) |
| requestId       | string | 是       | “6ca9ed98-27c8-4431-995f-59cc6d743dab” | 请求标识uuid |

返回数据：

| 名称            | 类型   | 示例                  | 描述                      |
| --------------- | ------ | --------------------- | ------------------------- |
| Code            | string | Success               | 返回状态码: Success: 成功 |
| Message         | string | null                  | 返回信息                  |
| Data            | object | {}                    | 返回数据                  |
| bandwidth_price | object | {}                    | 带宽的价格                |
| eip_price       | object | {}                    | ip的价格                  |
| total_price     | object | {}                    | 总价格                    |
| price           | double | 1.2                   | 价格                      |
| price_str       | string | “1.2”                 | 价格 str                  |
| sign            | string | “￥”                  | 单位                      |
| cycle           | string | “/天”                 | 周期                      |
| end_time        | string | “2099-01-01 00:00:00” | 结束时间                  |

错误码：

| 错误码 | 错误信息           | 描述                    |
| ------ | ------------------ | ----------------------- |
| 10003  | 传入参数不符合要求 | 传入参数不符合要求      |
| 13503  | 获取eip价格失败    | 服务错误查询失败        |
| 10006  | 参数错误           | 参数错误,无对应站点信息 |

返回示例

```json
{
    "Code": "Success",
    "Data": {
        "bandwidth_price": {
            "cycle": "/天",
            "end_time": "2099-01-01 00:00:00",
            "price": 1.5,
            "price_str": "1.50",
            "sign": "￥"
        },
        "eip_price": {
            "cycle": "/天",
            "end_time": "2099-01-01 00:00:00",
            "price": 0.5,
            "price_str": "0.50",
            "sign": "￥"
        },
        "total_price": {
            "cycle": "/天",
            "end_time": "2099-01-01 00:00:00",
            "price": 2.5,
            "price_str": "2.50",
            "sign": "￥"
        }
    },
    "Message": ""
}

```

代码调用示例

```python

def getEipPrice():
    '''
    获取弹性ip价格
    :return:
    '''
    action = "GetEipPrice"
    method = "GET"
    param = {
            "size":"1",
            "siteId": "09a38804-c1ee-11ec-bd22-4641dfd57315",
            "bandwidthConfId":"10289",
            "qos":"5",
            "requestId": "6ca9ed98-27c8-4431-995f-59cc6d743dab"
    }
    url = getUrl(action, AK, AccessKeySecret, method, CCS_URL, param=param)
    res = requests.get(url)
    result = json.loads(res.content)
    print(result)
    if result.get("Code") != "Success":
        print ("request error: %s" % result.get("Message"))
    return result

```



# 19. QueryVms

Action: QueryVms
描述: 查询云桌面集合
请求地址: [cdsapi.capitalonline.net/gcw](http://cdsapi.capitalonline.net/gcw)
请求方法: Get

请求参数：

| 名称       | 类型   | 是否必须 | 示例                                   | 描述                     |
| ---------- | ------ | -------- | -------------------------------------- | ------------------------ |
| siteId     | string | 否       | “32e6fd62-9bac-11ec-875a-2a8d1f4e167e” | 节点id                   |
| productId  | string | 否       | “745f6546-dc5f-492f-82d1-9eb47cd9fa2d” | 规格                     |
| billMethod | string | 否       | “1”                                    | 计费模式 1包年包月 0按需 |
| email      | string | 否       | “cds@[163.com](http://163.com)”        | 用户邮箱                 |
| vpcId      | string | 否       | “b4754c79-93fe-4662-a747-5581d23b8877” | VPC id                   |
| vpcName    | string | 否       | “保定-云桌面默认VPC”                   | VPC name                 |

返回数据：

| 名称  | 类型   | 示例                                     | 描述                      |
| ----- | ------ | ---------------------------------------- | ------------------------- |
| code  | string | Success                                  | 返回状态码: Success: 成功 |
| msg   | string | null                                     | 返回信息                  |
| data  | object | {}                                       | 返回数据                  |
| vmIds | list   | [“a8d09bab-64d4-4549-9c8c-0efe19423e5e”] | 云桌面ids                 |

错误码：

| 错误码 | 错误信息           | 描述                                                         |
| ------ | ------------------ | ------------------------------------------------------------ |
| 10003  | 传入参数不符合要求 | 传入参数不符合要求，计费模式可选值为1或0,1为包年包月,2为按需 |

返回示例

```json

{
    "Code": "Success",
    "Data": {
        "vmIds": [
            "a8d09bab-64d4-4549-9c8c-0efe19423e5e"
        ]
    },
    "Message": ""
}

```

代码调用示例

```python
def queryVms():
    '''
    查询云桌面集合
    :return:
    '''
    action = "QueryVms"
    method = "GET"
    param = {}
    url = getUrl(action, AK, AccessKeySecret, method, CCS_URL, param=param)
    res = requests.get(url)
    result = json.loads(res.content)
    print(result)
    if result.get("Code") != "Success":
        print ("request error: %s" % result.get("Message"))
    return result

```



# 20. QueryVm

Action: QueryVm
描述: 查询云桌面详细信息
请求地址: [cdsapi.capitalonline.net/gcw](http://cdsapi.capitalonline.net/gcw)
请求方法: Get

请求参数：

| 名称 | 类型   | 是否必须 | 示例                                   | 描述     |
| ---- | ------ | -------- | -------------------------------------- | -------- |
| vmId | string | 是       | “a8d09bab-64d4-4549-9c8c-0efe19423e5e” | 云桌面ID |

返回数据：

| 名称         | 类型   | 示例                                   | 描述                                                         |
| ------------ | ------ | -------------------------------------- | ------------------------------------------------------------ |
| code         | string | Success                                | 返回状态码: Success: 成功                                    |
| msg          | string | null                                   | 返回信息                                                     |
| data         | object | {}                                     | 返回数据                                                     |
| vmName       | string | “openapi_test_2”                       | 云桌面的名称                                                 |
| siteId       | string | “ebbfcb70-a98f-11ec-926b-8aaa763f849e” | 区域                                                         |
| billMethod   | int    | 0                                      | 计费类型 1包年包月 0按需                                     |
| productId    | string | “745f6546-dc5f-492f-82d1-9eb47cd9fa2d” | 规格                                                         |
| vpcId        | string | “73cbf764-cdcb-11ec-a318-ee97882ecf7d” | VPC id                                                       |
| vpcName      | string | “娄底-云桌面默认VPC”                   | vpc Name                                                     |
| eip          | string | “移动:120.226.84.70”                   | EIP                                                          |
| privateIp    | string | “vlan1704:10.1.0.14”                   | 子网                                                         |
| publicIp     | string | “745f6546-dc5f-492f-82d1-9eb47cd9fa2d” | 虚拟出网网关                                                 |
| bw           | int    | 5                                      | 带宽                                                         |
| accountName  | string | “”                                     | 所属用户名称                                                 |
| accountEmail | string | “”                                     | 用户邮箱                                                     |
| expireTime   | string | “2098-12-31T16:00:00.000+0000”         | 包月到期时间                                                 |
| status       | string | “using”                                | 状态 : configuring(“配置中”), rebooting(“重启中”), starting(“开机中”), using(“已开机”), stoping(“关机中”), stop(“已关机”), deleteing(“删除中”), deleted(“已删除”),dataMoving(“云桌面迁移中”),error(“错误”),asNeedExpiring(“欠费关机中”),asNeedExpired(“已欠费”),asMonthExpiring(“到期关机中”),asMonthExpired(“已到期”),logicalDeleted(“逻辑删除”),destroying(“欠费到期删除中”),destroy(“欠费到期已删除”),invisibleError(“回收错误”) |

错误码：

| 错误码 | 错误信息           | 描述                       |
| ------ | ------------------ | -------------------------- |
| 10003  | 传入参数不符合要求 | 云桌面id为空               |
| 10006  | 参数错误           | 参数错误，对应云桌面不存在 |

返回示例

```json

{
    "Code": "Success",
    "Data": {
        "accountEmail": "",
        "accountName": "",
        "billMethod": 0,
        "bw": 5,
        "eip": "移动:120.226.84.70",
        "expireTime": "2098-12-31T16:00:00.000+0000",
        "label": "",
        "privateIp": "vlan1704:10.1.0.14",
        "productId": "745f6546-dc5f-492f-82d1-9eb47cd9fa2d",
        "publicIp": "10.3.0.4",
        "siteId": "ebbfcb70-a98f-11ec-926b-8aaa763f849e",
        "status": "using",
        "vmName": "openapi_test_2",
        "vpcId": "73cbf764-cdcb-11ec-a318-ee97882ecf7d",
        "vpcName": "娄底-云桌面默认VPC"
    },
    "Message": ""
}

```

代码调用示例

```python
def queryVm():
    '''
    查询云桌面
    :return:
    '''
    action = "QueryVm"
    method = "GET"
    param = {"vmId": "a8d09bab-64d4-4549-9c8c-0efe19423e5e"}
    url = getUrl(action, AK, AccessKeySecret, method, CCS_URL, param=param)
    res = requests.get(url)
    result = json.loads(res.content)
    print(result)
    if result.get("Code") != "Success":
        print ("request error: %s" % result.get("Message"))
    return result
```



# 21. QueryExpireVms

Action: QueryExpireVms
描述: 查询七天内即将到期与已过期的云桌面信息
请求地址: [cdsapi.capitalonline.net/gcw](http://cdsapi.capitalonline.net/gcw)
请求方法: Get

请求参数：

| 名称 | 类型 | 是否必须 | 示例 | 描述 |
| ---- | ---- | -------- | ---- | ---- |
|      |      |          |      |      |



返回数据：

| **名称**   | **类型** | **示例** | **描述**                  |      |
| ---------- | -------- | -------- | ------------------------- | ---- |
| code       | string   | Success  | 返回状态码: Success: 成功 |      |
| msg        | string   | null     | 返回信息                  |      |
| data       | list     | []       | 返回数据                  |      |
| vmName     | string   | “”       | 云桌面的名称              |      |
| billMethod | int      | “”       | 计费类型                  |      |
| expireTime | string   | “”       | 包月到期时间              |      |
| status     | string   | “”       | 状态                      |      |

错误码：

| 错误码 | 错误信息 | 描述 |
| ------ | -------- | ---- |
|        |          |      |

返回示例

```json

{
    "code": "Success",
    "msg": null,
    "data": []
}
```

代码调用示例

```python

def queryExpireVms():
    '''
    查询到期的云桌面信息
    :return:
    '''
    action = "QueryExpireVms"
    method = "GET"
    param = {}
    url = getUrl(action, AK, AccessKeySecret, method, CCS_URL, param=param)
    res = requests.get(url)
    result = json.loads(res.content)
    print(result)
    if result.get("Code") != "Success":
        print ("request error: %s" % result.get("Message"))
    return result

```

# 22. CreateVm

Action: CreateVm
描述: 创建云桌面实例
请求地址: [cdsapi.capitalonline.net/gcw](http://cdsapi.capitalonline.net/gcw)
请求方法: Post

请求参数：

| 名称           | 类型   | 是否必须 | 示例                                   | 描述                                                         |
| -------------- | ------ | -------- | -------------------------------------- | ------------------------------------------------------------ |
| requestId      | string | 是       | “6ca9ed98-27c8-4431-995f-59cc6d743dab” | 请求uuid                                                     |
| siteId         | string | 是       | “ebbfcb70-a98f-11ec-926b-8aaa763f849e” | 节点ID                                                       |
| productId      | string | 是       | “745f6546-dc5f-492f-82d1-9eb47cd9fa2d” | 规格uuid                                                     |
| name           | string | 是       | “openapi_test_2”                       | GPU工作站名称                                                |
| num            | string | 否       | “1”                                    | 开通数量，默认为1                                            |
| hostNo         | string | 否       | “1”                                    | 开通机器起始编号，需大于0,购买超过一台GPU云桌面时，从第二台起名称后缀将自动添加编号，如名称为“测试”、后续名称为测试_001、测试_002等，默认为1 |
| imageId        | string | 是       | “dcd81283-d2e9-456d-9f03-803b83ecc25a” | 镜像id                                                       |
| moneyType      | string | 否       | “CN”                                   | 子账户-试用金的币种:US(美元)，CN(人民币) 默认人民币：“CN” ,  |
| subAccountId   | string | 否       | “76581”                                | 子账户-试用金id                                              |
| billCycle      | string | 否       | “minute”                               | 费周期 month是按月，minute是按需计费 ， 默认为minute 如果选择按需：minute，则参数duration、isToMonth、isAutoRenewal、priceToMonth无需传如果选择包月：montn，则参数 duration、isToMonth、isAutoRenewal、priceToMonth 选择：1、不传使用默认值：duration=1，isToMonth=0，isAutoRenewal=0，priceToMonth=0表示为：包1个整月 |
| duration       | string | 否       | “1”                                    | 包月周期数，billCtcle的值是mounth时为包月，3个月传3,5个月传5； 按需无需传，默认为1 |
| isToMonth      | string | 否       | “0”                                    | 包月是否到月底 1是到月底，0否， 默认为0如：包月开始时间为 2022.6.22 12:19:08isToMonth为1，duration为1，则包月到2022.7.1 00:00:00isToMonth为0，duration为1，则包整月到2022.7.22 12:19:08isToMonth为1，duration为6，则包整月到2022.12.1 12:19:08 isToMonth为0，duration为6，则包整月到2022.12.22 12:19:08 |
| isAutoRenewal  | string | 否       | “0”                                    | 包月是否续约 1是0否， 默认为0                                |
| priceToMonth   | string | 否       | “0”                                    | 包年包月 不足整月是否按整月收费 1是0否， 默认为0             |
| qos            | string | 是       | “5”                                    | 带宽大小 (mbps)                                              |
| vpcId          | string | 是       | “73cbf764-cdcb-11ec-a318-ee97882ecf7d” | vpc id                                                       |
| subnetNetId    | string | 是       | “73d2c7ec-cdcb-11ec-a318-ee97882ecf7d” | 子网–子网id                                                  |
| vGatewayNetId  | string | 是       | “80587138-cdcb-11ec-a318-ee97882ecf7d” | 虚拟出网网关网关–id                                          |
| vGatewayConfId | string | 是       | “10298”                                | 虚拟网关–conf_id                                             |

返回数据：

| 名称           | 类型   | 示例                                     | 描述                      |
| -------------- | ------ | ---------------------------------------- | ------------------------- |
| code           | string | Success                                  | 返回状态码: Success: 成功 |
| msg            | string | null                                     | 返回信息                  |
| data           | obejct | {}                                       | 返回数据                  |
| taskId         | string | “53b150e2-bb27-4db1-8dc6-650eaba66fc2”   | 任务id                    |
| vmIds          | list   | [“a8d09bab-64d4-4549-9c8c-0efe19423e5e”] | 云桌面ids                 |
| requestId      | string | “6ca9ed98-27c8-4431-995f-59cc6d743dab”   | 请求uuid                  |
| requestContent | string | “”                                       | 请求参数                  |

错误码：

| 错误码 | 错误信息                                                     | 描述                                                         |
| ------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 10007  | 当前账户权限不足                                             | 当前账户权限不足                                             |
| 10005  | 账户数据异常                                                 | 账户数据异常                                                 |
| 10003  | 传入参数不符合要求，请检查后重试                             | 传入参数不符合要求，请检查后重试                             |
| 13001  | GPU云桌面实例创建失败                                        | GPU云桌面实例创建失败                                        |
| 12501  | 当前用户包月购买已达配额上限，请修改计费方式或联系销售人员增加包月配额 | 当前用户包月购买已达配额上限，请修改计费方式或联系销售人员增加包月配额 |
| 12502  | 当前用户按需购买已达配额上限，请修改计费方式或联系销售人员增加按需配额 | 当前用户按需购买已达配额上限，请修改计费方式或联系销售人员增加按需配额 |
| 13505  | 校验网络信息失败                                             | 校验网络信息失败                                             |
| 13000  | 当前资源不足                                                 | 当前资源不足                                                 |
| 10006  | 参数错误                                                     | 参数错误，无对应商品信息                                     |

返回示例

```json

{
    "Code": "Success",
    "Data": {
        "requestContent": "{\"billCycle\":\"minute\",\"billMethod\":0,\"customerId\":\"E2129298\",\"duration\":1,\"funEipParam\":{\"qos\":5,\"siteId\":\"ebbfcb70-a98f-11ec-926b-8aaa763f849e\",\"size\":1,\"subnetNetId\":\"73d2c7ec-cdcb-11ec-a318-ee97882ecf7d\",\"vGatewayConfId\":\"10298\",\"vGatewayConfName\":\"移动\",\"vGatewayNetId\":\"80587138-cdcb-11ec-a318-ee97882ecf7d\",\"vpcId\":\"73cbf764-cdcb-11ec-a318-ee97882ecf7d\",\"vpcName\":\"娄底-云桌面默认VPC\"},\"isAutoRenewal\":0,\"isToMonth\":0,\"name\":\"openapi_test_2\",\"num\":1,\"priceToMonth\":0,\"productId\":\"745f6546-dc5f-492f-82d1-9eb47cd9fa2d\",\"qos\":5,\"requestId\":\"6ca9ed98-27c8-4431-995f-59cc6d743dab\",\"siteId\":\"ebbfcb70-a98f-11ec-926b-8aaa763f849e\",\"subnetNetId\":\"73d2c7ec-cdcb-11ec-a318-ee97882ecf7d\",\"userFrom\":\"cdsapi\",\"userId\":\"713367\",\"vGatewayConfId\":\"10298\",\"vGatewayConfName\":\"移动\",\"vGatewayNetId\":\"80587138-cdcb-11ec-a318-ee97882ecf7d\",\"vpcId\":\"73cbf764-cdcb-11ec-a318-ee97882ecf7d\",\"vpcName\":\"娄底-云桌面默认VPC\"}",
        "requestId": "6ca9ed98-27c8-4431-995f-59cc6d743dab",
        "taskId": "53b150e2-bb27-4db1-8dc6-650eaba66fc2",
        "vmIds": [
            "a8d09bab-64d4-4549-9c8c-0efe19423e5e"
        ]
    },
    "Message": ""
}

```

代码调用示例

```python
def createVm():
    '''
    创建云桌面实例
    :return:
    '''
    action = "CreateVm"
    method = "POST"
    body = {
        "requestId": "6ca9ed98-27c8-4431-995f-59cc6d743dab",
        "siteId": "ebbfcb70-a98f-11ec-926b-8aaa763f849e",
        "productId": "745f6546-dc5f-492f-82d1-9eb47cd9fa2d",
        "imageId": "dcd81283-d2e9-456d-9f03-803b83ecc25a”,
      "name": "openapi_999",
        "num": "1",
        "billCycle": "minute",
        "isToMonth": "0",
        "isAutoRenewal": "0",
        "priceToMonth":"0",
        "qos": "5",
        "vpcId": "b35e43a6-e706-11ec-8171-32f9a7e748fc",
        "subnetNetId": "b36b43a8-e706-11ec-8171-32f9a7e748fc",
        "vgatewayNetId": "c0505a90-e706-11ec-8171-32f9a7e748fc",
        "vgatewayConfId": "10298"
    }
 
 
    url = getUrl(action, AK, AccessKeySecret, method, CCS_URL, param={})
    res = requests.post(url,json=body)
    result = json.loads(res.content)
    print(result)
    if result.get("Code") != "Success":
        print ("request error: %s" % result.get("Message"))
    return result
```



# 23. OperateVm

Action: OperateVm
描述: 云桌面电源操作
请求地址: [cdsapi.capitalonline.net/gcw](http://cdsapi.capitalonline.net/gcw)
请求方法: Post

请求参数：

| 名称      | 类型   | 是否必须 | 示例                                     | 描述                        |
| --------- | ------ | -------- | ---------------------------------------- | --------------------------- |
| requestId | string | 是       | “ebbfcb70-a98f-11ec-926b-8aaa763f849e”   | 请求uuid                    |
| action    | string | 是       | “off”                                    | 操作: “on”, “off”, “reboot” |
| vmIds     | array  | 是       | [“a8d09bab-64d4-4549-9c8c-0efe19423e5e”] | vm Ids                      |

返回数据：

| 名称           | 类型   | 示例                                      | 描述                      |
| -------------- | ------ | ----------------------------------------- | ------------------------- |
| code           | string | Success                                   | 返回状态码: Success: 成功 |
| msg            | string | null                                      | 返回信息                  |
| data           | obejct | {}                                        | 返回数据                  |
| taskId         | string | “10e0284f-6ce5-4cb0-a61e-4858865d9295”    | 任务id                    |
| vmIds          | array  | [ “a8d09bab-64d4-4549-9c8c-0efe19423e5e”] | 云桌面ids                 |
| requestId      | string | “ebbfcb70-a98f-11ec-926b-8aaa763f849e”    | 请求uuid                  |
| requestContent | string | “”                                        | 请求参数                  |

错误码：

| 错误码 | 错误信息                         | 描述                             |
| ------ | -------------------------------- | -------------------------------- |
| 10003  | 传入参数不符合要求，请检查后重试 | 传入参数不符合要求，请检查后重试 |
| 10005  | 账户数据异常                     | 账户数据异常                     |
| 13002  | GPU云桌面执行操作失败            | GPU云桌面执行操作失败            |
| 10006  | 参数错误                         | 参数错误，暂不支持该操作         |

返回示例

```json

{
    "Code": "Success",
    "Data": {
        "requestContent": "{\"action\":\"off\",\"customerId\":\"E2129298\",\"funVmParam\":{\"action\":\"off\",\"instanceIds\":[\"a8d09bab-64d4-4549-9c8c-0efe19423e5e\"]},\"requestId\":\"ebbfcb70-a98f-11ec-926b-8aaa763f849e\",\"userFrom\":\"cdsapi\",\"userId\":\"713367\",\"vmIds\":[\"a8d09bab-64d4-4549-9c8c-0efe19423e5e\"]}",
        "requestId": "ebbfcb70-a98f-11ec-926b-8aaa763f849e",
        "taskId": "10e0284f-6ce5-4cb0-a61e-4858865d9295",
        "vmIds": [
            "a8d09bab-64d4-4549-9c8c-0efe19423e5e"
        ]
    },
    "Message": ""
}

```

代码调用示例

```python
def operateVm():
    '''
    云桌面电源操作
    :return:
    '''
    action = "OperateVm"
    method = "POST"
    body = {
        "vmIds": ["a8d09bab-64d4-4549-9c8c-0efe19423e5e"],
        "action": "off",  #"on", "off", "reboot"
        "requestId": "ebbfcb70-a98f-11ec-926b-8aaa763f849e"
    }
    url = getUrl(action, AK, AccessKeySecret, method, CCS_URL, param={})
    res = requests.post(url,json=body)
    result = json.loads(res.content)
    print(result)
    if result.get("Code") != "Success":
        print ("request error: %s" % result.get("Message"))
    return result

```



# 24. RebuildVm

Action: RebuildVm
描述: 重装云桌面
请求地址: [cdsapi.capitalonline.net/gcw](http://cdsapi.capitalonline.net/gcw)
请求方法: Get

请求参数：

| 名称      | 类型   | 是否必须 | 示例                                   | 描述     |
| --------- | ------ | -------- | -------------------------------------- | -------- |
| requestId | string | 是       | “6ca9ed98-27c8-4431-995f-59cc6d743dab” | 请求uuid |
| vmId      | string | 是       | “a8d09bab-64d4-4549-9c8c-0efe19423e5e” | vm Id    |
| imageId   | string | 是       | "dcd81283-d2e9-456d-9f03-803b83ecc25a" | 镜像id   |

返回数据：

| 名称           | 类型   | 示例                                   | 描述                      |
| -------------- | ------ | -------------------------------------- | ------------------------- |
| code           | string | Success                                | 返回状态码: Success: 成功 |
| msg            | string | null                                   | 返回信息                  |
| data           | obejct | {}                                     | 返回数据                  |
| taskId         | string | “0b4b8f52-def3-466f-ac37-d1069590cbe9” | 任务id                    |
| vmId           | string | “a8d09bab-64d4-4549-9c8c-0efe19423e5e” | 云桌面id                  |
| requestId      | string | “6ca9ed98-27c8-4431-995f-59cc6d743dab” | 请求uuid                  |
| requestContent | string | “”                                     | 请求参数                  |

错误码：

| 错误码 | 错误信息                                         | 描述                                             |
| ------ | ------------------------------------------------ | ------------------------------------------------ |
| 10007  | 当前账户权限不足                                 | 当前账户权限不足                                 |
| 10005  | 账户数据异常                                     | 账户数据异常                                     |
| 13004  | 当前状态无法重装，仅支持关机状态的云桌面进行重装 | 当前状态无法重装，仅支持关机状态的云桌面进行重装 |
| 10003  | 传入参数不符合要求                               | 传入参数不符合要求                               |
| 13002  | GPU云桌面执行操作失败                            | GPU云桌面执行操作失败                            |
| 10006  | 参数错误                                         | 参数错误,无对应云桌面信息                        |
| 10008  | 系统内数据错误                                   | 系统内数据错误,商品信息查询失败                  |

返回示例

```json
{
    "Code": "Success",
    "Data": {
        "requestContent": "vmId=a8d09bab-64d4-4549-9c8c-0efe19423e5e",
        "requestId": "6ca9ed98-27c8-4431-995f-59cc6d743dab",
        "taskId": "0b4b8f52-def3-466f-ac37-d1069590cbe9",
        "vmId": "a8d09bab-64d4-4549-9c8c-0efe19423e5e"
    },
    "Message": ""
}

```

代码调用示例

```python
def rebuildVm():
    '''
    重装云桌面
    :return:
    '''
    action = "RebuildVm"
    method = "GET"
    param = {"vmId": "a8d09bab-64d4-4549-9c8c-0efe19423e5e","imageId": "dcd81283-d2e9-456d-9f03-803b83ecc25a","requestId": "6ca9ed98-27c8-4431-995f-59cc6d743dab"}
    url = getUrl(action, AK, AccessKeySecret, method, CCS_URL, param=param)
    res = requests.get(url)
    result = json.loads(res.content)
    print(result)
    if result.get("Code") != "Success":
        print ("request error: %s" % result.get("Message"))
    return result

```

# 25. DeleteVm

Action: DeleteVm
描述: 删除云桌面
请求地址: [cdsapi.capitalonline.net/gcw](http://cdsapi.capitalonline.net/gcw)
请求方法: Post

请求参数：

| 名称      | 类型   | 是否必须 | 示例                                   | 描述     |
| --------- | ------ | -------- | -------------------------------------- | -------- |
| requestId | string | 是       | “ebbfcb70-a98f-11ec-926b-8aaa763f849e” | 请求uuid |
| vmId      | string | 是       | “a8d09bab-64d4-4549-9c8c-0efe19423e5e” | vm Id    |

返回数据：

| 名称           | 类型   | 示例                                   | 描述                      |
| -------------- | ------ | -------------------------------------- | ------------------------- |
| code           | string | Success                                | 返回状态码: Success: 成功 |
| msg            | string | null                                   | 返回信息                  |
| data           | obejct | {}                                     | 返回数据                  |
| taskId         | string | “8eb19f5b-fd44-4225-94f5-0f9e39e56695” | 任务id                    |
| vmId           | string | “a8d09bab-64d4-4549-9c8c-0efe19423e5e” | 云桌面id                  |
| requestId      | string | “ebbfcb70-a98f-11ec-926b-8aaa763f849e” | 请求uuid                  |
| requestContent | string | “”                                     | 请求参数                  |

错误码：

| 错误码 | 错误信息              | 描述                  |
| ------ | --------------------- | --------------------- |
| 10003  | 传入参数不符合要求    | 传入参数不符合要求    |
| 10007  | 当前账户权限不足      | 当前账户权限不足      |
| 10005  | 账户数据异常          | 账户数据异常          |
| 13002  | GPU云桌面执行操作失败 | GPU云桌面执行操作失败 |
| 10006  | 参数错误              | 参数错误,云桌面不存在 |

返回示例

```json
{
    "Code": "Success",
    "Data": {
        "requestContent": "{\"customerId\":\"E2129298\",\"funVmParam\":{\"instanceIds\":[\"a8d09bab-64d4-4549-9c8c-0efe19423e5e\"]},\"requestId\":\"ebbfcb70-a98f-11ec-926b-8aaa763f849e\",\"userFrom\":\"cdsapi\",\"userId\":\"713367\",\"vmId\":\"a8d09bab-64d4-4549-9c8c-0efe19423e5e\"}",
        "requestId": "ebbfcb70-a98f-11ec-926b-8aaa763f849e",
        "taskId": "8eb19f5b-fd44-4225-94f5-0f9e39e56695",
        "vmId": "a8d09bab-64d4-4549-9c8c-0efe19423e5e"
    },
    "Message": ""
}

```

代码调用示例

```python
def deleteVm():
    '''
    删除云桌面
    :return:
    '''
    action = "DeleteVm"
    method = "POST"
    body = {
        "vmId": "a8d09bab-64d4-4549-9c8c-0efe19423e5e",
        "requestId": "ebbfcb70-a98f-11ec-926b-8aaa763f849e"
    }
    url = getUrl(action, AK, AccessKeySecret, method, CCS_URL, param={})
    res = requests.post(url,json=body)
    result = json.loads(res.content)
    print(result)
    if result.get("Code") != "Success":
        print ("request error: %s" % result.get("Message"))
    return result

```

# 26. ChangeVmName

Action: ChangeVmName
描述: 修改云桌面名称
请求地址: [cdsapi.capitalonline.net/gcw](http://cdsapi.capitalonline.net/gcw)
请求方法: Post

请求参数：

| 名称      | 类型   | 是否必须 | 示例                                   | 描述     |
| --------- | ------ | -------- | -------------------------------------- | -------- |
| requestId | string | 是       | “ebbfcb70-a98f-11ec-926b-8aaa763f849e” | 请求uuid |
| vmId      | string | 是       | “1f08cc62-c24b-46dd-b190-bf139d00ee82” | vm Id    |
| name      | string | 是       | “openapi_改名”                         | vm name  |

返回数据：

| 名称 | 类型   | 示例    | 描述                      |
| ---- | ------ | ------- | ------------------------- |
| code | string | Success | 返回状态码: Success: 成功 |
| msg  | string | null    | 返回信息                  |
| data | obejct | {}      | 返回数据                  |

错误码：

| 错误码 | 错误信息           | 描述                  |
| ------ | ------------------ | --------------------- |
| 10003  | 传入参数不符合要求 | 传入参数不符合要求    |
| 10006  | 参数错误           | 参数错误,云桌面不存在 |

返回示例

```json

{
    "Code": "Success",
    "Data": null,
    "Message": ""
}

```

代码调用示例

```python
def changeVmName():
    '''
    修改云桌面名称
    :return:
    '''
    action = "ChangeVmName"
    method = "POST"
    body = {
        "vmId": "1f08cc62-c24b-46dd-b190-bf139d00ee82",
        "requestId": "ebbfcb70-a98f-11ec-926b-8aaa763f849e",
        "name": "openapi_改名"
    }
    url = getUrl(action, AK, AccessKeySecret, method, CCS_URL, param={})
    res = requests.post(url,json=body)
    result = json.loads(res.content)
    print(result)
    if result.get("Code") != "Success":
        print ("request error: %s" % result.get("Message"))
    return result

```

# 27. UpdateVmLabels

Action: UpdateVmLabels
描述: 修改云桌面备注（批量）
请求地址: [cdsapi.capitalonline.net/gcw](http://cdsapi.capitalonline.net/gcw)
请求方法: Post

请求参数：

| 名称      | 类型   | 是否必须 | 示例                                     | 描述     |
| --------- | ------ | -------- | ---------------------------------------- | -------- |
| requestId | string | 是       | “ebbfcb70-a98f-11ec-926b-8aaa763f849e”   | 请求uuid |
| vmIds     | array  | 是       | [“1f08cc62-c24b-46dd-b190-bf139d00ee82”] | vm Ids   |
| label     | string | 是       | “备注”                                   | 备注     |

返回数据：

| 名称 | 类型   | 示例    | 描述                      |
| ---- | ------ | ------- | ------------------------- |
| code | string | Success | 返回状态码: Success: 成功 |
| msg  | string | null    | 返回信息                  |
| data | obejct | {}      | 返回数据                  |

错误码：

| 错误码 | 错误信息           | 描述               |
| ------ | ------------------ | ------------------ |
| 10003  | 传入参数不符合要求 | 传入参数不符合要求 |
| 13015  | 更新云桌面备注失败 | 更新云桌面备注失败 |

返回示例

```json
{
    "Code": "Success",
    "Data": null,
    "Message": ""
}

```

代码调用示例

```python
def updateVmLabels():
    '''
    修改云桌面备注（批量）
    :return:
    '''
    action = "UpdateVmLabels"
    method = "POST"
    body = {
        "vmIds": ["1f08cc62-c24b-46dd-b190-bf139d00ee82"],
        "requestId": "ebbfcb70-a98f-11ec-926b-8aaa763f849e",
        "label": "备注"
    }
    url = getUrl(action, AK, AccessKeySecret, method, CCS_URL, param={})
    res = requests.post(url,json=body)
    result = json.loads(res.content)
    print(result)
    if result.get("Code") != "Success":
        print ("request error: %s" % result.get("Message"))
    return result

```

# 28. ChangeAccount

Action: ChangeAccount
描述: 实例修改绑定账户
请求地址: [cdsapi.capitalonline.net/gcw](http://cdsapi.capitalonline.net/gcw)
请求方法: Post

请求参数：

| 名称      | 类型   | 是否必须 | 示例                                   | 描述         |
| --------- | ------ | -------- | -------------------------------------- | ------------ |
| requestId | string | 是       | “ebbfcb70-a98f-11ec-926b-8aaa763f849e” | 请求uuid     |
| vmId      | string | 是       | “1f08cc62-c24b-46dd-b190-bf139d00ee82” | vm Id        |
| accountId | string | 是       | “9294858a-3948-4ece-8378-f31daf6bff0b” | vm accountId |

返回数据：

| 名称 | 类型   | 示例    | 描述                      |
| ---- | ------ | ------- | ------------------------- |
| code | string | Success | 返回状态码: Success: 成功 |
| msg  | string | null    | 返回信息                  |
| data | obejct | {}      | 返回数据                  |

错误码：

| 错误码 | 错误信息              | 描述                                                         |
| ------ | --------------------- | ------------------------------------------------------------ |
| 10003  | 传入参数不符合要求    | 传入参数不符合要求                                           |
| 13011  | 换绑GPU云桌面实例失败 | 对没有绑定用户的云桌面在已开机和已关机的状态下都可以绑定用户，对于已经绑定用户的云桌面仅在已关机的状态下可以换绑用户 |

返回示例

```json
{
    "Code": "Success",
    "Data": null,
    "Message": ""
}

```

代码调用示例

```python
def changeAccount():
    '''
    实例修改绑定账户
    :return:
    '''
    action = "ChangeAccount"
    method = "POST"
    body = {
        "vmId": "1f08cc62-c24b-46dd-b190-bf139d00ee82",
        "requestId": "ebbfcb70-a98f-11ec-926b-8aaa763f849e",
        "accountId": "9294858a-3948-4ece-8378-f31daf6bff0b"
    }
    url = getUrl(action, AK, AccessKeySecret, method, CCS_URL, param={})
    res = requests.post(url,json=body)
    result = json.loads(res.content)
    print(result)
    if result.get("Code") != "Success":
        print ("request error: %s" % result.get("Message"))
    return result

```

# 29. UnbindAccounts

Action: UnbindAccounts
描述: 实例解绑账户（批量）
请求地址: [cdsapi.capitalonline.net/gcw](http://cdsapi.capitalonline.net/gcw)
请求方法: Post

请求参数：

| 名称      | 类型   | 是否必须 | 示例                                     | 描述     |
| --------- | ------ | -------- | ---------------------------------------- | -------- |
| requestId | string | 是       | “ebbfcb70-a98f-11ec-926b-8aaa763f849e”   | 请求uuid |
| vmIds     | array  | 是       | [“1f08cc62-c24b-46dd-b190-bf139d00ee82”] | vm Ids   |

返回数据：

| 名称 | 类型   | 示例    | 描述                      |
| ---- | ------ | ------- | ------------------------- |
| code | string | Success | 返回状态码: Success: 成功 |
| msg  | string | null    | 返回信息                  |
| data | obejct | {}      | 返回数据                  |

错误码：

| 错误码 | 错误信息              | 描述                                     |
| ------ | --------------------- | ---------------------------------------- |
| 10003  | 传入参数不符合要求    | 传入参数不符合要求                       |
| 13012  | 解绑GPU云桌面实例失败 | 仅支持已关机状态的云桌面执行解绑用户操作 |

返回示例

```json
{
    "Code": "Success",
    "Data": null,
    "Message": ""
}

```

代码调用示例

```python
def unbindAccounts():
    '''
    实例解绑账户（批量）
    :return:
    '''
    action = "UnbindAccounts"
    method = "POST"
    body = {
        "vmIds": ["1f08cc62-c24b-46dd-b190-bf139d00ee82"],
        "requestId": "ebbfcb70-a98f-11ec-926b-8aaa763f849e"
    }
    url = getUrl(action, AK, AccessKeySecret, method, CCS_URL, param={})
    res = requests.post(url,json=body)
    result = json.loads(res.content)
    print(result)
    if result.get("Code") != "Success":
        print ("request error: %s" % result.get("Message"))
    return result

```

# 30. BindAccounts

Action: BindAccounts
描述: 实例绑定账户（批量）
请求地址: [cdsapi.capitalonline.net/gcw](http://cdsapi.capitalonline.net/gcw)
请求方法: Post

请求参数：

| 名称      | 类型   | 是否必须 | 示例                                     | 描述         |
| --------- | ------ | -------- | ---------------------------------------- | ------------ |
| requestId | string | 是       | “ebbfcb70-a98f-11ec-926b-8aaa763f849e”   | 请求uuid     |
| vmIds     | array  | 是       | [“1f08cc62-c24b-46dd-b190-bf139d00ee82”] | vm Ids       |
| accountId | string | 是       | “9294858a-3948-4ece-8378-f31daf6bff0b”   | vm accountId |

返回数据：

| 名称 | 类型   | 示例    | 描述                      |
| ---- | ------ | ------- | ------------------------- |
| code | string | Success | 返回状态码: Success: 成功 |
| msg  | string | null    | 返回信息                  |
| data | obejct | {}      | 返回数据                  |

错误码：

| 错误码 | 错误信息              | 描述                  |
| ------ | --------------------- | --------------------- |
| 10003  | 传入参数不符合要求    | 传入参数不符合要求    |
| 13013  | 绑定GPU云桌面实例失败 | 绑定GPU云桌面实例失败 |

返回示例

```json
{
    "Code": "Success",
    "Data": null,
    "Message": ""
}

```

代码调用示例

```python
def bindAccounts():
    '''
    实例绑定账户（批量）
    :return:
    '''
    action = "BindAccounts"
    method = "POST"
    body = {
        "vmIds": ["1f08cc62-c24b-46dd-b190-bf139d00ee82"],
        "requestId": "ebbfcb70-a98f-11ec-926b-8aaa763f849e",
        "accountId": "9294858a-3948-4ece-8378-f31daf6bff0b"
    }
    url = getUrl(action, AK, AccessKeySecret, method, CCS_URL, param={})
    res = requests.post(url,json=body)
    result = json.loads(res.content)
    print(result)
    if result.get("Code") != "Success":
        print ("request error: %s" % result.get("Message"))
    return result

```

