

# 数据结构课程设计：基于大模型的旅游推荐系统

基于Django框架开发的旅游推荐系统，集成了景点浏览、食物推荐、日记分享等功能。系统使用多种数据结构算法优化推荐效率。

<!-- PROJECT SHIELDS -->

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]

<!-- PROJECT LOGO -->
<br />

<p align="center">
  <a href="https://github.com/NARUTO-2117/travel-system-llm/">
    <img src="images/logo.png" alt="Logo" width="80" height="80">
  </a>

  <h3 align="center">旅游推荐系统</h3>
  <p align="center">
    一个基于Django的智能旅游推荐平台
    <br />
    <a href="https://github.com/NARUTO-2117/travel-system-llm"><strong>探索本项目的文档 »</strong></a>
    <br />
    <br />
    <a href="https://github.com/NARUTO-2117/travel-system-llm">查看Demo</a>
    ·
    <a href="https://github.com/NARUTO-2117/travel-system-llm/issues">报告Bug</a>
    ·
    <a href="https://github.com/NARUTO-2117/travel-system-llm/issues">提出新特性</a>
  </p>

</p>


 本篇README.md面向开发者
 
## 目录

- [数据结构课程设计：基于大模型的旅游推荐系统](#数据结构课程设计基于大模型的旅游推荐系统)
  - [目录](#目录)
    - [上手指南](#上手指南)
      - [开发前的配置要求](#开发前的配置要求)
      - [安装步骤](#安装步骤)
    - [项目特性](#项目特性)
    - [文件目录说明](#文件目录说明)
    - [开发的架构](#开发的架构)
    - [部署](#部署)
    - [使用到的框架](#使用到的框架)
    - [贡献者](#贡献者)
      - [如何参与开源项目](#如何参与开源项目)
    - [版本控制](#版本控制)
    - [作者](#作者)
    - [版权说明](#版权说明)
    - [鸣谢](#鸣谢)

### 上手指南

请将所有链接中的“NARUTO-2117/travel-system-llm”改为“your_github_name/your_repository”



#### 开发前的配置要求

1. Python 3.8+
2. Django 3.2+
3. SQLite 3

#### 安装步骤

1. 克隆项目

```sh
git clone https://github.com/NARUTO-2117/travel-system-llm.git
cd travel-system-llm-main/Tourism-development-system/Tour_Of_YLJ
```

2. 安装依赖

```sh
pip install -r requirements.txt
```

3. 数据库迁移

```sh
python manage.py makemigrations
python manage.py migrate
```

4. 生成测试数据（可选）

```sh
python generate_diaries.py
python scripts/generate_realistic_data.py
```

5. 启动服务器

```sh
python manage.py runserver
```

访问 http://127.0.0.1:8000 查看应用

### 项目特性

- **景点管理**: 支持多种类别景点的展示和管理
- **智能食物推荐**: 基于快速选择和堆排序算法的美食推荐系统
- **用户日记**: 支持日记发布、评论、点赞功能
- **用户系统**: 完整的用户注册、登录、个人中心
- **数据压缩**: 日记内容使用zlib压缩存储
- **响应式设计**: 适配移动端和桌面端的用户界面

### 文件目录说明

```
Tour_Of_YLJ/
├── db.sqlite3                    # SQLite数据库文件
├── manage.py                     # Django管理脚本
├── requirements.txt              # Python依赖包
├── start_server.bat             # Windows启动脚本
├── generate_diaries.py           # 日记数据生成脚本
├── import_diaries.py             # 日记导入脚本
├── sync_descriptions.py          # 描述同步脚本
├── update_diaries.py             # 日记更新脚本
├── media/                        # 媒体文件目录
│   ├── attraction_covers/        # 景点封面图片
│   ├── diaries/                  # 日记相关文件
│   └── diary_images/             # 日记图片
├── scripts/                      # 脚本目录
│   └── generate_realistic_data.py # 真实数据生成脚本
├── Tour_Of_YLJ/                  # Django项目主目录
│   ├── __init__.py
│   ├── asgi.py
│   ├── settings.py               # 项目设置
│   ├── urls.py                   # URL配置
│   └── wsgi.py
├── TourismSystem/                # 主应用目录
│   ├── __init__.py
│   ├── admin.py                  # 后台管理
│   ├── apps.py
│   ├── food_algorithms.py        # 食物推荐算法
│   ├── forms.py                  # 表单定义
│   ├── models.py                 # 数据模型
│   ├── settings.py
│   ├── tests.py
│   ├── urls.py                   # 应用URL配置
│   ├── views.py                  # 视图函数
│   ├── migrations/               # 数据库迁移文件
│   ├── static/                   # 静态文件
│   │   └── TourismSystem/
│   │       ├── css/              # 样式文件
│   │       ├── js/               # JavaScript文件
│   │       └── data/             # JSON数据文件
│   └── templates/                # HTML模板
│       └── TourismSystem/
└── users/                        # 用户应用目录
    ├── __init__.py
    ├── admin.py
    ├── apps.py
    ├── models.py
    ├── tests.py
    ├── urls.py
    └── views.py
```





### 开发的架构

本项目采用Django MTV架构：

- **Model**: 定义数据模型（景点、美食、日记、用户等）
- **Template**: HTML模板实现前端展示
- **View**: 处理业务逻辑和用户请求

核心算法：
- 食物推荐使用快速选择算法和堆排序优化性能
- 日记内容采用zlib压缩存储
- 景点数据支持树形结构存储

### 部署

1. 配置生产环境设置（修改settings.py中的DEBUG=False等）
2. 使用Nginx + Gunicorn部署
3. 配置静态文件服务
4. 设置数据库备份

### 使用到的框架

- [Django](https://www.djangoproject.com/) - Web框架
- [Pillow](https://python-pillow.org/) - 图像处理
- [django-filter](https://django-filter.readthedocs.io/) - 查询过滤
- [django-cors-headers](https://github.com/adamchainz/django-cors-headers) - CORS处理

### 贡献者

请阅读**CONTRIBUTING.md** 查阅为该项目做出贡献的开发者。

#### 如何参与开源项目

贡献使开源社区成为一个学习、激励和创造的绝佳场所。你所作的任何贡献都是**非常感谢**的。


1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request



### 版本控制

该项目使用Git进行版本管理。您可以在repository参看当前可用版本。

### 作者

xxx@xxxx

知乎:xxxx  &ensp; qq:xxxxxx    

 *您也可以在贡献者名单中参看所有参与该项目的开发者。*

### 版权说明

该项目签署了MIT 授权许可，详情请参阅 [LICENSE.txt](https://github.com/NARUTO-2117/travel-system-llm/blob/master/LICENSE.txt)

### 鸣谢

- [Django](https://www.djangoproject.com/)
- [Bootstrap](https://getbootstrap.com)
- [jQuery](https://jquery.com)
- [GitHub Emoji Cheat Sheet](https://www.webpagefx.com/tools/emoji-cheat-sheet)
- [Img Shields](https://shields.io)
- [Choose an Open Source License](https://choosealicense.com)
- [GitHub Pages](https://pages.github.com)

<!-- links -->
[your-project-path]:NARUTO-2117/travel-system-llm
[contributors-shield]: https://img.shields.io/github/contributors/NARUTO-2117/travel-system-llm.svg?style=flat-square
[contributors-url]: https://github.com/NARUTO-2117/travel-system-llm/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/NARUTO-2117/travel-system-llm.svg?style=flat-square
[forks-url]: https://github.com/NARUTO-2117/travel-system-llm/network/members
[stars-shield]: https://img.shields.io/github/stars/NARUTO-2117/travel-system-llm.svg?style=flat-square
[stars-url]: https://github.com/NARUTO-2117/travel-system-llm/stargazers
[issues-shield]: https://img.shields.io/github/issues/NARUTO-2117/travel-system-llm.svg?style=flat-square
[issues-url]: https://img.shields.io/github/issues/NARUTO-2117/travel-system-llm.svg
[license-shield]: https://img.shields.io/github/license/NARUTO-2117/travel-system-llm.svg?style=flat-square
[license-url]: https://github.com/NARUTO-2117/travel-system-llm/blob/master/LICENSE.txt



