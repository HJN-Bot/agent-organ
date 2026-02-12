# 工厂智能助手集群（Factory Smart Assistant Cluster）

## 0. 与Agent Organ核心概念的集成

### Agent Organ核心价值
- **器官感**：工厂智能助手集群作为工厂的"外置器官"，持续、自然地融入生产流程
- **低摩擦**：通过语音和物理按钮触发，1秒内可开始操作，减少工人认知负担
- **感知优先**：输入的首要价值是"感知"生产状态，不是"炫技"
- **神经反射式输出**：关键时刻提供及时反馈，少打扰但很有用
- **可审计**：所有操作和决策都有记录，可追溯、可分析

### 集成点
1. **从"工具"到"器官"**：将工厂智能助手从"设备集群"升级为"生产器官"，持续感知和辅助生产
2. **自主等级**：采用Agent Organ的L1/L2/L3自主等级，平衡自动化与人工控制
   - L1：自动记录（默认）- 捕获→结构化→入库
   - L2：建议输出（默认）- 给下一步建议，工人确认
   - L3：白名单自动执行（可选）- 低风险动作自动执行
3. **多模态交互**：声（语音指导）、光（状态指示）、屏（操作指导）的立体反馈
4. **事件化架构**：统一输入源的事件schema，实现数据标准化与可追溯


## 一、场景背景与核心痛点

### 工厂流水线场景
- **高频痛点**：
  1. **操作规范难记忆**：流水线工人需要记忆大量操作步骤和质量标准
  2. **错误率高**：人工操作容易出错，导致产品质量问题
  3. **培训成本高**：新员工上手慢，需要老员工带教
  4. **异常处理慢**：出现异常时，需要等待技术人员指导
  5. **数据采集难**：生产数据手动记录，效率低且易出错


## 二、智能助手集群设计

### 硬件集群配置
- **中央控制终端**：iPad/平板（显示整体生产状态、数据分析）
- **工位节点**（每个工位一个）：
  1. **操作指导屏**：小型显示屏，显示步骤和标准
  2. **质量检测器**：摄像头 + 传感器，检测产品质量
  3. **操作按钮**：物理按钮，用于确认步骤完成
  4. **状态指示灯**：LED灯，显示工位状态（正常/异常/警告）
  5. **语音扬声器**：播放操作指导和警告
- **巡检节点**：便携设备，用于巡查时的数据采集和异常处理


### 硬件实现方案（48h可完成）
- **中央终端**：iPad/平板（现有设备）
- **工位节点**：
  - ESP32 + 小型显示屏（操作指导屏）
  - ESP32 + 摄像头模块（质量检测器）
  - ESP32 + 按钮（操作按钮）
  - ESP32 + LED灯（状态指示灯）
  - ESP32 + 扬声器（语音扬声器）
- **巡检节点**：ESP32 + 小型显示屏 + 摄像头
- **连接方式**：所有节点通过Wi-Fi/BLE连接到中央终端


### 硬件组件清单与采购建议

#### 核心组件
| 组件名称 | 数量 | 价格范围（人民币） | 功能 | 采购建议 |
|---------|------|-------------------|------|----------|
| ESP32开发板 | 5-8 | 20-30/个 | 核心控制器，支持Wi-Fi/BLE | 推荐ESP32-DevKitC，性价比高，资料丰富 |
| 小型OLED显示屏（0.96英寸） | 3-5 | 10-15/个 | 显示操作指导和状态 | 推荐I2C接口，接线简单 |
| 摄像头模块（OV2640） | 2-3 | 30-40/个 | 质量检测和文档扫描 | 支持JPEG压缩，适合ESP32 |
| LED灯（RGB） | 5-8 | 2-5/个 | 状态指示 | 推荐NeoPixel或普通RGB LED |
| 按钮（轻触开关） | 5-8 | 1-2/个 | 操作确认和触发 | 推荐6x6mm轻触开关 |
| 扬声器（微型） | 3-5 | 5-10/个 | 语音指导和提示音 | 推荐8Ω 0.5W微型扬声器 |
| 麦克风模块（MAX9814） | 2-3 | 10-15/个 | 语音输入 | 内置放大器，音质好 |
| 面包板 | 2-3 | 5-10/个 | 原型搭建 | 推荐400孔面包板 |
| 杜邦线（公对公、公对母） | 100-200 | 10-20/套 | 连接组件 | 推荐40Pin套装 |
| 电源模块（5V 2A） | 2-3 | 10-15/个 | 为硬件节点供电 | 推荐USB电源模块 |

