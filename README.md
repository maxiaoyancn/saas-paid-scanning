# 收费软件检测系统
## SaaS Paid Software Scanning System

一个智能的收费软件检测和合规管理系统，帮助个人用户和企业识别、监控和管理潜在的软件授权风险。

---

## 🎯 项目概述

### 核心功能
- 🔍 **智能扫描检测** - 自动识别系统中的收费软件
- ⚠️ **风险评估预警** - AI驱动的软件风险评分系统  
- 📊 **合规管理报告** - 生成详细的合规分析报告
- 🔔 **实时监控通知** - 监控软件安装和政策变化
- 🏢 **企业级管理** - 支持多设备集中管理

### 技术栈
- **后端**: Golang + Gin + GORM + PostgreSQL + Redis
- **前端**: React + TypeScript + Ant Design
- **桌面端**: Electron + React
- **部署**: Docker + Kubernetes + CI/CD

---

## 📋 文档目录

- [📖 产品需求文档 (PRD)](./PRD.md) - 详细的产品规划和功能需求
- [🏗️ 系统架构文档](./架构文档.md) - 完整的技术架构设计
- [🔧 技术栈说明](./技术栈说明.md) - 技术选型和依赖说明
- [🚀 快速开始指南](./快速开始.md) - 开发环境搭建和部署指南

---

## 🚀 快速开始

### 环境要求
- Golang 1.21+
- Node.js 18+
- Docker & Docker Compose
- PostgreSQL 15+
- Redis 7+

### 一键启动
```bash
# 克隆项目
git clone https://github.com/your-org/saas-scanning-system.git
cd saas-scanning-system

# 启动开发环境
make dev-up

# 访问系统
# 前端: http://localhost:3000
# API: http://localhost:8080
# 文档: http://localhost:8080/swagger
```

详细说明请参考 [快速开始指南](./快速开始.md)

---

## 🏗️ 系统架构

```
┌─────────────────────────────────────────┐
│            客户端层                      │
├─────────────┬─────────────┬─────────────┤
│  桌面客户端  │  Web管理后台 │   移动端App  │
│ (Electron)  │  (React)    │ (React Native)│
└─────────────┴─────────────┴─────────────┘
                     │
┌─────────────────────────────────────────┐
│              网关层                      │
│    API Gateway + Load Balancer         │
└─────────────────────────────────────────┘
                     │
┌─────────────────────────────────────────┐
│              微服务层                    │
├──────┬──────┬──────┬──────┬────────────┤
│ 认证 │ 扫描 │ 风险 │ 分析 │    通知    │
│ 服务 │ 服务 │ 服务 │ 服务 │    服务    │
└──────┴──────┴──────┴──────┴────────────┘
                     │
┌─────────────────────────────────────────┐
│              数据层                      │
├──────┬──────┬──────┬──────┬────────────┤
│PostgreSQL│Redis │ElasticSearch│MinIO│RabbitMQ│
└──────┴──────┴──────┴──────┴────────────┘
```

---

## 📊 项目状态

### 开发进度
- [x] 📋 需求分析和架构设计
- [x] 🔧 技术栈选型和环境配置  
- [ ] 🏗️ 后端微服务开发 (进行中)
- [ ] 💻 前端界面开发 (计划中)
- [ ] 📱 桌面客户端开发 (计划中)
- [ ] 🧪 测试和质量保证 (计划中)
- [ ] 🚀 部署和运维配置 (计划中)

### 版本规划
- **v0.1.0** - MVP版本 (基础扫描功能)
- **v0.2.0** - 完整功能版本 (风险评估、报告)
- **v1.0.0** - 生产就绪版本 (企业功能、监控)

---

## 🤝 贡献

欢迎贡献代码、报告问题或提出建议！

### 贡献方式
1. Fork 本项目
2. 创建功能分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 创建 Pull Request

### 开发规范
- 遵循 [Go代码规范](https://github.com/golang/go/wiki/CodeReviewComments)
- 使用 [Conventional Commits](https://www.conventionalcommits.org/) 提交格式
- 确保测试覆盖率 > 80%
- 更新相关文档

---

## 📄 许可证

本项目采用 MIT 许可证 - 查看 [LICENSE](LICENSE) 文件了解详情

---

## 📞 联系方式

- 项目维护者：开发团队
- 邮箱：dev-team@example.com
- 问题反馈：[GitHub Issues](https://github.com/your-org/saas-scanning-system/issues)

---

*最后更新：2024年12月*
