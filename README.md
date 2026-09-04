# Visual Island / 视觉岛

AI-powered visual asset management tool for designers.

面向设计师与创意工作者的 AI 视觉资产管理工具，用于更高效地整理、分类、检索和回顾视觉参考图片。

> 本仓库为项目展示版本，不包含生产环境源码、完整 Prompt、API Key 或私有用户数据。

## Overview

设计师在日常工作中会持续积累大量来自 Pinterest、小红书、Behance、产品网站等渠道的参考图片。

传统文件夹或收藏夹的主要问题是：

- 图片越来越多后难以快速找回
- 手动分类、打标签、写描述成本较高
- 不同来源的视觉素材缺乏统一管理方式
- 搜索通常依赖文件名，而不是视觉内容本身

Visual Island 希望把这些零散图片变成一个可持续积累的个人视觉资产库。

## Core Features

- 批量上传视觉参考图片
- AI 自动判断图片所属分类
- AI 自动生成检索标签
- AI 生成简短图片描述
- 分类浏览、搜索与筛选
- 图片详情编辑
- 游客体验模式
- 图片资产持久化管理

## AI Workflow

AI 不作为独立聊天机器人存在，而是嵌入图片整理流程中。

主要分为两个阶段：

**1. AI Category Sorting**

上传图片后，AI 根据图片的设计用途、视觉结构和主体内容，判断其所属分类。

**2. AI Metadata Completion**

分类完成后，再生成：

- 4 个高价值检索标签
- 1 句简短图片描述

用户仍然可以手动调整分类、标签和描述。

## Model Evaluation

在真实图片测试中，我使用约 25 张不同类型的视觉参考图片进行评测，并针对以下问题持续优化：

- 3D / CG 产品容易被误判为插画
- 含大量人物摄影的网页截图容易被误判为摄影
- 标签存在颜色重复和语义重复
- 标签过度描述画面内容，检索价值不足
- 描述文本过长

Prompt V2 将分类判断优先级调整为：

**设计用途 > 视觉结构 > 主体内容 > 表现媒介**

同时将标签策略调整为：

- AI 固定生成 4 个高价值标签
- 用户可手动补充最多 2 个
- 优先生成适合设计参考检索的标签
- 减少重复颜色、具体物体描述和低价值标签

## Performance Optimization

针对批量图片处理，我对 AI 调用流程进行了多轮优化，包括：

- 分类阶段缩小图片尺寸
- 分类与详细信息生成拆分
- 后台并发处理
- 请求失败重试
- 图片加载与缓存优化
- 避免不必要的 Storage 重复下载

在 20 张图片批量处理场景中，完整 AI 补全流程可控制在约 1–2 分钟内完成。

## Security & Cost Control

项目在 Demo 阶段也进行了基础安全设计：

- AI Prompt 仅保存在服务端
- DashScope API Key 不进入前端
- API 请求字段采用白名单校验
- 限制图片与请求体大小
- Supabase Row Level Security
- Storage Bucket 设置为 Private
- 图片使用 Signed URL
- 游客数据与正式账户数据隔离
- 游客 AI 使用次数限制
- 服务端基础 IP / 时间窗口保护

当前定位仍为求职作品 Demo，并非商业级 SaaS。

## My Role

我负责该项目从产品定义到 Demo 落地的完整过程，包括：

- 产品定位与需求设计
- 信息架构与核心流程设计
- UI / 交互设计
- AI Prompt 设计
- 模型评测与错误分析
- AI 流程优化
- 功能测试与 Bug 定位
- 性能优化
- AI API 安全与成本控制
- 使用 AI Coding 工具完成 Web Demo 落地

## Tech Stack

- JavaScript
- HTML / CSS
- Supabase
- Vercel
- DashScope
- Qwen Vision Model
- IndexedDB
- AI Coding Workflow

## Demo

Live Demo: Coming soon

Demo Video: Coming soon

## Screenshots

Product screenshots and workflow demonstrations will be added here.

## Status

Current status: Demo completed, preparing portfolio presentation.

## Future Work

- 商业级持久化 AI 配额系统
- 更完整的多用户权限体系
- 缩略图与图片 CDN 优化
- 更稳定的中国大陆访问方案
- Moodboard / 灵感板功能