#### 工具与配件
| 工具名称 | 数量 | 价格范围（人民币） | 用途 | 采购建议 |
|---------|------|-------------------|------|----------|
| 电烙铁套装 | 1 | 30-50 | 焊接组件 | 推荐恒温电烙铁 |
| 万用表 | 1 | 20-40 | 测量电压、电流 | 推荐数字万用表 |
| 热缩管 | 1 | 5-10 | 绝缘保护 | 推荐多规格套装 |
| 扎带 | 50-100 | 5-10 | 整理线缆 | 推荐尼龙扎带 |

#### 采购渠道建议
1. **线上平台**：淘宝、京东、拼多多等，价格透明，选择多样
2. **电子元件店**：当地电子市场，可现场挑选，立等可取
3. **开发板经销商**：如安信可、乐鑫官方授权经销商，品质有保障
4. **二手平台**：闲鱼等，可购买二手iPad/平板，降低成本

#### 预算估计
- **基础版**（1个工位节点 + 1个巡检节点）：约300-400元
- **标准版**（3个工位节点 + 1个巡检节点）：约500-700元
- **完整版**（5个工位节点 + 1个巡检节点）：约800-1000元

#### 时间考虑
- 建议提前3-5天采购，确保所有组件到货
- 预留1天时间进行硬件测试和调试


## 三、实用功能与集群效果

### 1. 智能操作指导（个性化）
- **触发**：工人到达工位，系统自动识别工人ID（通过NFC/人脸识别）
- **集群效果**：
  - 中央终端显示该工位的生产计划和工人技能等级
  - 工位节点的操作指导屏显示个性化步骤（根据工人熟练度调整详细程度）
  - 状态指示灯变为绿色，表示准备就绪
- **智能输出**：根据工人历史操作数据，自动调整指导内容的详细程度，新手显示详细步骤，熟手显示关键要点


### 2. 实时质量检测（集群协同）
- **触发**：工人完成操作，按下确认按钮
- **集群效果**：
  - 质量检测器启动，拍摄产品照片并分析
  - 中央终端同步接收质量数据
  - 相邻工位的状态指示灯变为黄色，表示等待质量检测结果
- **智能输出**：AI分析产品质量，实时反馈：
  - 合格：状态指示灯变为绿色，语音提示"质量合格，继续下一个"
  - 轻微异常：状态指示灯变为橙色，操作指导屏显示修正步骤
  - 严重异常：状态指示灯变为红色，中央终端警报，通知巡检人员


### 3. 异常处理（集群联动）
- **触发**：质量检测器检测到严重异常或工人按下求助按钮
- **集群效果**：
  - 该工位状态指示灯变为红色并闪烁
  - 中央终端显示异常位置和类型
  - 巡检节点收到通知，显示前往路线
  - 相邻工位状态指示灯变为蓝色，表示暂停
- **智能输出**：AI分析异常原因，在中央终端和巡检节点显示可能的解决方案，巡检人员到达前，系统提供临时应对措施


### 4. 培训模式（个性化学习）
- **触发**：新员工培训时，选择培训模式
- **集群效果**：
  - 操作指导屏显示详细培训视频和步骤
  - 质量检测器拍摄操作过程，分析动作是否标准
  - 中央终端记录培训进度和成绩
- **智能输出**：根据培训表现，自动调整培训内容和难度，针对薄弱环节加强练习


### 5. 生产数据采集与分析（智能报表）
- **触发**：系统自动采集生产数据
- **集群效果**：
  - 所有工位节点实时上传生产数据
  - 中央终端汇总数据，生成实时生产报表
  - 状态指示灯根据生产目标完成情况变色（绿色：达标，黄色：接近，红色：未达标）
