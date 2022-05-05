# Git

### 配置git

```JavaScript
配置自己的用户名和邮件地址
git config --global user.name "Purify"	//用户名
git config --global user.name "2030403643@qq.com"	//邮箱
//注意: 使用了 --global选项，那么该命令只需执行一次，即可永久生效
```

### Git全局配置文件

```JavaScript
通过 git config --global user.name 和 git config --global user.name 配置的用户明和邮箱地址，会被写入到 C: /Users /用户名文件夹 /.gitconfig	文件中，这个文件是Git的全局配置文件，配置一次即可永久生效
打开该文件可以查看自己设置的全局性的配置
```

### 检查配置信息

```javascript
运行终端命令快速查看全局配置项
查看全局配置项
git config --list --global
查看指定的全局配置项
git config user.name
git config user.email
```

### 获取帮助信息

```JavaScript
可以使用 gti help <verb> 命令，无需联网即可在浏览器打开帮助手册
例、要想打开 git config 命令的帮助手册
git help config
如果不想查看完整的手册，那么可以用 -h 选项获取更简明的 help 输出
git config -h
```

### 获取Git仓库的两种方式

```JavaScript
1、将尚未进行版本控制的本地目录转换为 Git 仓库
2、从其它服务器克隆一个已存在的Git仓库
```

### 在现有的目录初始化仓库

```JavaScript
1、在项目目录中，通过鼠标右键打开 Git Bash
2、执行 git init 命令将当前的目录转化为Git仓库

git init 命令会创建一个名为 .git的隐藏目录，这个 .git 的目录就是当前项目的Git仓库，里面包含了所必要的初始文件，这些文件是Git仓库的必要组成部分
```

### 检查文件的状态

```
可以使用 git status 命令查看文件处于什么状态

以精简的方式显示文件状态
git status -s
git status --short
未跟踪的文件前面有红色的 ??标记
```

### 跟踪新文件

```JavaScript
使用命令 git add 开始跟踪一个新文件， 
例、git add index.html 
运行完这个命令时表示git已经开始跟踪并管理这个文件了
此时在运行 git status 命令，会看到index.html文件在 Changes to be committed 这行的下面，说明已被跟踪并处于暂存状态
// 以精简方法显示 新添加到暂存区的文件前面会绿色的 A 标记
```

### 提交更新

```JavaScript
现在暂存区中有一个index.html文件等待被提交到Git仓库中进行保存，可以执行 git commit 命令进行提交，其中 -m 选择后面的是本次的提交信息，用来对提交的内容做进一步的描述
例、
git commit -m "新建了index.html文件"
提交成功后，在查看状态，得到如下提示
nothing to commit，working tree clean
证明工作区中的所有文件都处于 未修改的状态 没有任何文件要被提交
```

### 对已提交的文件进行修改

```JavaScript
当文件已被跟踪，且工作区跟仓库一致的时候，修改了文件
此时说明文件内容已经发生了变化，但还没有放到暂存区
//修改过的，没有放入暂存区的文件前面有红色的	M 标记
```

### 暂存已修改的文件

```JavaScript
当文件以被修改，需要暂存文件时，需要再次运行 git add命令
git add 命令是多功能命令，有以下三个功能
1、可以用它开始跟踪新文件
2、把已跟踪的、且已修改的文件放到暂存区
3、把有冲突的文件标记为已解决状态
```

### 提交暂存文件

```
再次运行 git commit -m "提交消息" 命令，将暂存区的文件提交到Git仓库
```

### git checkout -- 文件名 撤销文件的修改

```JavaScript
把共工作区中对应的文件，还原成 git 仓库中所保存的版本
操作的结果是，所有的修改会丢失，且无法恢复，危险性较高，慎重操作
git checkout -- index.html
撤销操作的本质: 用Git仓库中保存的文件，覆盖工作区中指定的文件
```

### git add . 一次添加多个文件

git add .		把所有新增和修改的文件加入暂存区

### git reset HEAD 取消已暂存的文件

```JavaScript
如果要从暂存区中移除对应的文件
git reset HEAD 要移除文件的名称

一次移除所有暂存区的文件
git reset HEAD .
```

### git commit -a -m "描述信息" 跳过使用暂存区

```JavaScript
Git的工作流程是 工作区 暂存区 Git仓库，
简化流程可以直节跳过暂存区，直接将工作区的修改提交到Git仓库
git commit -a Git会自动把所有以跟踪的文件暂存起来一并提交
```

### 移除文件

```JavaScript
从git仓库中移除文件的方式有两种
1、从Git仓库和工作区中同时移除对应的文件
git rm -f 移除的文件名
2、只从Git仓库中移除，但保留工作区中的文件
git rm --cached	移除的文件名
```

### 忽略文件

```JavaScript
一般我们总会有些文件无需纳入 Git 的管理，也不希望它们总出现在未跟踪文件列表。 在这种情况下，我们可
以创建一个名为 .gitignore 的配置文件，列出要忽略的文件的匹配模式。
文件 .gitignore 的格式规范如下：
1、以 # 开头的是注释
2、以 / 结尾的是目录
3、以 / 开头防止递归
4、以 ! 开头表示取反
5、可以使用 glob 模式进行文件和文件夹的匹配（glob 指简化了的正则表达式）

glob 模式
所谓的 glob 模式是指简化了的正则表达式：
1、星号 * 匹配零个或多个任意字符
2、[abc] 匹配任何一个列在方括号中的字符 （此案例匹配一个 a 或匹配一个 b 或匹配一个 c）
3、问号 ? 只匹配一个任意字符
4、在方括号中使用短划线分隔两个字符， 表示所有在这两个字符范围内的都可以匹配（比如 [0-9] 表示匹配
所有 0 到 9 的数字）
5、两个星号 ** 表示匹配任意中间目录（比如 a/**/z 可以匹配 a/z 、 a/b/z 或 a/b/c/z 等）
```

