# OPC DA → OPC UA 桥接器

## 一、项目简介
本项目实现了一个 OPC DA 到 OPC UA 的桥接器，用于将传统 OPC DA 数据通过 OPC UA 协议对外提供，使不同技术栈、不同平台的 OPC UA 客户端能够访问。

适用于工业系统升级、协议转换及数据集成场景。

---

## 二、功能特点

- 支持 OPC DA 数据采集
- 提供 OPC UA 服务端接口
- 支持多点位（Tag）映射（基于 JSON 配置）
- 支持类型转换（Double / Int32 / Boolean / String）

---

## 三、项目结构

```
Config/   配置文件
Docs/     文档说明
SRC/      源代码
```

---

## 四、快速运行

### 方式一：源码运行

1. 打开 SRC 中的 `.sln` 文件
2. 修改配置文件 `Config/bridgeconfig.json`
3. 运行项目

---

### 方式二：运行 Demo（推荐）

1. 下载 Release 中的 zip 包
2. 解压
3. 运行 exe

---

## 五、配置说明

配置文件：`bridgeconfig.json`

### 示例：

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
```

---

### 字段说明

- **DaItemId**：OPC DA 点位标识
- **UaNodeName**：在 OPC UA 中显示的节点名称
- **DataTypeName**：数据类型

---

## 六、支持数据类型

当前支持：

- Double
- Int32
- Boolean
- String

---

## 七、适用场景

- 工业系统升级
- 协议转换
- 数据集成
- OPC UA 对接

---

## 八、注意事项

- 需本地已安装 OPC DA 服务
- 建议在 Windows 环境运行