- **智能输出**：AI分析生产数据，生成个性化报表：
  - 管理层：整体生产效率、质量趋势、瓶颈分析
  - 班组长：本班组生产进度、质量问题分布
  - 工人：个人操作效率、质量达标率、技能提升建议


## 四、技术实现要点

### 1. 硬件集成
- **ESP32开发板**：作为工位节点的核心控制器，支持Wi-Fi/BLE通信
- **传感器模块**：摄像头（质量检测）、按钮（操作确认）、LED（状态指示）
- **显示屏**：小型OLED/LCD显示屏，显示操作指导
- **音频**：扬声器，播放语音指导


### 2. 软件架构
- **中央终端App**：iPad/平板上的应用，负责：
  - 集群管理：连接和管理所有工位节点
  - 数据汇总：收集和分析生产数据
  - 可视化：显示生产状态、报表和分析
  - AI集成：运行质量检测和数据分析模型

- **工位节点固件**：ESP32上运行的代码，负责：
  - 本地控制：控制传感器和执行器
  - 数据采集：采集操作数据和质量数据
  - 通信：与中央终端通信
  - 本地反馈：显示状态和播放语音


### 4. 工位节点固件代码框架

#### 代码架构
```
├── main.cpp              # 主程序入口
├── config.h              # 配置文件
├── communication/        # 通信模块
│   ├── mqtt_client.cpp   # MQTT客户端
│   ├── wifi_manager.cpp  # Wi-Fi管理
│   └── ble_manager.cpp   # BLE管理（可选）
├── sensors/              # 传感器模块
│   ├── camera.cpp        # 摄像头控制
│   ├── button.cpp        # 按钮控制
│   └── microphone.cpp    # 麦克风控制
├── actuators/            # 执行器模块
│   ├── display.cpp       # 显示屏控制
│   ├── led.cpp           # LED控制
│   └── speaker.cpp       # 扬声器控制
├── feedback/             # 反馈模块
│   ├── audio.cpp         # 音频反馈
│   ├── visual.cpp        # 视觉反馈
│   └── haptic.cpp        # 触觉反馈（可选）
├── utils/                # 工具模块
│   ├── json_parser.cpp   # JSON解析
│   ├── time_utils.cpp    # 时间工具
│   └── error_handling.cpp # 错误处理
└── models/               # 本地模型（可选）
    └── quality_detection.cpp # 本地质量检测模型
```

#### 核心代码示例

##### main.cpp（主程序）
```cpp
#include <Arduino.h>
#include "config.h"
#include "communication/mqtt_client.h"
#include "sensors/button.h"
#include "sensors/camera.h"
#include "actuators/display.h"
#include "actuators/led.h"
#include "actuators/speaker.h"
#include "feedback/audio.h"
#include "feedback/visual.h"

// 全局变量
MQTTClient mqttClient;
Button button;
Camera camera;
Display display;
LED led;
Speaker speaker;

// 状态变量
String currentWorkerId = "";
String currentTask = "";
int currentStep = 0;
bool isProcessing = false;

void setup() {
  // 初始化串口
  Serial.begin(115200);
  
  // 初始化硬件
  button.init();
  camera.init();
  display.init();
  led.init();
  speaker.init();
  
  // 初始化通信
  mqttClient.init();
  mqttClient.connect();
  mqttClient.subscribe("factory/工位1/commands");
  
  // 初始化完成
  led.setColor(LED_GREEN);
  speaker.playTone(NOTE_C5, 500);
  display.showMessage("初始化完成", "等待指令...");
  
  Serial.println("工位节点初始化完成");
}

void loop() {
  // 处理MQTT消息
  mqttClient.loop();
  
  // 处理按钮事件
  if (button.isPressed()) {
    handleButtonPress();
  }
  
  // 处理状态更新
  updateState();
  
  delay(100);
}

void handleButtonPress() {
  if (isProcessing) return;
  
  isProcessing = true;
  
  // 根据当前状态处理按钮事件
  switch (getCurrentState()) {
    case STATE_IDLE:
      // 开始新任务
      startNewTask();
      break;
    case STATE_OPERATING:
      // 完成当前步骤
      completeStep();
      break;
    case STATE_QUALITY_CHECK:
      // 触发质量检测
      performQualityCheck();
      break;
    case STATE_ERROR:
      // 求助
      sendHelpRequest();
      break;
  }
  
  isProcessing = false;
}

void performQualityCheck() {
  // 拍摄照片
  camera.capture();
  
  // 显示处理中
  led.setColor(LED_YELLOW);
  display.showMessage("质量检测", "正在分析...");
  
  // 发送照片到中央终端
  mqttClient.publish("factory/工位1/quality_data", camera.getImageData());
  
  // 等待结果
  // 注意：实际实现中应该使用回调函数处理MQTT响应
}

void updateState() {
  // 根据当前状态更新LED和显示屏
  switch (getCurrentState()) {
    case STATE_IDLE:
      led.setColor(LED_BLUE);
      break;
    case STATE_OPERATING:
      led.setColor(LED_GREEN);
      break;
    case STATE_QUALITY_CHECK:
      led.setColor(LED_YELLOW);
      break;
    case STATE_ERROR:
      led.setColor(LED_RED);
      speaker.playTone(NOTE_A4, 1000);
      break;
  }
}
```

