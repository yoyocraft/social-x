[English Version (英文版)](README.md)

# Social-X

## 项目简介

Social-X 是一个面向大规模社交平台的混合型社交网络系统，集成多种数据库范式，提供全栈解决方案。项目包含三个主要模块：

- **后端**：基于 Spring Boot 的后端服务，负责用户、内容管理、认证等。
- **前端**：现代化 React Web 应用，面向终端用户和管理员。
- **检测**：AI 驱动的图片与文本内容审核服务。

---

## 项目结构

```
social-x/
├── social-x-backend/      # 后端服务（Java, Spring Boot）
├── social-x-frontend/     # 前端 Web 应用（React, Ant Design Pro）
├── social-x-detection/    # 内容检测服务（Python, AI）
├── .gitmodules            # 子模块配置
└── README.md              # 项目文档
```

---

## 1. 后端：social-x-backend

一个模块化的 Spring Boot 后端，提供社交平台核心功能。

### 功能

- 用户管理、认证（Sa-Token）
- 内容管理（帖子、评论、媒体）
- 消息通知系统
- 模块化架构（common, infra, component, runner, test）
- API 文档（Knife4j）

### 技术栈

- Java 17, Spring Boot 2.7.18
- MyBatis, Redis, MySQL
- Sa-Token, Knife4j, Hutool, MapStruct, Easy-Captcha

### 目录结构

```
social-x-backend/
├── app-common/      # 公共工具
├── app-infra/       # 基础设施（数据库、缓存、消息队列）
├── app-component/   # 业务逻辑
├── app-runner/      # 应用主入口
├── app-test/        # 测试
├── run.sh           # 启动脚本
├── Dockerfile       # Docker 构建
└── pom.xml          # Maven 配置
```

### 快速开始

1. **环境要求**：JDK 17+，Maven 3.6+，MySQL 8.0+，Redis 6.0+
2. **配置**：创建数据库并导入表结构，在 `app-runner/src/main/resources/` 下配置 `application-local.yml`
3. **编译**：
   ```bash
   ./mvnw clean package -Plocal -Dmaven.test.skip=true
   ```
4. **启动**：
   ```bash
   ./run.sh
   # 或
   java -jar app-runner/target/social-x.jar
   ```
5. **API 文档**：http://localhost:8080/doc.html

---

## 2. 前端：social-x-frontend

基于 React 和 Ant Design Pro 的现代化 Web 前端。

### 功能

- 用户与管理后台界面
- Markdown 与表情支持
- 响应式设计
- TypeScript、ESLint、Prettier、Git hooks

### 技术栈

- React 18, TypeScript, UmiJS, Ant Design Pro
- Monaco Editor, Markdown, Emoji

### 目录结构

```
social-x-frontend/
├── config/         # UmiJS 配置
├── src/            # 源码
│   ├── components/ # 公共组件
│   ├── constants/  # 常量
│   ├── hooks/      # 自定义 hooks
│   ├── pages/      # 页面
│   ├── services/   # API 服务
│   ├── app.tsx     # 应用入口
│   └── global.tsx  # 全局配置
├── public/         # 静态资源
├── nginx.conf      # Nginx 配置
└── package.json    # 依赖
```

### 快速开始

1. **环境要求**：Node.js >= 12，npm >= 6
2. **安装依赖**：
   ```bash
   npm install
   ```
3. **启动开发环境**：
   ```bash
   npm run dev
   # 测试/预发环境
   npm run start:test
   npm run start:pre
   ```
4. **构建生产包**：
   ```bash
   npm run build
   ```
5. **预览生产包**：
   ```bash
   npm run preview
   ```
6. **部署**：生产环境可使用 `nginx.conf`

---

## 3. 检测：social-x-detection

基于 Python 的 AI 内容审核服务，支持多模态内容分析。

### 功能

- 图片分类（正常、涉黄、敏感）
- OCR 文本提取（EasyOCR）
- 敏感词检测（BERT、定制词库）
- RESTful API（Flask）
- 模型评估与指标

### 技术栈

- Python 3.8+, Flask
- torch, torchvision, onnx, onnxruntime
- transformers, easyocr, numpy, Pillow

### 目录结构

```
social-x-detection/
├── core/           # 检测核心逻辑
│   ├── main.py     # 入口
│   ├── requirements.txt # 依赖
│   ├── model/      # 模型文件
│   ├── sensitive/  # 敏感词库
│   └── ...
├── train/          # 训练脚本
├── assets/         # 图片、图表
└── README.md
```

### 快速开始

1. **环境要求**：Python 3.8+
2. **环境搭建**：
   ```bash
   cd social-x-detection/core
   python3 -m venv ./venv
   source ./venv/bin/activate
   pip install -r requirements.txt
   ```
3. **运行**：
   ```bash
   python3 main.py
   ```
4. **API**：`POST /check_img`（详见模块 README）

---

## 开发与贡献

- 克隆带子模块：`git clone --recurse-submodules ...`
- 更新子模块：`git submodule update --remote --merge`
- 各模块有独立 README，详见各自目录
- 欢迎 PR 与 issue！

---

## 许可证

MIT License，详见各模块 LICENSE。
