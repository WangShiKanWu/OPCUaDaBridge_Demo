# 系统架构说明

## 一、概述

本项目实现了一个 OPC DA 到 OPC UA 的桥接器，用于将传统 OPC DA 数据转换为 OPC UA 服务，使不同平台的客户端能够访问。

---

## 二、数据流

OPC DA Server → 桥接器 → OPC UA Server → OPC UA 客户端

---

## 三、核心组成

### 1. OPC DA 客户端
- 使用 Advosol OPCDA.NET 库
- 负责从 OPC DA Server 读取数据

---

### 2. OPC UA 服务端
- 基于 OPC Foundation .NET Standard OPC UA
- 对外提供统一的 OPC UA 接口

---

### 3. 映射配置层
- 使用 bridgeconfig.json 配置
- 定义 DA 点位与 UA 节点的映射关系

---

## 四、核心功能

- 支持多点位（Tag）映射
- 支持类型转换（Double / Int32 / Boolean / String）
- 实时数据同步（轮询方式）
- 单点位异常隔离（不会影响整体运行）
- 值变化去重，避免无效更新

---

## 五、运行模式

当前采用单进程架构：

- 一个进程同时完成：
  - OPC DA 数据采集
  - OPC UA 服务发布

该架构简单可靠，适用于当前桥接需求。

---

## 六、适用场景

- 将旧系统 OPC DA 数据接入现代 OPC UA 系统
- 实现跨平台工业数据访问
- 用于工业协议升级或系统过渡