##### config.h（配置文件）
```cpp
// Wi-Fi配置
#define WIFI_SSID "FactoryNetwork"
#define WIFI_PASSWORD "FactoryPassword"

// MQTT配置
#define MQTT_BROKER "192.168.1.100"
#define MQTT_PORT 1883
#define MQTT_CLIENT_ID "ESP32_工位1"
#define MQTT_TOPIC_COMMANDS "factory/工位1/commands"
#define MQTT_TOPIC_STATUS "factory/工位1/status"
#define MQTT_TOPIC_QUALITY "factory/工位1/quality_data"

// 硬件引脚配置
#define BUTTON_PIN 2
#define LED_PIN 13
#define SPEAKER_PIN 12
#define DISPLAY_SDA 21
#define DISPLAY_SCL 22
#define CAMERA_PIN 32

// LED颜色定义
#define LED_OFF 0
#define LED_RED 1
#define LED_GREEN 2
#define LED_BLUE 3
#define LED_YELLOW 4

// 状态定义
#define STATE_IDLE 0
#define STATE_OPERATING 1
#define STATE_QUALITY_CHECK 2
#define STATE_ERROR 3

// 音频定义
#define NOTE_C4 262
#define NOTE_D4 294
#define NOTE_E4 330
#define NOTE_F4 349
#define NOTE_G4 392
#define NOTE_A4 440
#define NOTE_B4 494
#define NOTE_C5 523
```

##### communication/mqtt_client.cpp（MQTT客户端）
```cpp
#include <Arduino.h>
#include <PubSubClient.h>
#include <WiFi.h>
#include "config.h"

class MQTTClient {
private:
  WiFiClient wifiClient;
  PubSubClient client;
  
public:
  void init() {
    client.setClient(wifiClient);
    client.setServer(MQTT_BROKER, MQTT_PORT);
    client.setCallback([this](char* topic, byte* payload, unsigned int length) {
      this->callback(topic, payload, length);
    });
  }
  
  bool connect() {
    if (client.connect(MQTT_CLIENT_ID)) {
      Serial.println("MQTT连接成功");
      return true;
    } else {
      Serial.print("MQTT连接失败，状态码：");
      Serial.println(client.state());
      return false;
    }
  }
  
  void subscribe(String topic) {
    client.subscribe(topic.c_str());
  }
  
  void publish(String topic, String message) {
    client.publish(topic.c_str(), message.c_str());
  }
  
  void loop() {
    if (!client.connected()) {
      connect();
    }
    client.loop();
  }
  
  void callback(char* topic, byte* payload, unsigned int length) {
    // 处理接收到的消息
    String message = String((char*)payload).substring(0, length);
    Serial.print("收到消息 [");
    Serial.print(topic);
    Serial.print("]: ");
    Serial.println(message);
    
    // 解析消息并执行相应操作
    processMessage(topic, message);
  }
  
  void processMessage(String topic, String message) {
    // 处理不同类型的消息
    if (topic == MQTT_TOPIC_COMMANDS) {
      // 处理命令消息
      if (message.startsWith("SET_WORKER")) {
        // 设置工人信息
        currentWorkerId = message.substring(10);
        display.showMessage("工人已设置", currentWorkerId);
      } else if (message.startsWith("SET_TASK")) {
        // 设置任务
        currentTask = message.substring(8);
        currentStep = 0;
        display.showMessage("新任务", currentTask);
      } else if (message.startsWith("SET_STEP")) {
        // 设置步骤
        currentStep = message.substring(8).toInt();
        display.showMessage("步骤 " + String(currentStep), getStepInstruction(currentStep));
      } else if (message.startsWith("QUALITY_RESULT")) {
        // 处理质量检测结果
        handleQualityResult(message.substring(14));
      } else if (message.startsWith("ERROR_SOLUTION")) {
        // 处理错误解决方案
        handleErrorSolution(message.substring(15));
      }
    }
  }
};
```

