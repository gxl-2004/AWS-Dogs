# AWS Nginx Dogs Service
这是一个基于 Nginx 的静态页面服务，通过 Docker 容器化部署，并使用 AWS CodeBuild 自动构建镜像并推送至 Amazon ECR。

## 项目功能
- 运行 Nginx 服务，提供静态网页展示
- 页面随机展示 10 张狗狗图片
- 支持通过 /dogs 路径访问页面
- 集成 AWS CLI，支持云服务交互

## 技术栈
- Nginx
- Docker
- HTML / JavaScript
- AWS CodeBuild
- AWS ECR
- AWS S3（图片资源存储）

## 目录文件说明
- Dockerfile：构建 Docker 镜像的配置文件
- buildspec.yml：AWS CodeBuild 自动构建配置
- default.conf：Nginx 服务配置文件
- index.html：前端展示页面

## 构建与运行
### 本地构建 Docker 镜像
docker build -t dogs .

### 本地运行容器
docker run -d -p 80:80 dogs

### 访问服务
http://localhost

http://localhost/dogs

## AWS 自动化部署
本项目通过 AWS CodeBuild 自动完成：
1. 登录 ECR
2. 构建 Docker 镜像
3. 推送镜像至 ECR
4. 生成镜像定义文件用于 ECS 部署

## 服务端口
- 容器暴露端口：80
- Nginx 监听端口：80
