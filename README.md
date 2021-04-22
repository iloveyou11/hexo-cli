## 使用本项目hexo-cli提供的脚手架搭建流程
### 修改配置文件`_config.yml`

```yml
deploy:
  type: git
  repo: https://github.com/iloveyou11/iloveyou11.github.io.git # 这里填写github的项目地址，记得加.git
  branch: master
```

- 分别运行`hexo g` 、`hexo s`，可以在https://[yourname].github.io/查看博客（在下方会讲命令的具体作用）
- 可以修改`source/_posts`下的博客文档，或者新增博客，可预览效果

### 主题更换
需要在[主题官网](https://hexo.io/themes/)选择好主题，找到对应的 github 仓库，`git clone [theme path] themes/[theme name]`安装到本项目的 themes 文件夹下，并修改\_config.yml 配置文件中 theme（名字与你命名的主题文件夹名字相同）：

```yml
theme: miho
```

分别运行

```sh
hexo clean  #清除缓存
hexo g   #相当于hexo generate，生成博客
hexo d   #相当于hexo deploy，部署博客
```

或者一次运行：

```sh
hexo clean && hexo g && hexo d
```

打开你的博客地址即可看到效果

### 书写博客

1. 关于博客书写
`hexo n "博客名字"`，会在`source/_posts`文件夹下生成 markdown 文件，使用 markdown 语法书写博客即可，建议使用markdown编辑器编写。

2. 博客的格式
博客的大体可以采用以下格式（不同主题格式或许有些不同，可以自行查阅相关文档）：

```markdown
---
title: Hello World
date: 2019-07-25
author: XXX
categories: XXX
tags:
  - Android
comments: true
cover_picture: /images/banner.jpg
---

这里写博客开头部分内容

# 如果添加下行语句，文章会自动生成“更多”按钮，点击后 more 后面的内容才会显示

<!-- more -->

这里写后续的博客内容
```

3. 关于图片
如果采用本地项目文件夹存储图片，每次打开博客会加载大量的图片，会导致性能有所下降，建议使用图床存储，如[七牛](https://www.qiniu.com/) 或 [贴图库](http://www.tietuku.com/) ，在文章中直接采用外链引入图片。

**[坑]**： 如果 hexo g 生成的文件缺少 index.html 和 archive，部署后打开博客会出现 404 的错误说找不到 index,html 文件,在 github 仓库中打开确实没有.造成这个问题的原因是缺少相应的 npm 包，输入命令`npm ls --depth 0`，安装好缺少的包重新发布即可。

## 从零开始的搭建流程

### 项目初始化
- 安装 git，申请 github 账号，生成 ssh 密钥，在 github 新建 new SSH Key
- 在 github 新建个人仓库用户名，取名为**''用户名.github.io''**这个用户名使用你的 GitHub 帐号名称代替，这个是固定写法
- 安装 nodejs
- 安装 hexo `npm install -g hexo-cli`
- 初始化博客 `hexo init [name]`创建博客项目
- 为了检测网站别按顺序输入以下命令：`hexo g` 、`hexo s`，打开 localhost:4000 查看网站是否成功显示
- 关联 github，安装包`npm install hexo-deployer-git --save`，修改\_config.yml 配置文件

```yml
deploy:
  type: git
  repo: https://github.com/name/name.github.io.git  #记得加.git
  branch: master
```

分别运行`hexo g` 、`hexo s`，在https://[yourname].github.io/查看博客（在下方会讲命令的具体作用）。

### 主题更换
需要在[主题官网](https://hexo.io/themes/)选择好主题，找到对应的 github 仓库，`git clone [theme path] themes/[theme name]`安装到本项目的 themes 文件夹下，并修改\_config.yml 配置文件中 theme（名字与你命名的主题文件夹名字相同）：

```yml
theme: miho
```

分别运行

```sh
hexo clean  #清除缓存
hexo g   #相当于hexo generate，生成博客
hexo d   #相当于hexo deploy，部署博客
```

或者一次运行：

```sh
hexo clean && hexo g && hexo d
```

打开你的博客地址即可看到效果

### 书写博客

1. 关于博客书写
`hexo n "博客名字"`，会在`source/_posts`文件夹下生成 markdown 文件，使用 markdown 语法书写博客即可，建议使用markdown编辑器编写。

2. 博客的格式
博客的大体可以采用以下格式（不同主题格式或许有些不同，可以自行查阅相关文档）：

```markdown
---
title: Hello World
date: 2019-07-25
author: XXX
categories: XXX
tags:
  - Android
comments: true
cover_picture: /images/banner.jpg
---

这里写博客开头部分内容

# 如果添加下行语句，文章会自动生成“更多”按钮，点击后 more 后面的内容才会显示

<!-- more -->

这里写后续的博客内容
```

3. 关于图片
如果采用本地项目文件夹存储图片，每次打开博客会加载大量的图片，会导致性能有所下降，建议使用图床存储，如[七牛](https://www.qiniu.com/) 或 [贴图库](http://www.tietuku.com/) ，在文章中直接采用外链引入图片。

**[坑]**： 如果 hexo g 生成的文件缺少 index.html 和 archive，部署后打开博客会出现 404 的错误说找不到 index,html 文件,在 github 仓库中打开确实没有.造成这个问题的原因是缺少相应的 npm 包，输入命令`npm ls --depth 0`，安装好缺少的包重新发布即可。

### hexo 常用命令

```sh
npm install hexo -g #全局安装Hexo
npm update hexo -g #升级hexo
hexo init #初始化项目
hexo n "name" <=> hexo new "name" #新建名为name的文章
hexo g <=> hexo generate #生成博客
hexo s <=> hexo server #启动服务，本地预览效果
hexo d <=> hexo deploy #部署博客
```