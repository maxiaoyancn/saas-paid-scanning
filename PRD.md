# 收费软件检测系统 PRD
## Product Requirements Document

---

## 1. 项目概述

### 1.1 项目背景
随着软件行业的发展，越来越多的软件采用"免费试用 + 后期收费"或"表面免费 + 隐性收费"的商业模式。典型案例如Anaconda，用户可以免费下载使用，但在商业环境中使用时会面临版权纠纷和法律风险。许多用户在不知情的情况下使用了这类软件，最终面临高额的授权费用或法律诉讼。

### 1.2 项目目标
构建一个智能检测系统，帮助个人用户和企业识别、监控和管理潜在的收费软件风险，避免意外的法律和财务损失。

### 1.3 目标用户
- **个人开发者**：需要了解所使用软件的授权风险
- **中小企业**：需要合规性检查，避免版权纠纷
- **大型企业**：需要全面的软件资产管理和合规监控
- **法务团队**：需要评估软件使用的法律风险
- **IT管理员**：需要监控和管理企业内部的软件使用情况

---

## 2. 功能需求

### 2.1 核心功能

#### 2.1.1 软件识别与检测
- **本地软件扫描**
  - 扫描用户计算机上已安装的软件
  - 识别软件版本、安装路径、使用频率
  - 检测软件的数字签名和来源
  
- **实时监控**
  - 监控新安装的软件
  - 检测软件的网络活动和数据传输
  - 识别软件的自动更新行为

- **深度分析**
  - 分析软件的许可证类型
  - 检测软件是否包含遥测或数据收集功能
  - 识别软件的商业使用限制

#### 2.1.2 风险评估系统
- **风险等级分类**
  - 🟢 低风险：完全开源或明确免费
  - 🟡 中风险：个人免费但商业收费
  - 🔴 高风险：存在隐性收费或法律风险
  - ⚫ 未知风险：缺乏足够信息判断

- **风险评估指标**
  - 许可证类型和限制条款
  - 商业使用政策
  - 历史收费案例
  - 用户举报和投诉记录
  - 公司商业模式分析

#### 2.1.3 数据库和知识库
- **软件信息数据库**
  - 维护常见软件的详细信息
  - 包含许可证、收费政策、使用限制
  - 定期更新软件版本和政策变化
  
- **案例库**
  - 收集实际的收费和法律纠纷案例
  - 分析软件公司的收费策略变化
  - 提供参考判例和处理建议

### 2.2 高级功能

#### 2.2.1 智能预警系统
- **行为模式分析**
  - 检测软件是否收集用户信息
  - 监控软件的网络通信模式
  - 识别可疑的数据上传行为

- **政策变化监控**
  - 监控软件公司的许可证政策变化
  - 及时通知用户政策更新
  - 提供政策变化的影响分析

#### 2.2.2 合规管理
- **企业版功能**
  - 生成合规报告
  - 软件资产清单管理
  - 许可证到期提醒
  - 成本预算和规划

- **批量处理**
  - 支持多台设备的批量扫描
  - 网络环境下的集中管理
  - 自动化的合规检查流程

### 2.3 用户界面功能

#### 2.3.1 桌面应用
- **主控制台**
  - 系统概览和风险统计
  - 快速扫描和深度扫描选项
  - 实时监控状态显示

- **详细报告**
  - 软件清单和风险评估结果
  - 可视化的风险分布图
  - 导出功能（PDF、Excel等）

#### 2.3.2 Web管理平台
- **企业管理后台**
  - 多设备统一管理
  - 用户权限管理
  - 策略配置和分发

- **数据分析**
  - 使用趋势分析
  - 风险热力图
  - 成本效益分析

---

## 3. 技术架构

### 3.1 系统架构
```
前端层
├── 桌面客户端 (Electron + React)
├── Web管理后台 (React)
└── 移动端App (React Native)

服务层
├── API网关
├── 用户认证服务
├── 扫描引擎服务
├── 风险评估服务
├── 数据分析服务
└── 通知服务

数据层
├── 软件信息数据库 (PostgreSQL)
├── 用户数据库 (PostgreSQL)
├── 日志存储 (Elasticsearch)
├── 缓存层 (Redis)
└── 文件存储 (MinIO/S3)
```

### 3.2 核心技术栈
- **后端**：Golang + Gin
- **前端**：React + TypeScript
- **桌面客户端**：Electron + React
- **数据库**：PostgreSQL + Redis
- **消息队列**：RabbitMQ/Kafka
- **容器化**：Docker + Kubernetes
- **监控**：Prometheus + Grafana