### 查看提交历史

```JavaScript
如果想要查看回顾项目的提交历史，可以使用 git log 这个简单有效的命令

1、按时间先后顺序列出所有的提交历史，最近的提交安排在最上面
git log
2、只展示最新的两条提交历史，数字可以按需进行填写
git log -2
3、在一行上展示最近两条提交历史的信息
git log -2 --pretty = oneline
```

### 回退到指定的版本

```JavaScript
CommitID 是版本的唯一标识 
1、在一行上展示所有的提交历史
git log --pretty=oneline
2、使用git reset --hard 命令 根据指定的提交ID回退到指定的版本
git reset --hard <CommitID>

//当切换回旧版本时需要用以下的命令来更改版本
3、在旧版本中使用 git reflog --pretty=oneline 命令 查看命令操作的历史
git reflog --pretty=oneline
4、再次根据最新提交的ID 跳转到最新的版本
git reset --hard <commitID
```

# Girhub

### 远程仓库的两种访问方式

```JavaScript
Github上的远程仓库，有两种访问方式
1、HTTPS: 零配置，但是每次访问仓库，需要重复输入Github的账户密码才能成功
2、SSH 需要进行额外的配置，但是配置成功后，每次访问仓库时，不需要重复输入Github的账号和密码

```

### 将远程仓库克隆到本地

git clone 远程仓库的地址

### Git分支

```
在进行多人协作开发的时候，为了防止互相干扰，提高协调开发的效率，建议每个开发者都基于分支进行项目功能的开发

master 主分支
在初始化本地Git仓库时，Git默认已经帮我们创建了一个名字叫做master分支，通常我们把这个master分支叫做主分支
在实际工作中，master主分支的功能是: 用来保存和记录整个项目已完成的功能代码

功能分支
由于程序员不能直接在master分支上进行功能的开发，所以就有了功能分支的概念
功能分支 指的是专门用来开发新功能的分支，它是临时从master主分支上分叉出来的，当新功能开发且测试完毕后，最终需要合并到master主分支上
```

### 查看分支列表

使用 git branch 可以查看当前Git仓库中的所有分支列表

### 创建新分支

使用 git branch 分支名称 可以基于当前分支，创建一个新分支，此时新分支的代码和当前分支完全一样

### 切换分支

使用 git checkout 分支名 可以切换到指定的分支上进行开发

### 分支的快速创建和切换

使用如下的命令，可以创建指定名称的新分支，并立即切换到新分支上

```JavaScript
// -b	表示创建一个新分支
// checkout	表示切换到刚才新建的分支上
git checkout -b 分支名称
```

### 合并分支

```JavaScript
1、切换到master分支
git checkout master
2、在master 分支上运行 git merge 命令将login分支的代码合并到master分支
git merge login
//合并分支的注意点
假设要把C分支的代码合并到A分支，则必须先切换到A分支上，在运行 git mergr 命令，来合并C分支
```

### 删除分支

```
当把功能分支的代码合并到 master 主分支上以后，就可以使用如下的命令，删除对应的功能分支
git branch -d 分支名称
```

### 遇到冲突时的分支合并

```JavaScript
如果在两个不同的分支中，对同一个文件进行了不同的修改，Git就没办法干净的合并它们，此时，我们需要打开这些包含冲突的文件然后手动解决冲突
```

### 将本地分支推送到远程仓库

```javascript
如果是第一次将本地分支推送到远程仓库，需要运行如下命令
-u 表示把本地分支和远程分支进行关联，只在第一次推送时需要-u参数
git push -u 远程仓库的别名 本地分支名称:远程分支名称

示例、
git push -u origin payment:pay

如果希望远程的分支的名称和本地分支名称保持一致，可以对命令进行简化
git push -u origin payment

// 只有第一次推送分支时需要带-u参数，此后可以直接用 git push 推送代码到远程分支
```

### 查看远程仓库分支列表

git remote show 远程仓库名称	可以查看远程仓库中，所有的分支列表

### 跟踪分支

```JavaScript
跟踪分支指的是，从远程仓库中，把远程分支下载到本地仓库中
//	从远程仓库中，把对应的远程分支下载到本地仓库，保持本地分支和远程分支名称相同
git checkout 远程分支的名称
示例、
git checkout pay

//从远程仓库中，把对应的远程分支下载到本地仓库，并把下载的本地分支进行重命名
git checkout -b 本地分支名称 远程仓库名称/远程分支名称
示例
git checkout -b payment origin/pay
```

### 拉取远程分支的最新代码

git pull	从远程仓库，拉去当前分支的最新代码，保持当前分支的代码和远程分支代码一致

### 删除远程分支

```JavaScript
//删除远程仓库中，指定名称的远程分支
git push 远程仓库名称 --delete 远程分支名称
示例、
git push origin --delete login
```