##### sensors/button.cpp（按钮控制）
```cpp
#include <Arduino.h>
#include "config.h"

class Button {
private:
  int pin;
  bool lastState;
  unsigned long lastDebounceTime;
  const unsigned long debounceDelay = 50;
  
public:
  void init() {
    pin = BUTTON_PIN;
    pinMode(pin, INPUT_PULLUP);
    lastState = digitalRead(pin);
    lastDebounceTime = 0;
  }
  
  bool isPressed() {
    bool reading = digitalRead(pin);
    
    if (reading != lastState) {
      lastDebounceTime = millis();
    }
    
    if ((millis() - lastDebounceTime) > debounceDelay) {
      if (reading != lastState) {
        lastState = reading;
        return !reading; // 按钮按下时返回true
      }
    }
    
    return false;
  }
};
```

##### actuators/display.cpp（显示屏控制）
```cpp
#include <Arduino.h>
#include <Adafruit_SSD1306.h>
#include "config.h"

class Display {
private:
  Adafruit_SSD1306 display;
  
public:
  void init() {
    display = Adafruit_SSD1306(128, 64, &Wire, -1);
    if (!display.begin(SSD1306_SWITCHCAPVCC, 0x3C)) {
      Serial.println("显示屏初始化失败");
      return;
    }
    display.clearDisplay();
    display.setTextSize(1);
    display.setTextColor(SSD1306_WHITE);
    display.setCursor(0, 0);
    display.println("初始化中...");
    display.display();
  }
  
  void showMessage(String title, String message) {
    display.clearDisplay();
    display.setTextSize(1);
    display.setTextColor(SSD1306_WHITE);
    display.setCursor(0, 0);
    display.println(title);
    display.setTextSize(1);
    display.setCursor(0, 20);
    display.println(message);
    display.display();
  }
  
  void showSteps(int currentStep, int totalSteps, String instruction) {
    display.clearDisplay();
    display.setTextSize(1);
    display.setTextColor(SSD1306_WHITE);
    display.setCursor(0, 0);
    display.print("步骤 " + String(currentStep) + "/" + String(totalSteps));
    display.setTextSize(1);
    display.setCursor(0, 20);
    display.println(instruction);
    display.display();
  }
};
```

##### feedback/audio.cpp（音频反馈）
```cpp
#include <Arduino.h>
#include "config.h"

class Audio {
private:
  int speakerPin;
  
public:
  void init() {
    speakerPin = SPEAKER_PIN;
    pinMode(speakerPin, OUTPUT);
  }
  
  void playTone(int frequency, int duration) {
    tone(speakerPin, frequency, duration);
  }
  
  void playSuccessSound() {
    playTone(NOTE_C5, 200);
    delay(250);
    playTone(NOTE_E5, 200);
    delay(250);
    playTone(NOTE_G5, 200);
  }
  
  void playErrorSound() {
    playTone(NOTE_G4, 300);
    delay(350);
    playTone(NOTE_E4, 300);
    delay(350);
    playTone(NOTE_C4, 300);
  }
  
  void playWarningSound() {
    playTone(NOTE_A4, 100);
    delay(150);
    playTone(NOTE_A4, 100);
    delay(150);
    playTone(NOTE_A4, 100);
  }
};
```

