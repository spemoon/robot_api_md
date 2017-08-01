## 接口说明

### 创建微信机器人
- HTTP请求方式: POST
- 请求地址: **/app_message**
- 请求JSON格式参数:
```json
    {
        "item_ids": "string, 商品id, 多个商品id用逗号隔开",
        "pics":"string, 图片, 多个图片用逗号隔开",
        "group_text": "string, 群文本",
        "circle_text": "string, 朋友圈文本",
        "content_type": "int, 内容类型, 1:9个商品带9个 id  2、1个商品，多图",
        "send_type": "int, 发送类型, 0：发群 1：发朋友圈 2：两个都发"
    }
```
- 示例：
```json
    {
        "data": {
            "item_ids": "551791620448,540948528503,551597829741,549271457308,552249320835,548539417507,539186916594,552863855893,547643217146",
            "pics": "//img.alicdn.com/bao/uploaded/i4/TB1dcNJRFXXXXX8apXXXXXXXXXX_!!0-item_pic.jpg,//img.alicdn.com/bao/uploaded/i4/TB1ZqlXRFXXXXcPXXXXXXXXXXXX_!!0-item_pic.jpg,//img.alicdn.com/bao/uploaded/i4/TB1ZqlXRFXXXXcPXXXXXXXXXXXX_!!0-item_pic.jpg,//img.alicdn.com/bao/uploaded/i4/TB1ZqlXRFXXXXcPXXXXXXXXXXXX_!!0-item_pic.jpg,//img.alicdn.com/bao/uploaded/i4/TB1ZqlXRFXXXXcPXXXXXXXXXXXX_!!0-item_pic.jpg,//img.alicdn.com/bao/uploaded/i4/TB1ZqlXRFXXXXcPXXXXXXXXXXXX_!!0-item_pic.jpg,//img.alicdn.com/bao/uploaded/i4/TB1ZqlXRFXXXXcPXXXXXXXXXXXX_!!0-item_pic.jpg,//img.alicdn.com/bao/uploaded/i4/TB1ZqlXRFXXXXcPXXXXXXXXXXXX_!!0-item_pic.jpg,//img.alicdn.com/bao/uploaded/i4/TB1ZqlXRFXXXXcPXXXXXXXXXXXX_!!0-item_pic.jpg",
            "group_text":"群文本",
            "circle_text": "朋友圈文本",
            "content_type": 1,
            "send_type": 0
        }
    }
```
- 成功响应:
```json
    {}
```