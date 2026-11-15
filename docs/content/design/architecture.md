---
title: 架构边界
weight: 40
---

**状态：设计讨论稿；产品方案尚未确认或实现。**

## 当前可验证边界

```text
Markdown + docs/hugo.yaml + docs/go.mod/go.sum
                 ↓ Hugo Extended + OINK
          docs/public/（忽略的构建产物）
                 ↓ 经评审后的 Pages 工作流
              GitHub Pages
```

文档站为静态内容，不需要业务后端、数据库、登录或运行时秘密。主题通过 Hugo Module 引入，构建不接入业务应用。

## 业务架构待确认

客户端形态、服务边界、接口协议、数据存放、身份与授权、外部依赖、性能目标均未确定。
待目标场景确认后，再比较选项、责任边界与失败处理；本页不是既有系统架构说明。
