## 背景需求

    aws的API Gateway中的websocket服务直接和手机端app通信，本地模拟手机端监听websocket通道，进行websocket消息的收发，主要使用事件循环监听通道，接受所需要的消息信息。

## 代码样例

```python
import asyncio
import websockets
import json


async def send_polling_list():
    async with websockets.connect("wss://3w6vr0g2le.execute-api.ap-southeast-1.amazonaws.com/leeyydev1") as conn:
        polling_list_data = {
            "action": "set_notify_list",
            "devices": [
                {
                    "deviceId": "LEYYTEST01",
                    "list": [
                        "iu_onoff",
                        "iu_set_tmp"
                    ]
                },
                {
                    "deviceId": "LEYYTEST02",
                    # "list": [
                    #     "iu_onoff",
                    #     "iu_hmd"
                    # ]
                }
            ]
        }
        result = await conn.send(json.dumps(polling_list_data))
        print("send result: %s " % result)
        while True:
            recv = await conn.recv()
            print("recv result %s" % recv)

if __name__ == "__main__":
    loop = asyncio.get_event_loop()
    loop.run_until_complete(send_polling_list())
 

```
