[中文说明 (Chinese README)](README_CN.md)

# Social-X

## Overview

Social-X is a cutting-edge hybrid social network system, integrating multiple database paradigms and providing a full-stack solution for large-scale social platforms. The project consists of three main modules:

- **Backend**: A Spring Boot-based backend service for user/content management, authentication, and more.
- **Frontend**: A modern React-based web application for end users and administrators.
- **Detection**: An AI-powered image and text content moderation service.

---

## Project Structure

```
social-x/
├── social-x-backend/      # Backend service (Java, Spring Boot)
├── social-x-frontend/     # Frontend web app (React, Ant Design Pro)
├── social-x-detection/    # Content detection service (Python, AI)
├── .gitmodules            # Git submodules config
└── README.md              # Project documentation
```

---

## 1. Backend: social-x-backend

A modular Spring Boot backend providing core social platform features.

### Features

- User management, authentication (Sa-Token)
- Content management (posts, comments, media)
- Notification system
- Modular architecture (common, infra, component, runner, test)
- API documentation (Knife4j)

### Tech Stack

- Java 17, Spring Boot 2.7.18
- MyBatis, Redis, MySQL
- Sa-Token, Knife4j, Hutool, MapStruct, Easy-Captcha

### Directory Structure

```
social-x-backend/
├── app-common/      # Common utilities
├── app-infra/       # Infrastructure (DB, cache, MQ)
├── app-component/   # Business logic
├── app-runner/      # Main application entry
├── app-test/        # Tests
├── run.sh           # Startup script
├── Dockerfile       # Docker build
└── pom.xml          # Maven config
```

### Quick Start

1. **Requirements**: JDK 17+, Maven 3.6+, MySQL 8.0+, Redis 6.0+
2. **Configure**: Create DB, import schema, set up `application-local.yml` in `app-runner/src/main/resources/`
3. **Build**:
   ```bash
   ./mvnw clean package -Plocal -Dmaven.test.skip=true
   ```
4. **Run**:
   ```bash
   ./run.sh
   # or
   java -jar app-runner/target/social-x.jar
   ```
5. **API Docs**: http://localhost:8080/doc.html

---

## 2. Frontend: social-x-frontend

A modern web frontend for Social-X, built with React and Ant Design Pro.

### Features

- User and admin interfaces
- Markdown & emoji support
- Responsive design
- TypeScript, ESLint, Prettier, Git hooks

### Tech Stack

- React 18, TypeScript, UmiJS, Ant Design Pro
- Monaco Editor, Markdown, Emoji

### Directory Structure

```
social-x-frontend/
├── config/         # UmiJS config
├── src/            # Source code
│   ├── components/ # Shared components
│   ├── constants/  # Constants
│   ├── hooks/      # Custom hooks
│   ├── pages/      # Pages
│   ├── services/   # API services
│   ├── app.tsx     # App entry
│   └── global.tsx  # Global config
├── public/         # Static assets
├── nginx.conf      # Nginx config
└── package.json    # Dependencies
```

### Quick Start

1. **Requirements**: Node.js >= 12, npm >= 6
2. **Install**:
   ```bash
   npm install
   ```
3. **Run**:
   ```bash
   npm run dev
   # or for test/preprod
   npm run start:test
   npm run start:pre
   ```
4. **Build**:
   ```bash
   npm run build
   ```
5. **Preview**:
   ```bash
   npm run preview
   ```
6. **Deploy**: Use `nginx.conf` for production deployment

---

## 3. Detection: social-x-detection

A Python-based AI service for image and text moderation, supporting multi-modal content analysis.

### Features

- Image classification (normal, porn, sensitive)
- OCR text extraction (EasyOCR)
- Sensitive word detection (BERT, custom dictionary)
- RESTful API (Flask)
- Model evaluation and metrics

### Tech Stack

- Python 3.8+, Flask
- torch, torchvision, onnx, onnxruntime
- transformers, easyocr, numpy, Pillow

### Directory Structure

```
social-x-detection/
├── core/           # Main detection logic
│   ├── main.py     # Entry point
│   ├── requirements.txt # Dependencies
│   ├── model/      # Model files
│   ├── sensitive/  # Sensitive word dict
│   └── ...
├── train/          # Training scripts
├── assets/         # Images, diagrams
└── README.md
```

### Quick Start

1. **Requirements**: Python 3.8+
2. **Setup**:
   ```bash
   cd social-x-detection/core
   python3 -m venv ./venv
   source ./venv/bin/activate
   pip install -r requirements.txt
   ```
3. **Run**:
   ```bash
   python3 main.py
   ```
4. **API**: `POST /check_img` (see module README for details)

---

## Development & Contribution

- Clone with submodules: `git clone --recurse-submodules ...`
- Update submodules: `git submodule update --remote --merge`
- Each module has its own README for more details
- PRs and issues welcome!

---

## License

MIT License. See each module for details.
