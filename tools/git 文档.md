### 一、github 介绍

1. GitHub 是全球最大的社交编程及代码托管网站（https://github.com/）

2. GitHub 可以托管各种 git 库，并提供一个 Web 界面（**用户名.github.io/仓库名**）

3. 借助 GitHub 托管（保存）项目代码

### 二、github 名词介绍

1. 仓库(**repository**)
   用来存放项目代码，每个项目对应一个仓库，多个开源项目则有多个仓库
2. 收藏(**Star**)
   收藏项目，方便下次查看
3. 复制克隆项目(**Fork**)
   将别人的项目复制过来
4. 发起请求(**Full Request**)
   请求别人修改项目
5. 关注(**Watch**)
   关注别人项目更新
6. 事务(**Issue**)
   别人提出的问题

### 三、GitHub 搭建网站

1. 创建个人站点 -> 新建仓库(仓库名必须是：用户名.github.io)
2. 在仓库下新建 index.html 的文件即可

> 注意：
> GitHub page 仅支持静态网页
> 仓库里面只能是 .html 文件

> **应用模板：**
> 进入项目主页，点击 settings
> 在 settings 页面，点击 Launch automatic page generator 来自动生成主题页面
> 新建站点基础信息设置
> 选择主题
> 生成网站
> 可以在仓库主页中 Branch 中选择，修改 index.html 即可

### 四、git 下载

> windows 版本：https://git-scm.com/download/win

### 五、git 初识

> 工作区(workspace) -> 暂存区(index/stage) -> Git 仓库(本地仓库 repository) -> 远程仓库(remote)

1. **工作区**：添加、编辑、修改文件等动作（init）
2. **暂存区**：暂存已经修改的文件最后统一提交到 Git 仓库中（add）
3. **Git 仓库**：最终确定的文件保存到仓库，成为一个新的版本，并且对他人可见（commit）
4. **远程仓库**：提交到 github 中（push）

### 六、git 常用命令行

1. 克隆仓库：`git clone [url]`

> eg：git clone git://github.com/schacon/grit.git

2. 检查当前文件状态：`git status`
3. 对现有的某个项目开始用 Git 管理：`git init`
4. 跟踪新文件：`git add 文件或目录路径`

> `git add -A` 提交所有变化
> `git add -u` 提交被修改(modified)和被删除(deleted)文件，不包括新文件(new)
> `git add .`  提交新文件(new)和被修改(modified)文件，不包括被删除(deleted)文件

4. 提交更新：`git commit`

> 先用 git status 查看是否都已经暂存起来，再提交
>
> 会启动 vim 文本编辑器 :wq 退出 vim 模式

5. 移除文件：`git rm file`

> git 中删除带有**空格**和**括号**的文件都要加反斜杠

6. 移动文件：`git mv file_from file_to`

7. 推送数据到远程仓库：`git push origin master`

> **常用命令：**
>
> `git init`
> `git add -A`
> `git commit -m 'update'`
> `git push`

### 七、github 常用技巧

1. 进入仓库页面，按 T 可以搜索项目的文件

2. 点击New files按钮，然后输入含有slash字符(“/”)的文件名即可。也就是建立一个含有路径(目录)的文件，即会自动产生新文件夹。

3. 点击Upload files按钮，然后直接把本地的文件夹（内含文件）拖进去批处理上传。

### 八、参考文献

> 1. git 官方文档：https://git-scm.com/book/zh/v1/Git-%E5%9F%BA%E7%A1%80-%E5%8F%96%E5%BE%97%E9%A1%B9%E7%9B%AE%E7%9A%84-Git-%E4%BB%93%E5%BA%93

> 2. git 教程：http://www.runoob.com/git/git-tutorial.html

> 3. solve 'everything up-to-date'：https://stackoverflow.com/questions/2936652/git-push-wont-do-anything-everything-up-to-date