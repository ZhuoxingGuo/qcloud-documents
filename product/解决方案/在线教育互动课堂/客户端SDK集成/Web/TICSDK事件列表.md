该文档主要列举 TICSDK 中的事件名称和事件产生时机，请在阅读该文章之前阅读 [TICSDK 文档](/document/product/680/17887)。


## TICKSDK 监听方法

ticsdk.on('事件名'，回调函数);

```
var ticsdk = new TICSDK();
ticSdk.on(TICSDK.CONSTANT.EVENT.IM.LOGIN_SUCC, res => {
});
```

## 事件类型分类

TICSDK 中存在以下几种类型：

#### 课堂（TIC）类：

| 事件名 | 描述
| --------- | --------- 
| TICSDK.CONSTANT.EVENT.TIC.ROOMID_NOT_FOUND | 创建课堂的时候，没有传房间号 
| TICSDK.CONSTANT.EVENT.TIC.ROOMID_NOT_MATCH | 房间号不匹配(老师创建的房间和要进入的房间) 
| TICSDK.CONSTANT.EVENT.TIC.CREATE_CLASS_ROOM_ERROR | 创建课堂失败 
| TICSDK.CONSTANT.EVENT.TIC.JOIN_CLASS_ROOM_ERROR | 加入课堂失败 
| TICSDK.CONSTANT.EVENT.TIC.QUIT_CLASS_ROOM_ERROR | 退出课堂失败 
| TICSDK.CONSTANT.EVENT.TIC.DESTROY_CLASS_ROOM_ERROR | 销毁课堂失败 
| TICSDK.CONSTANT.EVENT.TIC.CREATE_CLASS_ROOM_SUCC | 创建课堂成功 
| TICSDK.CONSTANT.EVENT.TIC.JOIN_CLASS_ROOM_SUCC | 加入课堂成功 
| TICSDK.CONSTANT.EVENT.TIC.QUIT_CLASS_ROOM_SUCC | 退出课堂成功 
| TICSDK.CONSTANT.EVENT.TIC.DESTROY_CLASS_ROOM_SUCC | 销毁课堂成功 


#### WebRTC 类：

| 事件名 | 描述
| --------- | ---------
| TICSDK.CONSTANT.EVENT.WEBRTC.INIT_ERROR| 初始化错误
| TICSDK.CONSTANT.EVENT.WEBRTC.INIT_SUCC| 初始化成功
| TICSDK.CONSTANT.EVENT.WEBRTC.LOCAL_STREAM_ADD | 本地视频流新增/更新
| TICSDK.CONSTANT.EVENT.WEBRTC.REMOTE_STREAM_UPDATE | 远端视频流新增/更新
| TICSDK.CONSTANT.EVENT.WEBRTC.REMOTE_STREAM_REMOVE | 远端视频流断开
| TICSDK.CONSTANT.EVENT.WEBRTC.WEBSOCKET_CLOSE | WebSocket 断开
| TICSDK.CONSTANT.EVENT.WEBRTC.RELAY_TIME_OUT | 视频流 server 超时断开
| TICSDK.CONSTANT.EVENT.WEBRTC.KICK_OUT | 被踢下线（同一个用户重复登录）
| TICSDK.CONSTANT.EVENT.WEBRTC.ERROR_NOTIFY | 错误事件通知
| TICSDK.CONSTANT.EVENT.WEBRTC.PEER_CONNECTION_ADD | PeerConnection 连接通知
| TICSDK.CONSTANT.EVENT.WEBRTC.WEBSOCKET_NOTIFY | WebSocket 事件通知
| TICSDK.CONSTANT.EVENT.WEBRTC.STREAM_NOTIFY | 视频流事件通知


#### IM 类：

