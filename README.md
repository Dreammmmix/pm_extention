# PM智慧助手 - 产品经理每日知识推送Chrome插件

## 目录

- [PM智慧助手 - 产品经理每日知识推送Chrome插件](#pm智慧助手---产品经理每日知识推送chrome插件)
  - [产品概述](#产品概述)
  - [核心功能](#核心功能)
  - [用户体验流程](#用户体验流程)
  - [技术实现](#技术实现)
  - [开发路线图](#开发路线图)
  - [技术可行性分析](#技术可行性分析)
  - [安装说明](#安装说明)
  - [使用说明](#使用说明)
  - [更新日志](#更新日志)
    - [v1.4.1 (2024-03-23)](#v141-2024-03-23)
    - [v1.4.0 (2024-03-23)](#v140-2024-03-23)
    - [v1.3.0 (2024-03-23)](#v130-2024-03-23)
    - [v1.2.0 (2024-03-22)](#v120-2024-03-22)
    - [v1.1.0 (2024-03-22)](#v110-2024-03-22)
    - [v1.0.0 (2024-03-22)](#v100-2024-03-22)
  - [项目文件结构](#项目文件结构)
  - [下一步计划](#下一步计划)
  - [✨和cursor的交互过程](#和cursor的交互过程)

## 产品概述

PM智慧助手是一款专为产品经理设计的Chrome浏览器插件，通过AI技术每天推送产品管理相关的知识、技巧和行业动态，帮助产品经理持续学习成长。

弹窗页+配置页：

<div align="center">
  <img src="image/README/1742726787329.png" width="70%" />
</div>

配置页：

<div align="center">
  <img src="image/README/1742726819642.png" width="70%" />
</div>

导出的图片示例：

<div align="center">
  <img src="image/README/1742727107856.png" width="70%" />
</div>


## 核心功能

1. **每日知识推送**：自动推送产品经理相关知识，内容包括产品设计、用户研究、需求分析、项目管理等方面的技巧和最佳实践
2. **即时知识查询**：点击插件图标，即可获取AI生成的产品经理相关知识点
3. **知识刷新**：通过"获取新知识"按钮，随时手动更新知识内容
4. **知识收藏**：用户可收藏有价值的知识点，方便日后查阅
5. **Markdown支持**：支持富文本格式，包括加粗、列表、标题等Markdown语法
6. **每日知识缓存**：在一天内重复打开插件时使用缓存内容，避免重复请求API，节省资源
7. **深色/浅色主题**：支持自动或手动切换深色/浅色模式，适应不同环境和个人偏好
8. **一键复制**：支持一键复制知识内容，保留Markdown格式，方便分享或记录
9. **导出PNG卡片**：支持将知识内容导出为精美PNG图片，便于分享到社交媒体
10. **个性化知识推荐**：根据用户设置的偏好领域，智能推荐相关知识内容
11. **收藏内容管理**：在设置页面可以管理收藏的知识内容，支持复制和导出为PNG图片功能

## 用户体验流程

1. 用户安装插件后，每日会收到一条产品经理相关知识的通知
2. 点击Chrome工具栏中的插件图标，弹出知识展示窗口
3. 在同一天内再次点击插件图标时，会显示相同的知识内容（无需重复请求API）
4. 用户可以点击"获取新知识"按钮手动更新当天的知识
5. 用户可以收藏喜欢的知识点，并在"我的收藏"中查看
6. 用户可以根据喜好切换深色/浅色模式
7. 用户可以一键复制知识内容或导出为PNG图片
8. 用户可以在设置页面设置知识偏好，获取更相关的内容推送

## 技术实现

1. **AI接口调用**：

   - 使用DeepSeek API（deepseek-r1-250120模型）
   - 基础URL：https://ark.cn-beijing.volces.com/api/v3
   - 通过精心设计的提示词，引导AI生成高质量的产品经理知识内容
   - 根据用户知识偏好定制提示词，提供个性化内容
   - 支持用户自定义API Key，从火山引擎ARK控制台获取
2. **插件架构**：

   - 前端：HTML, CSS, JavaScript
   - 数据存储：Chrome Storage API
   - 后端通信：Fetch API
   - Markdown解析：marked.js
   - HTML转图片：html2canvas.js
   - 缓存机制：基于日期的本地存储缓存
   - 主题系统：CSS变量和媒体查询
3. **核心组件**：

   - 弹出窗口（popup.html）：展示知识内容和交互按钮
   - 后台脚本（background.js）：处理API调用和定时任务
   - 内容脚本（content.js）：实现网页内通知
   - 设置页面（options.html）：用户个性化配置
   - 样式系统：基于Apple设计语言和Linear App风格的现代UI


## 开发路线图

1. **阶段一**：基础功能实现

   - 插件框架搭建
   - AI API接口对接
   - 基础UI实现
2. **阶段二**：功能完善

   - 知识收藏功能
   - 用户设置页面
   - 每日推送定时功能
   - Markdown格式支持
   - 每日知识缓存功能
3. **阶段三**：优化迭代（已完成）

   - UI/UX优化
   - 深色/浅色主题支持
   - 响应式设计
   - 交互体验优化
4. **阶段四**：高级功能（已完成）

   - 一键复制功能
   - 导出PNG卡片功能
   - 个性化知识推荐系统
   - 用户自定义知识领域

## 技术可行性分析

基于已有的DeepSeek API和Chrome扩展开发框架，该项目技术实现完全可行。主要技术点包括：

1. API调用和参数配置
2. Chrome插件开发与生命周期管理
3. 本地数据存储
4. 定时任务实现
5. Markdown解析与渲染
6. HTML到图片的转换
7. 基于日期的缓存管理
8. 现代化的CSS变量系统
9. 用户偏好管理与个性化推荐

## 安装说明

1. **开发模式安装**

   - 打开Chrome浏览器，访问 `chrome://extensions/`
   - 开启右上角的"开发者模式"
   - 点击"加载已解压的扩展程序"
   - 选择 `pm_extension/extension`目录
   - 插件将被安装到Chrome浏览器中
2. **图标文件**

   - 请确保 `pm_extension/extension/images/`目录下包含以下图标文件：
     - icon16.png (16x16像素)
     - icon48.png (48x48像素)
     - icon128.png (128x128像素)

## 使用说明

1. **初始配置**

   - 首次使用时，请点击"前往设置"按钮
   - 在火山引擎ARK控制台获取您的API Key：[火山引擎ARK控制台](https://console.volcengine.com/ark/)
     - [火山引擎API Key配置教程](https://wcntkdvmwjsh.feishu.cn/wiki/ScEewJo8KideZmkRZ5ycEGqynmT)
   - 将API Key填入设置页面的API设置区域并保存
2. **查看知识**

   - 点击Chrome工具栏中的PM智慧助手图标
   - 在弹出窗口中查看产品经理知识
   - 当天首次打开时会请求新知识，之后重复打开会显示相同内容
3. **刷新知识**

   - 在弹出窗口中点击"获取新知识"按钮可以强制获取新的知识内容
   - 每天凌晨会自动重置缓存，确保每天至少获取一条新知识
4. **收藏知识**

   - 在弹出窗口中点击"收藏"按钮保存当前知识
   - 在设置页面查看所有收藏的知识
5. **复制与导出**

   - 点击知识卡片右上角的复制图标，可一键复制当前知识内容
   - 点击知识卡片右上角的图片图标，可将知识导出为PNG图片
6. **个性化设置**

   - 在设置页面选择您感兴趣的产品知识领域
   - 添加自定义知识领域标签
   - 系统将根据您的偏好推送更相关的内容
7. **设置通知**

   - 点击弹出窗口底部的"设置"链接
   - 在设置页面开启/关闭每日通知
   - 设置通知推送时间
8. **查看收藏**

   - 点击弹出窗口底部的"我的收藏"链接
   - 或者点击设置页面，查看"我的收藏"部分
   - 可以对收藏的知识进行复制和导出为PNG图片操作
   - 复制功能保留原始Markdown格式，方便二次编辑或分享
   - 导出PNG功能生成精美图片，便于在社交平台分享
9. **切换主题**

   - 在设置页面点击右上角的主题切换按钮
   - 在深色和浅色模式之间切换
   - 默认跟随系统设置

## 更新日志

### v1.4.1 (2024-03-23)

- 新增API Key自定义配置功能，支持用户使用自己的火山引擎ARK API Key
- 首次使用时增加提示，引导用户配置API Key
- 优化API调用逻辑，提高错误处理能力

弹窗页：

<div align="center">
  <img src="image/README/1742725752199.png" width="70%" />
</div>

设置页：

<div align="center">
  <img src="image/README/1742725838807.png" width="70%" />
</div>

### v1.4.0 (2024-03-23)

- 新增一键复制功能，支持复制知识内容并保留Markdown格式
- 新增导出PNG卡片功能，支持将知识转换为精美图片并下载
- 新增个性化知识推荐系统，根据用户兴趣定制内容
- 添加知识偏好设置页面，包括预设领域选择和自定义标签功能
- 支持自动根据用户偏好调整API请求，提供更相关的知识内容
- 增强收藏页面功能，添加复制和导出PNG功能，提升内容管理体验

设置页：

<div align="center">
  <img src="image/README/1742723478360.png" width="70%" />
</div>

弹窗页：

<div align="center">
  <img src="image/README/1742723503408.png" width="70%" />
</div>

### v1.3.0 (2024-03-23)

- 全新UI设计，采用Apple设计语言和Linear App风格
- 添加完整的深色/浅色主题支持，可手动切换或跟随系统
- 集成Font Awesome图标库，优化按钮和交互元素
- 重新设计的通知和反馈系统，提供更好的用户体验
- 优化滚动条样式和动画效果
- 改进Markdown内容渲染，提高可读性
- 重构CSS系统，使用变量实现一致性设计

<div align="center">
  <img src="image/README/1742723412563.png" width="70%" />
</div>

### v1.2.0 (2024-03-22)

- 新增每日知识缓存功能，在同一天内重复打开插件无需重复请求API
- 修改"再来一个"按钮为"获取新知识"，更明确表示其功能
- 添加午夜自动重置缓存机制，确保每天自动更新知识内容
- 优化API调用失败时的容错机制，使用最近的缓存内容作为备用

<div align="center">
  <img src="image/README/1742723379896.png" width="70%" />
</div>

### v1.1.0 (2024-03-22)

- 新增Markdown格式支持，知识卡片现在可以正确渲染加粗、列表、标题等格式
- 改进文本显示，支持适当换行和段落间距
- 优化样式，提升阅读体验
- 使用marked.js作为Markdown解析工具

### v1.0.0 (2024-03-22)

- 初始版本发布
- 实现基本知识推送功能
- 支持每日定时通知
- 实现知识收藏功能
- 提供用户设置页面
- icon来源：

  <div align="center">
    <img src="image/README/1742723825544.png" width="70%" />
  </div>

## 项目文件结构

```
pm/extension/
├── manifest.json        # 插件配置文件
├── popup.html           # 弹出窗口HTML
├── options.html         # 设置页面HTML
├── css/
│   └── popup.css        # 弹出窗口样式（包含主题变量）
├── js/
│   ├── background.js    # 后台服务脚本
│   ├── popup.js         # 弹出窗口脚本
│   ├── options.js       # 设置页面脚本
│   ├── marked.min.js    # Markdown解析库
│   └── html2canvas.min.js # HTML转图片库
└── images/
    ├── icon16.png       # 16x16像素图标
    ├── icon48.png       # 48x48像素图标
    └── icon128.png      # 128x128像素图标
```

## 下一步计划

1. 细化需求和UI设计（已完成）
2. 搭建基础代码框架（已完成）
3. 实现API调用逻辑（已完成）
4. 开发基础UI组件（已完成）
5. 添加Markdown格式支持（已完成）
6. 实现每日知识缓存功能（已完成）
7. 优化UI设计和用户体验（已完成）
8. 添加一键复制和导出PNG功能（已完成）
9. 实现个性化知识推荐系统（已完成）
10. 进行用户测试和收集反馈

## ✨和cursor的交互过程

1. 搭建框架

<div align="center">
  <img src="image/README/1742724029881.png" width="70%" />
</div>

2. markdown渲染

<div align="center">
  <img src="image/README/1742724065619.png" width="70%" />
</div>

3. 修正调用api逻辑

<div align="center">
  <img src="image/README/1742724082428.png" width="70%" />
</div>

4. 样式

<div align="center">
  <img src="image/README/1742724098623.png" width="70%" />
</div>

5. 样式，并手动调整了一下

<div align="center">
  <img src="image/README/1742724125903.png" width="70%" />
</div>

6. 修复收藏逻辑、保存设置逻辑

<div align="center">
  <img src="image/README/1742724143100.png" width="70%" />
</div>

<div align="center">
  <img src="image/README/1742724164626.png" width="70%" />
</div>

8. 导出

<div align="center">
  <img src="image/README/1742724184410.png" width="70%" />
</div>

9. 修复导出和样式

<div align="center">
  <img src="image/README/1742724203309.png" width="70%" />
</div>

<div align="center">
  <img src="image/README/1742724217160.png" width="70%" />
</div>

11. 补充设置页面的导出

<div align="center">
  <img src="image/README/1742724235111.png" width="70%" />
</div>

12. 逻辑更改为用户自行配置key

<div align="center">
  <img src="image/README/1742724261967.png" width="70%" />
</div>
