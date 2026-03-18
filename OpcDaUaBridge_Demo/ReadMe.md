# OPC DA → OPC UA 桥接器

## 一、项目简介

本项目实现了一个 OPC DA 到 OPC UA 的桥接器，用于将传统 OPC DA 数据通过 OPC UA 协议对外提供，使不同技术栈、不同平台的 OPC UA 客户端能够访问。

适用于工业系统升级、协议转换及数据集成场景。

---

## 二、功能特点

- 支持 OPC DA 数据采集
- 提供 OPC UA 服务端接口
- 支持多点位（Tag）映射（基于 JSON 配置）
- 支持类型安全转换（Double / Int32 / Boolean / String）
- 实时数据同步（轮询方式）
- 值变化去重，避免无效更新
- 单点位异常隔离，不影响整体运行

---

## 三、项目结构

OpcDaUaBridge_Demo/
│
├── 1_Run/ 可执行程序（直接运行）
├── 2_Config/ 配置示例
├── 3_Docs/ 文档与截图
├── 4_Source/ 源码备份
└── README.md 项目说明


---

## 四、运行环境

- .NET 8 Runtime
- OPC DA Server（推荐 Matrikon Simulation Server）
- OPC UA 客户端（如 Matrikon OPC UA Explorer 或 UA Expert）

---

## 五、快速开始

### 1. 启动 OPC DA Server
确保 OPC DA Server 已启动（例如 Matrikon Simulation Server）。

---

### 2. 运行桥接器

进入目录：
1_Run/OpcDaUaBridge_v1.0/
双击运行：OpcDaUaBridge.exe


---

### 3. 连接 OPC UA 服务

使用 OPC UA 客户端连接：
opc.tcp://localhost:4840/OpcDaUaBridge


---

### 4. 验证结果

连接成功后，在客户端中浏览：
Objects → Demo


应看到节点：

- TestDouble
- TestInt32
- TestBool
- TestString

并且节点数值会实时变化。

---

## 六、配置说明

配置文件：
bridgeconfig.json


示例：

```json
{
  "Mappings": [
    {
      "DaItemId": "Random.Real8",
      "UaNodeName": "TestDouble",
      "DataTypeName": "Double"
    }
  ]
}


字段说明

DaItemId：OPC DA 点位标识

UaNodeName：在 OPC UA 中显示的节点名称

DataTypeName：数据类型

---


##七、支持数据类型

当前支持：

Double

Int32

Boolean

String

---


##八、验证情况

本项目已完成实际测试验证：

OPC UA 客户端可成功连接

节点结构正确显示

数据实时同步更新

类型转换正确

多点位运行稳定


---


##九、技术栈

.NET 8

OPC Foundation UA .NET Standard

Advosol OPCDA.NET


---



##十、项目状态

当前版本：V1.0

已完成开发与调试

已通过 OPC UA 客户端验证

可作为基础桥接器使用


---


十一、说明

本项目为功能验证与基础实现版本，适用于：

协议转换验证

系统集成测试

工业数据接入演示

如需进一步提升稳定性或扩展功能，可在此基础上进行增强开发。