| 事件名 | 描述 |
|--------- | ---------|
| TICSDK.CONSTANT.EVENT.IM.LOGIN_ERROR | 登录错误 |
| TICSDK.CONSTANT.EVENT.IM.JOIN_CHATROOM_FAIL | 加入 IM 群组成功 |
| TICSDK.CONSTANT.EVENT.IM.LOGOUT_ERROR | IM 退出异常 |
| TICSDK.CONSTANT.EVENT.IM.LOGIN_SUCC | 登录成功 |
| TICSDK.CONSTANT.EVENT.IM.CONNECTION_EVENT | 用于监听用户连接状态变化的函数，选填 |
| TICSDK.CONSTANT.EVENT.IM.BIG_GROUP_MSG_NOTIFY | 监听新消息(直播聊天室)事件，直播场景下必填 |
| TICSDK.CONSTANT.EVENT.IM.MSG_NOTIFY | 监听新消息函数，必填 |
| TICSDK.CONSTANT.EVENT.IM.GROUP_SYSTEM_NOTIFYS | 监听（多终端同步）群系统消息事件，必填 |
| TICSDK.CONSTANT.EVENT.IM.GROUP_INFO_CHANGE_NOTIFY | 监听群资料变化事件，选填 |
| TICSDK.CONSTANT.EVENT.IM.JOIN_CHATROOM_SUCC | 加入IM群组成功 |
| TICSDK.CONSTANT.EVENT.IM.LOGOUT_SUCC | 注销成功 |
| TICSDK.CONSTANT.EVENT.IM.RECEIVE_BOARD_ROOM_MSG | 接收到白板消息 |
| TICSDK.CONSTANT.EVENT.IM.RECEIVE_CHAT_ROOM_MSG | 接收到聊天消息 |
| TICSDK.CONSTANT.EVENT.IM.RECEIVE_C2C_MSG | 接收到 C2C 消息 |
| TICSDK.CONSTANT.EVENT.IM.SEND_CHAT_MSG_ERROR | 发送聊天消息失败 |
| TICSDK.CONSTANT.EVENT.IM.SEND_CHAT_MSG_EMPTY_RECEIVE_ERROR | 发送 C2C 消息没有接收人 |
| TICSDK.CONSTANT.EVENT.IM.SEND_CHAT_MSG_EMPTY_MSG_ERROR | 发送空消息 |
| TICSDK.CONSTANT.EVENT.IM.SEND_CHAT_MAX_LENGTH_MSG_ERROR | 发送消息超过最大长度 |
| TICSDK.CONSTANT.EVENT.IM.KICKED | 被踢下线 |
| TICSDK.CONSTANT.EVENT.IM.FRIEND_SYSTEM_NOTIFYS | 监听好友系统通知事件 |
| TICSDK.CONSTANT.EVENT.IM.PROFILE_SYSTEM_NOTIFYS | 监听资料系统通知函数对象 |
| TICSDK.CONSTANT.EVENT.IM.C2C_EVENT_NOTIFYS | 监听 C2C 消息通道的处理 |


#### BOARD 类：

| 事件名 | 描述 | 
|--------- | ---------|
| TICSDK.CONSTANT.EVENT.BOARD.HISTROY_DATA_COMPLETE | 历史数据同步完成 |
| TICSDK.CONSTANT.EVENT.BOARD.REAL_TIME_DATA | 接收到其他端的同步数据 |
| TICSDK.CONSTANT.EVENT.BOARD.ADD_BOARD | 新增白板 |
| TICSDK.CONSTANT.EVENT.BOARD.DELETE_BOARD | 删除白板 |
| TICSDK.CONSTANT.EVENT.BOARD.SWITCH_BOARD | 切换白板 |
| TICSDK.CONSTANT.EVENT.BOARD.ADD_GROUP | 增加组/文件 |
| TICSDK.CONSTANT.EVENT.BOARD.DELETE_GROUP | 删除组/文件 |
| TICSDK.CONSTANT.EVENT.BOARD.SWITCH_GROUP | 切换组/文件 |
| TICSDK.CONSTANT.EVENT.BOARD.ADD_DATA_ERROR | 接收到其他端的同步数据解析错误 |
| TICSDK.CONSTANT.EVENT.BOARD.IMG_START_LOAD | 背景图片开始加载 |
| TICSDK.CONSTANT.EVENT.BOARD.IMG_LOAD | 背景图片加载完成 |
| TICSDK.CONSTANT.EVENT.BOARD.IMG_ERROR | 背景图片加载错误 |
| TICSDK.CONSTANT.EVENT.BOARD.IMG_ABORT | 背景图片加载中断 |
| TICSDK.CONSTANT.EVENT.BOARD.VERIFY_SDK_SUCC | 白板服务鉴权通过 |
| TICSDK.CONSTANT.EVENT.BOARD.VERIFY_SDK_ERROR | 白板服务鉴权失败,请先购买服务 |
| TICSDK.CONSTANT.EVENT.BOARD.CANVAS_MOUSEDOWN | 白板鼠标点击事件 |
| TICSDK.CONSTANT.EVENT.BOARD.CANVAS_MOUSEMOVE | 白板鼠标移动事件 |
| TICSDK.CONSTANT.EVENT.BOARD.CANVAS_MOUSEUP | 白板鼠标弹起事件 |
| TICSDK.CONSTANT.EVENT.BOARD.CANVAS_MOUSELEAVE | 白板鼠标移出白板范围事件 |


#### COS 类：

| 事件名 | 描述 |
|--------- | ---------|
| TICSDK.CONSTANT.EVENT.COS.HASH_PROGRESS | 计算文件 MD5 值的进度回调函数 |
| TICSDK.CONSTANT.EVENT.COS.PROGRESS| 上传文件的进度 |
| TICSDK.CONSTANT.EVENT.COS.TASK_READY | 上传任务创建时的回调函数，返回一个 taskId |
| TICSDK.CONSTANT.EVENT.COS.GET_SIGN_ERROR | 大账号模式/URL 模式获取 COS 签名失败 |
| TICSDK.CONSTANT.EVENT.COS.GET_SIGN_SUCCESS | 大账号模式/URL 模式获取 COS 签名成功 |
| TICSDK.CONSTANT.EVENT.COS.DOES_NOT_SUPPORT_UPLOAD | 不支持上传。如果没有配置相应的 COS 参数，调用上传接口，则会提示不支持上传 |
| TICSDK.CONSTANT.EVENT.COS.UPLOAD_ERROR | 上传成功 |
| TICSDK.CONSTANT.EVENT.COS.UPLOAD_SUCCESS | 上传失败 |