#### 通信协议

##### MQTT主题结构
```
factory/
  ├── 工位1/
  │   ├── commands    # 中央终端发送到工位的命令
  │   ├── status      # 工位发送到中央终端的状态
  │   └── quality_data # 工位发送到中央终端的质量数据
  ├── 工位2/
  │   ├── commands
  │   ├── status
  │   └── quality_data
  └── all/            # 发送到所有工位的命令
      └── commands
```

##### 消息格式（JSON）

###### 命令消息（中央终端 → 工位）
```json
{
  "type": "SET_WORKER",
  "data": {
    "worker_id": "W001",
    "skill_level": 3,
    "name": "张三"
  }
}
```

###### 状态消息（工位 → 中央终端）
```json
{
  "type": "STATUS_UPDATE",
  "data": {
    "worker_id": "W001",
    "task": "装配产品A",
    "step": 2,
    "status": "OPERATING",
    "timestamp": "2026-02-12T10:30:00Z"
  }
}
```

###### 质量数据消息（工位 → 中央终端）
```json
{
  "type": "QUALITY_DATA",
  "data": {
    "product_id": "P12345",
    "image_url": "data:image/jpeg;base64,...",
    "timestamp": "2026-02-12T10:35:00Z"
  }
}
```

##### 本地异常处理
- **硬件故障**：检测到传感器/执行器故障时，发送错误消息到中央终端
- **通信中断**：当MQTT连接断开时，本地缓存关键数据，待连接恢复后重发
- **电量低**：当检测到电量低时，进入低功耗模式，仅保留核心功能

##### 性能优化
- **内存管理**：使用动态内存分配，避免内存泄漏
- **电源管理**：非活动时进入深度睡眠模式，延长电池寿命
- **数据压缩**：对图像数据进行压缩后传输，减少带宽使用
- **本地缓存**：缓存常用指令和数据，减少网络请求

#### 编译与上传
1. **开发环境**：Arduino IDE或PlatformIO
2. **依赖库**：
   - PubSubClient（MQTT客户端）
   - Adafruit_SSD1306（OLED显示屏）
   - ArduinoJson（JSON解析）
   - ESP32 Arduino Core（ESP32支持）
3. **上传方法**：
   - 使用USB线连接ESP32到电脑
   - 在IDE中选择对应开发板和端口
   - 编译并上传代码

#### 测试与调试
- **串口调试**：使用Serial.print()输出调试信息
- **LED状态**：通过LED颜色和闪烁模式指示当前状态
- **MQTT监控**：使用MQTT.fx等工具监控MQTT消息
- **模拟测试**：使用中央终端模拟发送命令，测试工位节点响应


### 3. 中央终端App UI界面与交互流程

#### App架构
- **主要页面**：
  1. **仪表盘**：生产状态总览
  2. **工位管理**：单个工位详情和控制
  3. **数据分析**：生产数据报表和趋势
  4. **异常处理**：异常事件管理和历史
  5. **系统设置**：设备管理和配置

#### 详细UI设计

##### 1. 仪表盘页面
- **顶部导航栏**：
  - 应用标题："工厂智能助手集群"
  - 用户角色切换：管理层/班组长/工人
  - 通知中心入口

- **核心区域**：
  - **生产状态卡片**：
    - 今日产量：大数字显示，同比增长
    - 质量合格率：环形进度条，颜色编码
    - 效率指标：折线图，显示当日趋势
  - **工位状态网格**：
    - 每个工位显示为卡片，颜色对应状态（绿色：正常，黄色：警告，红色：异常）
    - 点击卡片进入工位详情
  - **异常警报列表**：
    - 最近异常事件，按紧急程度排序
    - 显示异常类型、位置、时间

- **底部快捷操作**：
  - 快速巡检
  - 开始/暂停生产
  - 紧急停止

##### 2. 工位管理页面
- **顶部导航**：
  - 工位名称和编号
  - 返回按钮
  - 编辑按钮

