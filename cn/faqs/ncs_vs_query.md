
---
title: 消息通知服务和 query 方法的对比
description: 1
platform: All Platforms
updatedAt: Mon Aug 17 2020 22:24:20 GMT+0800 (CST)
---
# 消息通知服务和 query 方法的对比
你可以通过云端录制的 `query` 方法或消息通知服务来监视云端录制服务的状态，在状态异常时及时采取措施，以保证服务可用性。两种方法各有优劣：

## 云端录制 `query` 方法

你可以定时调用云端录制的 `query` 方法，查询云端录制的状态。详见[查询云端录制状态的 API](https://docs.agora.io/cn/cloud-recording/cloud_recording_api_rest?platform=All%20Platforms#a-namequerya查询云端录制状态的-api)。

- 优点：录制服务状态为主动查询后获得，可靠性高。
- 缺点：
  - 提供的状态信息有限。
  - 需要主动查询，且有 QPS 限制，实时性不如消息通知服务。

如果你对状态查询的可靠性要求较高，Agora 强烈建议你使用 `query` 方法。

## 消息通知服务

Agora 消息通知服务用于监听云端录制的重要事件。你需要配置一个 HTTP/HTTPS 服务器来接收事件通知。详见[云端录制 RESTful API 回调服务](https://docs.agora.io/cn/cloud-recording/cloud_recording_callback_rest)。

- 优点：实时性好。
- 缺点：服务器被动接收消息，可能会出现消息丢失的情况。

如果你的业务对消息通知服务强依赖，建议联系 [support@agora.io](mailto:support@agora.io) 开通冗余消息功能，即接收双路消息通知，降低消息丢失的概率。开通冗余消息功能后，你需要对接收到的消息进行去重。