### 3.3 检测技术
- **静态分析**
  - 文件签名识别
  - 注册表分析
  - 配置文件解析
  
- **动态监控**
  - 进程监控
  - 网络流量分析
  - 系统调用跟踪

- **机器学习**
  - 异常行为检测
  - 软件分类模型
  - 风险评分算法

---

## 4. 产品功能详细设计

### 4.1 扫描引擎设计

#### 4.1.1 本地扫描模块
```python
# 扫描策略示例
class ScanStrategy:
    def scan_installed_software(self):
        # Windows: 注册表扫描
        # macOS: Applications文件夹 + brew list
        # Linux: 包管理器查询
        pass
    
    def analyze_software_signature(self, software_path):
        # 数字签名验证
        # 文件哈希计算
        # 版本信息提取
        pass
    
    def detect_network_behavior(self, process_id):
        # 网络连接监控
        # 数据传输分析
        # DNS查询记录
        pass
```

#### 4.1.2 风险评估算法
```python
class RiskAssessment:
    def calculate_risk_score(self, software_info):
        score = 0
        
        # 许可证风险 (40%)
        license_risk = self.assess_license_risk(software_info.license)
        score += license_risk * 0.4
        
        # 商业模式风险 (30%)
        business_risk = self.assess_business_model(software_info.company)
        score += business_risk * 0.3
        
        # 历史案例风险 (20%)
        history_risk = self.assess_historical_cases(software_info.name)
        score += history_risk * 0.2
        
        # 行为风险 (10%)
        behavior_risk = self.assess_behavior_pattern(software_info.behavior)
        score += behavior_risk * 0.1
        
        return min(score, 100)
```

### 4.2 数据库设计

#### 4.2.1 软件信息表
```sql
CREATE TABLE software_database (
    id SERIAL PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    vendor VARCHAR(255),
    version VARCHAR(100),
    license_type VARCHAR(100),
    commercial_use_allowed BOOLEAN,
    individual_use_free BOOLEAN,
    risk_level INTEGER, -- 0-100
    last_policy_change DATE,
    data_collection BOOLEAN,
    network_activity_level INTEGER,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

#### 4.2.2 用户扫描记录表
```sql
CREATE TABLE scan_results (
    id SERIAL PRIMARY KEY,
    user_id INTEGER REFERENCES users(id),
    software_id INTEGER REFERENCES software_database(id),
    detected_version VARCHAR(100),
    installation_path TEXT,
    usage_frequency INTEGER,
    risk_score INTEGER,
    scan_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    status VARCHAR(50) -- 'active', 'removed', 'updated'
);
```

### 4.3 API设计

#### 4.3.1 扫描相关API
```yaml
# 启动扫描
POST /api/v1/scan/start
{
  "scan_type": "quick|full|custom",
  "target_paths": ["/Applications", "C:\\Program Files"],
  "scan_options": {
    "include_system_software": false,
    "deep_analysis": true,
    "network_monitoring": true
  }
}

# 获取扫描结果
GET /api/v1/scan/results/{scan_id}
{
  "scan_id": "uuid",
  "status": "completed",
  "total_software": 156,
  "high_risk_count": 3,
  "medium_risk_count": 12,
  "results": [...]
}