- **工位信息区**：
  - 工人信息：当前操作人员、技能等级
  - 设备信息：设备型号、状态、维护时间
  - 生产信息：当前产品、计划数量、完成数量

- **操作指导区**：
  - 步骤列表：当前步骤高亮显示
  - 操作说明：图文并茂的操作指导
  - 质量标准：关键质量控制点

- **实时数据区**：
  - 操作时间：当前步骤耗时
  - 质量数据：最近质量检测结果
  - 效率指标：该工位今日效率

- **控制按钮**：
  - 开始/暂停
  - 质量检测
  - 求助
  - 完成步骤

##### 3. 数据分析页面
- **顶部导航**：
  - 时间范围选择：今日/本周/本月/自定义
  - 数据类型选择：产量/质量/效率/异常

- **图表区域**：
  - **趋势图**：显示选定时间范围的数据趋势
  - **对比图**：不同工位/不同时间段的对比
  - **分布饼图**：质量问题类型分布

- **数据表格**：
  - 详细数据列表，支持排序和筛选
  - 导出按钮：导出为Excel/PDF

- **智能洞察**：
  - AI生成的数据分析和建议
  - 瓶颈识别和优化建议

##### 4. 异常处理页面
- **顶部导航**：
  - 异常类型筛选
  - 状态筛选：未处理/处理中/已解决

- **异常列表**：
  - 异常卡片：显示异常类型、位置、时间、状态
  - 严重程度标识：颜色编码（红色：严重，黄色：中等，蓝色：轻微）
  - 点击卡片进入异常详情

- **异常详情**：
  - 异常描述：详细信息和现场照片
  - 处理历史：已采取的措施
  - 解决方案：AI建议的解决方案
  - 处理按钮：分配处理人、标记为已解决

##### 5. 系统设置页面
- **设备管理**：
  - 已连接设备列表
  - 设备状态和信号强度
  - 添加/删除设备

- **用户管理**：
  - 用户列表和权限设置
  - 工人技能等级管理

- **系统配置**：
  - 网络设置
  - 通知设置
  - AI模型设置
  - 数据存储设置

#### 交互流程

##### 1. 开机启动流程
1. App启动，显示加载动画
2. 自动扫描并连接所有工位节点
3. 显示仪表盘页面，更新生产状态
4. 播放启动成功提示音

##### 2. 工位操作流程
1. 工人到达工位，系统自动识别（NFC/人脸识别）
2. App发送工人信息到对应工位节点
3. 工位节点显示个性化操作指导
4. 工人完成操作，按下确认按钮
5. 工位节点采集质量数据，发送到App
6. App分析数据，返回结果到工位节点
7. 工位节点显示质量结果和下一步指导

##### 3. 异常处理流程
1. 工位节点检测到异常，发送异常信息到App
2. App显示异常警报，播放警报音
3. 管理人员点击异常卡片，查看详情
4. App显示AI建议的解决方案
5. 管理人员选择解决方案，发送到工位节点
6. 工位节点显示解决方案，指导工人操作
7. 异常解决后，工位节点发送确认信息到App
8. App更新异常状态为已解决

##### 4. 数据分析流程
1. 管理人员进入数据分析页面
2. 选择时间范围和数据类型
3. App加载并显示对应数据图表
4. 点击图表中的数据点，查看详细信息
5. 查看AI生成的数据分析和建议
6. 点击导出按钮，导出报表

#### 视觉设计
- **配色方案**：
  - 主色：深蓝色（#1A365D）- 专业、可靠
  - 辅助色：
    - 绿色（#38A169）- 正常、成功
    - 黄色（#ED8936）- 警告、注意
    - 红色（#E53E3E）- 异常、错误
    - 蓝色（#3182CE）- 信息、提示

- **字体**：
  - 标题：无衬线字体，粗体
  - 正文：无衬线字体，常规
  - 数据：等宽字体，突出显示

- **图标**：
  - 使用线性图标，风格统一
  - 功能图标：简洁明了，易于识别
  - 状态图标：颜色编码，直观反映状态

