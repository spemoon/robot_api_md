## 接口说明

### 创建微信机器人
- HTTP请求方式: POST
- 请求地址: **/robots**
- 请求JSON格式参数:
```json
    {
        "token": "string, 访问令牌，由平台分配",
        "username":"string, 微信号"
    }
```
- 成功响应:
```json
    {
        "retCode": "int, 错误码，0代表成功，其它代表错误",
        "errorMsg": "string, 错误描述"
        "data": {
            "robot": {
                "id": "string, 机器人唯一标识",
                "status": "string, 状态",
                "username": "string, 微信号",
                "nickname": "string, 微信昵称"
            }
        }
    }
```

### 查询机器人状态
- HTTP请求方式: GET
- 请求地址: **/robots/<string:robot_id>**
- 请求URL参数:
    - token: "string, 访问令牌，由平台分配"
- 成功响应:
```json
    {
        "retCode": "int, 错误码，0代表成功，其它代表错误",
        "errorMsg": "string, 错误描述"
        "data": {
            "robot": {
                "id": "string, 机器人唯一标识",
                "status": "string, 状态",
                "username": "string, 微信号",
                "nickname": "string, 微信昵称"
            }
        }
    }
```

### 删除机器人
- HTTP请求方式: DELETE
- 请求地址: **/robots/<string:robot_id>**
- 请求URL参数:
    - token: "string, 访问令牌，由平台分配"
- 成功响应:
```json
    {
        "retCode": "int, 错误码，0代表成功，其它代表错误",
        "errorMsg": "string, 错误描述"
        "data": {
            "robot": {
                "id": "string, 机器人唯一标识",
                "status": "string, 状态",
                "username": "string, 微信号",
                "nickname": "string, 微信昵称"
            }
        }
    }
```

### 微信登录
- HTTP请求方式: POST
- 请求地址: **/robots/<string:robot_id>/login**
- 请求JSON格式参数:
```json
    {
        "token": "string, 访问令牌，由平台分配",
        "callback_url": "string, 登录回调url，微信二维码登录成功发送GET通知这个url",
        "agent_id": "string, 代理号, 用于绑定群名称后6位"
    }
```
- 成功响应:
```json
    {
        "retCode": "int, 错误码，0代表成功，其它代表错误",
        "errorMsg": "string, 错误描述"
        "data": {
            "robot": {
                "id": "string, 机器人唯一标识",
                "status": "string, 状态",
                "username": "string, 微信号",
                "nickname": "string, 微信昵称"
            },
            "qrcode_url": "string, 微信登录二维码链接"
        }
    }
```

### 同步微信群列表
- HTTP请求方式: POST
- 请求地址: **/robots/<string:robot_id>/rooms/sync**
- 请求JSON格式参数:
```json
    {
        "token": "string, 访问令牌，由平台分配"
    }
```
- 成功响应:
```json
    {
        "retCode": "int, 错误码，0代表成功，其它代表错误",
        "errorMsg": "string, 错误描述"
        "data": {
            "rooms": [
                {
                    "id": "string, 微信群唯一标识",
                    "nickname": "string, 微信群备注"
                },
                ...
            ]
        }
    }
```

### 获取微信群列表
- HTTP请求方式: GET
- 请求地址: **/robots/<string:robot_id>/rooms**
- 请求URL参数:
    - token: "string, 访问令牌，由平台分配"
- 成功响应:
```json
    {
        "retCode": "int, 错误码，0代表成功，其它代表错误",
        "errorMsg": "string, 错误描述"
        "data": {
            "rooms": [
                {
                    "id": "string, 微信群唯一标识",
                    "nickname": "string, 微信群备注"
                },
                ...
            ]
        }
    }
```

### 发送消息
- HTTP请求方式: POST
- 请求地址: **/robots/<string:robot_id>/message**
- 请求JSON格式参数:
```json
    {
        "token": "string, 访问令牌，由平台分配",
        "to_user":"string, 微信群标识, 支持原来room_id和username",
        "msg_type": "string, 类型，text代表文本，image代表图片",
        "content": "string, 消息内容，如果msg_type是image类型，请放图片链接"
    }
```
- 成功响应:
```json
    {
        "retCode": "int, 错误码，0代表成功，其它代表错误",
        "errorMsg": "string, 错误描述"
    }
```

### 退出登录
- HTTP请求方式: POST
- 请求地址: **/robots/<string:robot_id>/logout**
- 请求JSON格式参数:
```json
    {
        "token": "string, 访问令牌，由平台分配"
    }
```
- 成功响应:
```json
    {
        "retCode": "int, 错误码，0代表成功，其它代表错误",
        "errorMsg": "string, 错误描述"
    }
```

### 获取绑定微信群列表
- HTTP请求方式: GET
- 请求地址: **/robots/<string:robot_id>/rooms/active**
- 请求URL参数:
    - token: "string, 访问令牌，由平台分配"
- 成功响应:
```json
    {
        "retCode": "int, 错误码，0代表成功，其它代表错误",
        "errorMsg": "string, 错误描述"
        "data": {
            "rooms": [
                {
                    "username": "string, 微信群标识，以@@开头",
                    "nickname": "string, 微信群备注"
                },
                ...
            ]
        }
    }
```

## 接口回调
### 通知开发者
- HTTP请求方式: POST
- 请求地址: **接口URL，由开发者提供**
- 请求JSON格式参数:
```json
    {
        "token": "string, 访问令牌，由平台分配",
        "action": "send_message",
        "data": {
            "content": "string, 消息内容",
            "robot_id": "string, 机器人ID",
            "room_id": "string, 群ID",
            "nickname": "string, 昵称"
        }
    }
```
- 成功响应:
```json
    {
        "retCode": "int, 错误码，0代表成功，其它代表错误",
        "errorMsg": "string, 错误描述"
    }
```

## 错误码
- 2000：应用不存在
- 1205：图片发送太频繁，被限制发送
- 1102：微信已经退出登录
- 1: 请求接口失败
- -1: 消息发送失败
- -1000: 返回值不带BaseResponse,
- -1001：微信群不存在
- -1002：文件位置错误
- -1003：服务器拒绝连接
- -1004: 服务器返回异常值
- -1005: 参数错误
- -1006: 无效操作

