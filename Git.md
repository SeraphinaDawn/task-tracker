# Git

## 查看是否安装命令

```git
git --version
```

![image-20250114132835599](https://gitee.com/ActonT/pic-go_img/raw/master/image-20250114132835599.png)

## 指定用户名

```shell
git config --global user.name "Ah Nan" 			--这里引号里面填写自己要设定的名称
去除引号就是检查当前是哪个用户名
git config --global user.name
Ah Nan
```

## 指定用户邮箱

```shell
git config --global user.email ""   			--这里引号里面填写自己要设定的邮箱
去除引号就是检查当前是哪个邮箱
git config --global user.email
xxxxxxxx@gmail.com
```



## 将默认 分支改为`main`

```shell
git config --global init.defaultBranch main				--这里去除main就会显示当前分支
git config --global init.defaultBranch
main
```

## 正式开始学习使用

### 初始化本地仓库

```shell
git init
```

![image-20250114141243846](https://gitee.com/ActonT/pic-go_img/raw/master/image-20250114141243846.png)

**当初始化后回发现文件后面带一个`u`**:
**表示文件未跟踪**:

![image-20250114142822847](https://gitee.com/ActonT/pic-go_img/raw/master/image-20250114142822847.png)

### 查看隐藏文件

```shel
ls -a 			--Windows上的power shell可以使用 `ls -force`
```

![image-20250114141853102](https://gitee.com/ActonT/pic-go_img/raw/master/image-20250114141853102.png)

### 查看具体那些文件未跟踪

```shell
git status
```

![image-20250114143103490](https://gitee.com/ActonT/pic-go_img/raw/master/image-20250114143103490.png)

> 红色表示未跟踪
>
> 下面可以选择单独跟踪或者全部跟踪

#### **单独跟踪**

```shell
git add index.html
```

![image-20250114143449970](https://gitee.com/ActonT/pic-go_img/raw/master/image-20250114143449970.png)

#### **全部跟踪**

```shell
git add .
```

![image-20250114143622300](https://gitee.com/ActonT/pic-go_img/raw/master/image-20250114143622300.png)

### 提交到存储库

```shell
git commit -m "first commit" 				--引号里可以写任意东西(不限包括于备注等等)
```

![image-20250114143746906](https://gitee.com/ActonT/pic-go_img/raw/master/image-20250114143746906.png)

### 更改内容会提示`M`

> 这里一旦在已经提交的内容上做更改马上会显示`M`
>
> 需要再次`跟踪`加`提交`

```shell
git add .
git commit -m "Add new task"
```

![image-20250114144033641](https://gitee.com/ActonT/pic-go_img/raw/master/image-20250114144033641.png)

![image-20250114144516157](https://gitee.com/ActonT/pic-go_img/raw/master/image-20250114144516157.png)

### 查看提交的用户是谁

```shell
git log
```

![image-20250114144837236](https://gitee.com/ActonT/pic-go_img/raw/master/image-20250114144837236.png)

### 链接远程`GitHub`仓库

> 当你在`GitHub`上有一个仓库后会有以下消息,
>
> 如果我们已经初始过了就选择第二个

![image-20250114145404354](https://gitee.com/ActonT/pic-go_img/raw/master/image-20250114145404354.png)

#### **进行连接远程仓库**

> 代表链接远程仓库

```shell
git remote add origin git@github.com:SeraphinaDawn/task-tracker.git
```

![image-20250114145504357](https://gitee.com/ActonT/pic-go_img/raw/master/image-20250114145504357.png)

#### **切换主分支**

```shell
git branch -m main
```

#### **进行上传远程仓库**

```shell
git push origin main
```

![image-20250114145907687](https://gitee.com/ActonT/pic-go_img/raw/master/image-20250114145907687.png)

**刷新远程仓库**:

![image-20250114150003237](https://gitee.com/ActonT/pic-go_img/raw/master/image-20250114150003237.png)

#### **添加项目描述文件**

`README.md`

```markdown
# Task Tracker
This is a demo project for my Git tutorial
```

下面是在远程仓库里进行添加的,本地仓库不会显现,需要自行拉去

![image-20250114150508149](https://gitee.com/ActonT/pic-go_img/raw/master/image-20250114150508149.png)

#### 拉去最新项目

> 由于我们添加了描述文件`README.md`,本地是没有这个文件的需要进行拉去
>
> 这里需要使用 `git pull`而不是`git fetch`,
>
> - 原因如下:
>   - 因为 `git pull`是下面的两个的组合,拉取最新仓库并且自动合并
>   - `git merge` or `git rebase` :这两个需要手动拉去加上手动合并

```shell
git pull origin main			--这里是拉取最新的主分支
git pull origin <分支名>		  --如果要拉取其他分支需要写对应的分支名
```

![image-20250114151447741](https://gitee.com/ActonT/pic-go_img/raw/master/image-20250114151447741.png)

#### 简洁提交方式

> 我们直接更改其中一个文件
>
> 然后进行使用下面命令提交,省去了 `git add .`的操作,等价于 `git add . && git commit -m "Add task 6"`

```shell
git commit -am 'Add task 6'
```



### **保护 Git 私密文件**

> 提交密钥等私密文件并不想让别人看到
>
> 这个要求的话需要添加一个名为 `.gitignore`的文件 里面写入不想让比尔看到的文件例如我不想让别人看到我的 `.env`文件
>
> <img src="https://gitee.com/ActonT/pic-go_img/raw/master/image-20250114152109571.png" alt="image-20250114152109571" style="zoom:80%;" />

**提交效果**:

![image-20250114152524758](https://gitee.com/ActonT/pic-go_img/raw/master/image-20250114152524758.png)

### 从 GitHub 获取代码

![](https://gitee.com/ActonT/pic-go_img/raw/master/image-20250114153922078.png)

以下是从 GitHub 获取代码的几种常见方式，包括克隆的不同方法：

*   **下载 (Downloading):** 你可以下载一个仓库的 ZIP 压缩包。这是快速获取代码快照的方式，但不包含 Git 历史。

*   **`git clone`:**  这个命令会在你的本地机器上创建一个仓库的完整副本，包括其所有历史记录。这是开始一个 Git 项目的标准方式。
    > *   **HTTPS:** 使用 HTTPS URL 克隆仓库。
    >     *   **优点:** 简单，大多数情况下可以使用。
    >     *   **缺点:** 每次推送代码时可能需要输入用户名和密码 (或者使用 token)。
    >     *   **示例:**  `git clone https://github.com/用户名/仓库名.git`
    > *   **SSH:**  使用 SSH URL 克隆仓库。
    >     *   **优点:** 不需要每次都输入用户名和密码，使用 SSH 密钥进行身份验证。
    >     *   **缺点:** 需要配置 SSH 密钥。
    >     *   **示例:** `git clone git@github.com:用户名/仓库名.git`
    > *   **GitHub CLI:** 使用 GitHub 命令行工具 (`gh`) 克隆仓库。
    >     *   **优点:** 集成了 GitHub 的功能，更加方便。
    >     *   **缺点:** 需要安装 GitHub CLI。
    >     *   **示例:** `gh repo clone 用户名/仓库名`

*   **`git pull`:** 这个命令从远程仓库获取最新的更改，并将其合并到你当前的分支。它用于保持本地仓库与远程仓库同步。

*   **`git fetch`:** 这个命令从远程仓库获取最新的更改，但是不合并。你可以先查看这些更改，再决定是否合并。

*   **Fork (复制):** 这会在你自己的 GitHub 帐户中创建仓库的副本。当你想要为项目贡献代码或者在不直接更改原始仓库的情况下试验代码时，这个非常有用。

#### 生成ssh密钥

```shell
ssh-keygen -t rsa -b 4096
```

**存储位置**:

```shell
C:\Users\MAH/.ssh/id_github
```

![image-20250114154839319](https://gitee.com/ActonT/pic-go_img/raw/master/image-20250114154839319.png)

**在存储位置就可以看到了**:

![image-20250114154951934](https://gitee.com/ActonT/pic-go_img/raw/master/image-20250114154951934.png)

#### 公钥添加到GitHub上

![git_key](https://gitee.com/ActonT/pic-go_img/raw/master/git_key.gif)

**检查是否成功**:

> 提示下面图片证明成功

```shell
ssh -T git@github.com
```

![image-20250114160108075](https://gitee.com/ActonT/pic-go_img/raw/master/image-20250114160108075.png)

#### 克隆仓库

> 下面的例子是对远程仓库进行克隆到本地的一个文件夹内

![git_clone](https://gitee.com/ActonT/pic-go_img/raw/master/git_clone.gif)

### 切换分支 or 合并分支

> 先添加一个名为`feature/login`这个分支代表的是login登录界面
>
> 使用下面命令会立即创建加上马上切换分支

```shell
git checkout -b feature/login
```

#### **添加如下内容**:

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>Task Tracker</title>
        <link rel="stylesheet" href="style.css" />
    </head>
    <body>
        <div>
            <form action="/login" method="post">
                <div class="form-control">
                    <label for="username">Username</label>
                    <input
                           type="text"
                           id="username"
                           name="username"
                           placeholder="Enter username"
                           required
                           />
                </div>
                <div class="form-control">
                    <label for="password">Password</label>
                    <input
                           type="password"
                           id="password"
                           name="password"
                           placeholder="Enter password"
                           required
                           />
                </div>
                <button type="submit" class="btn">Login</button>
            </form>
        </div>
        <script src="script.js"></script>
    </body>
</html>
```

#### **下面是进行分支合并,并且删除分支**:

> 这里演示在GitHub里完成合并并且删除

![git_合并](https://gitee.com/ActonT/pic-go_img/raw/master/git_合并.gif)

#### **进行切换到主分支并拉取最新远程仓库**:

> 这里切换到主分支会发现login 没有在本地,是因为没有进行拉取最新

```shell
git checkout main				--切换到主分支
--注意这里是本地仓库所以分支并没有删除,只是远程仓库的分支被删除了
git pull origin main			--拉取最新main分支
```

![image-20250114163250003](https://gitee.com/ActonT/pic-go_img/raw/master/image-20250114163250003.png)

#### **进行删除本地多余分支**:

```shell
git branch -d feature/login				--删除本地余留的分支
git branch 							  --查看本地的分支
```

![image-20250114163633946](https://gitee.com/ActonT/pic-go_img/raw/master/image-20250114163633946.png)