- **动画**：
  - 过渡动画：平滑的页面切换
  - 数据更新动画：数值变化时的平滑过渡
  - 警报动画：醒目的闪烁效果

- **响应式设计**：
  - 适配不同尺寸的iPad/平板
  - 横屏模式：更宽的图表和数据表格
  - 竖屏模式：更紧凑的布局，优先显示关键信息


### 3. 通信协议
- **MQTT**：轻量级消息协议，适合设备间通信
- **Wi-Fi**：工位节点与中央终端的主要通信方式
- **BLE**：巡检节点与中央终端的通信方式


### 4. AI模型
- **质量检测**：使用MobileNet等轻量视觉模型，检测产品缺陷
- **操作分析**：使用姿态估计模型，分析工人操作是否标准
- **数据预测**：使用时间序列模型，预测生产效率和质量趋势


### 5. 数据存储
- **本地存储**：工位节点存储本地操作数据
- **中央存储**：中央终端存储所有工位数据和分析结果
- **云存储**（可选）：将数据同步到云端，实现远程监控


## 五、48h开发计划

### Day 1
- **0-6h**：硬件节点制作
  - 组装ESP32 + 显示屏 + 摄像头 + LED + 按钮
  - 测试硬件连接和基本功能

- **6-12h**：通信协议实现
  - 配置MQTT broker
  - 实现工位节点与中央终端的通信
  - 测试集群通信可靠性

- **12-18h**：中央终端App开发
  - 设计UI界面
  - 实现节点管理功能
  - 实现数据显示功能

- **18-24h**：基本功能实现
  - 实现操作指导功能
  - 实现质量检测功能
  - 测试基本流程


### Day 2
- **0-6h**：AI模型集成
  - 集成质量检测模型
  - 实现数据分析功能
  - 测试AI预测准确性

- **6-12h**：异常处理和培训模式
  - 实现异常检测和报警功能
  - 实现培训模式功能
  - 测试集群联动效果

- **12-18h**：数据采集和报表
  - 实现生产数据采集功能
  - 实现智能报表生成
  - 测试数据分析准确性

- **18-24h**：演示准备和调试
  - 优化用户体验
  - 测试端到端流程
  - 准备演示脚本


## 六、演示亮点

### 1. 集群协同效果
- 展示多个工位节点同时工作，状态同步变化
- 演示异常处理时的集群联动效果
- 展示中央终端对所有节点的实时监控


### 2. 智能个性化
- 切换不同熟练度的工人ID，展示指导内容的自动调整
- 演示培训模式下的个性化学习路径
- 展示针对不同角色的个性化报表


### 3. 实时质量检测
- 演示AI检测产品质量的过程和结果
- 展示不同异常等级的处理流程
- 演示质量数据的实时分析和反馈


### 4. 数据可视化
- 展示实时生产状态的可视化界面
- 演示生产数据的趋势分析
- 展示瓶颈分析和优化建议


### 5. 实用性展示
- 量化展示错误率降低效果
- 展示培训时间缩短效果
- 展示生产效率提升效果


## 七、市场潜力与应用扩展

### 市场潜力
- **制造业**：流水线生产、质量控制、员工培训
- **物流业**：分拣操作、包装标准、仓库管理
- **服务业**：餐饮操作、酒店服务、零售标准


### 应用扩展
- **远程监控**：通过云端实现远程生产监控
- **预测维护**：基于设备数据预测维护需求
- **供应链优化**：基于生产数据优化供应链
- **员工绩效**：基于操作数据评估员工绩效


## 八、总结

工厂智能助手集群通过硬件集群的协同工作和AI的智能分析，实现了：

1. **降低错误率**：实时质量检测和操作指导，减少人为错误
2. **提高效率**：个性化操作指导，减少思考时间，提高生产速度
3. **降低培训成本**：智能培训模式，缩短新员工上手时间
4. **快速异常处理**：集群联动和AI分析，快速解决异常问题
5. **数据驱动决策**：实时生产数据和AI分析，帮助管理层优化生产流程

同时，集群式硬件设计和多模态交互，为工厂生产带来了全新的智能化体验，展示了物联网、AI和边缘计算的融合应用潜力。