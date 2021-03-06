>? **当前页面接口为旧版 API，未来可能停止维护，目前不展示在左侧导航。黑石物理服务器1.0 API 3.0 版本接口定义更加规范，访问时延下降显著，建议使用 <a href="https://cloud.tencent.com/document/api/386/18637" target="_blank">黑石物理服务器1.0 API 3.0</a>。**
>

## 功能描述
EipBmUnbindRs 接口用于解绑黑石物理服务器上的弹性公网EIP。需注意的是，解绑成功后的EIP会处于闲置状态，该状态下的EIP会收取闲置费，请及时[释放清理](/document/product/386/6676)。
 
接口访问域名: bmeip.api.qcloud.com

 

## 请求
### 请求示例
```
GET https://bmeip.api.qcloud.com/v2/index.php?
	Action=EipBmUnbindRs
	&<公共请求参数>
	&eipId=<EIP实例ID>
	&instanceId=<黑石物理服务器实例ID>
```

### 请求参数

以下请求参数列表仅列出了接口请求参数，正式调用时需要加上公共请求参数，见[公共请求参数页面](/document/product/386/6718)。其中，此接口的Action字段为 EipBmUnbindRs。

|参数名称|必选|类型|描述|
|-------|----|---|----|
| eipId | 否 | String | EIP实例ID |
| instanceId | 否 | String | 黑石物理服务器实例ID，可通过[查询服务器](/document/product/386/6728)接口返回字段中的instanceId获取|


## 响应
### 响应示例
```
{
    "code": 0,
    "message": "",
    "codeDesc": "Success",
    "data": {
        "requestId": "<异步任务ID>"
    }
}
```
### 响应参数

响应参数部分包含两层结构，外层展示接口的响应结果，内层展示具体的接口内容，主要包括解绑操作的异步任务ID。

| 参数名称 | 类型 | 描述 |
|---------|---------|---------|
| code |  Int | 错误码, 0: 成功, 其他值: 失败，具体含义可以参考[错误码](/document/product/386/6725)。 |
| message |   String | 错误信息 |
| data |   Array | 返回异步任务信息，具体结构描述如下 |

Data结构

|参数名称|类型|描述|
|---|---|---|
| data.requestId | Int | 解绑操作的异步任务ID，可以通过[查询EIP任务状态](/document/product/386/6670)查询任务状态|

## 错误码
|错误代码|英文提示|错误描述|
|---|---|---|
|9003|ParamInvalid|请求参数不正确|
|9006|InternalErr|内部数据操作异常|
|9032|InternalCgwErr|内部接口错误|
|30009|EipNotExist|操作的EIP记录不存在|
|30010|EipStateCannotOp|EIP当前状态不允许解绑|

## 实际案例
 
### 输入
```
GET https://bmeip.api.qcloud.com/v2/index.php?
	Action=EipBmUnbindRs
	&SecretId=AKIDlfdHxN0ntSVt4KPH0xXWnGl21UUFNoO5
	&Nonce=15988
	&Timestamp=1507792595
	&Region=bj
	&eipId=eip-e791epal
	&instanceId=cpm-pale791e
	&Signature=WR%2FKxls%2Fht5EtGPzvVkdhTM8Tms%3D
```

### 输出
```
{
    "code": 0,
    "message": "",
    "codeDesc": "Success",
    "data": {
        "requestId": 100000
    }
}
```

