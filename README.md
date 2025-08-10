<<<<<<< HEAD
**前言：在Github上部署自己的博客网站，首先的有自己的Gighub账号。**

# 环境准备

## 安装Ruby。Jekyll需要Ruby环境来运行，自己的博客项目需要。

下载流程：

1.  Ruby官网或者找镜像源进行下载
2.  勾选MSYS2，MSYS2 是Jekyll在Windows能正常运行的"助手工具包"。

## 安装Jekyll。主要是因为它与 GitHub Pages 深度集成，当你推送MarkDown文件或者Jekyll项目到GitHub仓库时候，Github会自动调用 Jekyll进行编译，简化了发布流程。

下载流程：

1.  打开命令行或者Powershell
2.  输入：`gem install jekyll bundler`下载jekyll
3.  在自己博客目录下输入：`jekyll new myblog`  
    (`\--skip-bundle`：跳过自动安装)

# 本地开发

## 安配置国内镜像

找到项目目录下 `Gemfile` 文件，首行写入：  
`source \"https://gems.ruby-china.com\"`

## 安装依赖

打开命令行或者Powershell输入：  
`bundle install \--path vendor/bundle`，安装主题/插件依赖，

`\--path`：将依赖安装到项目内（自己项目和系统分开）

## 启动本地服务器

在 `Gemfile` 文件目录下打开命令行或者Powershell输入：  
`bundle exec jekyll serve`，

访问地址：`http://localhost:4000`即可看到本地的服务器部署样子，不过最终还是要部署到github上的，这样都可看到了。

# **部署到GitHub Pages**

## 创建GitHub仓库

1.  命名规则：用户名.github.io（如`bigmasterQi.github.io`）
2.  仓库需设为Public

<!-- -->

## 配置SSH密钥

1.  创建密钥工作目录，命令行输入：`mkdir D:\\MySSH`
2.  生成新的SSH密钥，命令行输入：  
    ```shell
    ssh-keygen -t ed25519 -f \"D:\\MySSH\\id_ed25519\" -C \"你的邮箱@example.com\"
    ```
    按3次回车（不设置密码）后完成
3.  创建SSH配置文件，命令行输入：`notepad D:\\MySSH\\config`，粘贴以下内容：
    ```config
    Host github.com
      HostName github.com
      User git
      IdentityFile D:\\MySSH\\id_ed25519
      IdentitiesOnly yes
    ```
4.  查看并复制密钥，命令行输入：`type D:\\MySSH\\id_ed25519.pub`
5.  登录 GitHub → Settings → SSH and GPG keys → New SSH key：
    *   Title: MyDDriveKey
    *   Key: 粘贴刚才复制的公钥内容

## 推送代码

命令行输入以下内容：

```shell
# 初始化本地 Git 仓库（生成 .git 文件夹）
git init

# 关联远程 GitHub 仓库（替换为你的仓库地址）
git remote add origin git@github.com:bigmasterQi/bigmasterQi.github.io.git

# 将所有新增/修改的文件添加到暂存区（"." 代表当前目录）
git add .

# 提交到本地仓库，并添加描述信息（建议写清楚改动内容）
git commit -m \"Initial commit\"

# 推送到远程仓库的 main 分支（-u 设置默认上游分支）
git push -u origin main
=======
# bigmasterQi.github.io
my blog
>>>>>>> 136b54ff920ada680d01264590ff3ffe03d0105f
