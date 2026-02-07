# 02｜信息源（Sources）与事件（Events）

## 1) 输入源（可从易到难落地）
### A. 语音
- 麦克风录音（短语音/长录音）
- 语音转写（ASR）

### B. 图像
- 相机拍照（文档/白板/屏幕/场景）
- OCR + 版面解析

### C. 设备与环境信号（可选）
- 位置（GPS/地理围栏）
- 时间（上下班/会议前后）
- 运动/心率/睡眠（来自手表/健康平台）

### D. 数字世界事件（手机作为“硬件代理”）
- 通知（邮件/IM/日历）
- 分享（Share sheet）
- 截图/剪贴板

## 2) 统一事件 Schema（建议）
无论输入来自哪里，统一成事件：
- event_id
- ts
- source_type: voice|image|text|notification|calendar|location|health
- payload_uri（原始媒体）
- transcript/ocr_text
- metadata: app/device/location
- sensitivity_level（数据分级）

## 3) 结构化落地（输出类型）
- Task（待办）
- Idea（想法）
- Evidence（证据/引用）
- Minutes（会议纪要）
- Memory（长期偏好/规则资产）