# 获取软件详细信息
GET /api/v1/software/{software_id}/details
{
  "software_id": 123,
  "name": "Anaconda",
  "risk_assessment": {
    "score": 75,
    "level": "high",
    "reasons": [
      "商业使用需要付费许可证",
      "检测到数据收集行为",
      "存在历史收费案例"
    ]
  }
}
```

---

## 5. 用户体验设计

### 5.1 主界面设计

#### 5.1.1 仪表板
- **风险概览卡片**
  - 总软件数量
  - 高风险软件数量
  - 合规状态
  - 最近扫描时间

- **快速操作区**
  - 一键扫描按钮
  - 实时监控开关
  - 设置入口

#### 5.1.2 扫描结果页面
- **软件列表**
  - 风险等级标识（颜色编码）
  - 软件名称和版本
  - 安装路径
  - 最后使用时间
  - 风险描述

- **筛选和排序**
  - 按风险等级筛选
  - 按软件类别筛选
  - 按安装时间排序

### 5.2 交互流程

#### 5.2.1 首次使用流程
1. 欢迎页面和功能介绍
2. 选择扫描类型（快速/完整）
3. 扫描进度显示
4. 结果展示和风险说明
5. 建议操作指导

#### 5.2.2 日常使用流程
1. 查看风险概览
2. 处理高风险软件
3. 查看详细报告
4. 设置监控规则
5. 导出合规报告

---

## 6. 商业模式

### 6.1 产品版本规划

#### 6.1.1 免费版 (Community Edition)
- 基础软件扫描功能
- 最多监控50个软件
- 基础风险评估
- 社区支持

#### 6.1.2 专业版 (Professional Edition) - ¥299/年
- 无限制软件监控
- 实时监控和预警
- 详细合规报告
- 邮件和短信通知
- 优先技术支持

#### 6.1.3 企业版 (Enterprise Edition) - ¥999/年起
- 多设备集中管理
- 批量部署和配置
- API集成支持
- 定制化报告
- 专属客户经理
- SLA保障

### 6.2 盈利模式
- **订阅收费**：按年收费的SaaS模式
- **企业定制**：大型企业的定制化解决方案
- **API服务**：为其他软件提供风险检测API
- **咨询服务**：软件合规咨询和培训服务

---

## 7. 实施计划

### 7.1 开发阶段

#### Phase 1 (3个月) - MVP版本
- [ ] 基础扫描引擎开发
- [ ] 核心数据库构建
- [ ] 简单的桌面客户端
- [ ] 基础风险评估算法
- [ ] 50个常见软件的数据收集

#### Phase 2 (2个月) - 功能完善
- [ ] Web管理后台
- [ ] 实时监控功能
- [ ] 报告导出功能
- [ ] 用户管理系统
- [ ] 扩展软件数据库到500个

#### Phase 3 (2个月) - 企业功能
- [ ] 多设备管理
- [ ] API接口开发
- [ ] 批量部署工具
- [ ] 高级分析功能
- [ ] 机器学习模型优化

#### Phase 4 (持续) - 运营优化
- [ ] 数据库持续更新
- [ ] 用户反馈处理
- [ ] 性能优化
- [ ] 新功能迭代
- [ ] 市场推广

### 7.2 技术里程碑
- **Week 1-2**：技术架构设计和环境搭建
- **Week 3-6**：扫描引擎核心功能开发
- **Week 7-10**：数据库设计和API开发
- **Week 11-12**：前端界面开发和集成测试

---

## 8. 风险和挑战

### 8.1 技术风险
- **检测准确性**：避免误报和漏报
- **性能优化**：大量软件扫描的性能问题
- **兼容性**：跨平台兼容性挑战
- **安全性**：用户隐私和数据安全

### 8.2 业务风险
- **法律风险**：避免与软件厂商的法律纠纷
- **数据准确性**：确保软件信息的及时更新
- **市场竞争**：大厂可能推出类似产品
- **用户接受度**：教育用户认识软件合规的重要性

### 8.3 应对策略
- 建立专业的法律顾问团队
- 与开源社区合作，共同维护数据库
- 注重产品差异化和用户体验
- 加强用户教育和市场推广

---

## 9. 成功指标

### 9.1 产品指标
- **用户增长**：月活跃用户数
- **留存率**：用户留存率和使用频率
- **检测准确率**：风险识别的准确性
- **响应时间**：扫描和分析的性能指标

### 9.2 商业指标
- **收入增长**：订阅收入和续费率
- **客户满意度**：NPS评分和用户反馈
- **市场份额**：在软件合规领域的地位
- **成本控制**：获客成本和运营效率

### 9.3 社会价值
- 帮助用户避免的法律风险金额
- 提升软件行业的透明度
- 促进开源软件的发展
- 推动软件合规意识的普及

---

## 10. 附录

### 10.1 典型案例分析

#### Anaconda案例
- **问题**：个人免费，商业使用需付费，但界限模糊
- **风险**：企业用户面临追缴授权费
- **检测要点**：识别商业环境使用，监控网络活动

#### JetBrains系列
- **问题**：试用期后需购买，但可能存在破解使用
- **风险**：版权侵权和法律诉讼
- **检测要点**：验证许可证有效性，检测破解特征

#### Oracle产品
- **问题**：复杂的许可证条款，易产生合规风险
- **风险**：高额的审计费用和罚款
- **检测要点**：分析使用场景，评估许可证需求

### 10.2 竞品分析
- **Black Duck**：专业的开源软件合规平台
- **WhiteSource**：软件组成分析工具
- **Snyk**：开发者安全平台
- **FOSSA**：开源许可证合规工具

### 10.3 技术参考
- 软件指纹识别技术
- 许可证文本分析算法
- 网络行为监控技术
- 机器学习在风险评估中的应用

---

*文档版本：v1.0*  
*最后更新：2024年12月*  
*负责人：产品团队*
