# git简要笔记


>+ git remote -v：                                        查看远程仓库详细信息，可以看到仓库名称
>+ git remote remove orign：                       删除orign仓库（如果把origin拼写成orign，删除错误名称仓库）
>+ git remote add origin 仓库地址：              重新添加远程仓库地址
>+ gti push -u origin master：                      提交到远程仓库的master主干

## 1. git clone
>从git服务器拉取代码
```git
git clone https://github.com/gafish/gafish.github.com.git
```
+ 代码下载完成后在当前文件夹中会有一个 gafish.github.com 的目录，通过 cd gafish.github.com 命令进入目录。

## 2. git config
>配置开发者用户和邮箱
```git
git config user.name gafish
git config user.email gafish@qq.com
```
+ 每次代码提交的时候都会生成一条提交记录，其中会包含当前配置的用户名和邮箱

## 3. git branch
>创建、重命名、查看、删除项目分支，通过Git做项目开发时，一般都是在开发分支中进行，开发完成后合并分支到主干。
```git
git branch daily/0.0.0                   #创建一个名为```daily/0.0.0```的日常开发分支，分支名只要不包括特殊字符即可
git branch -m daily/0.0.0 daily/0.0.1    #如果觉得之前的分支名不合适，可以为新建的分支重命名
git branch -a                            #通过不带参数的branch命令可以查看当前项目分支列表
git branch -d daily/0.0.1                #删除本地已经合并了的分支
git branch -D daily/0.0.1                #删除本地未合并的分支
```

## 4. git checkout
>切换分支
```git
git checkout daily/0.0.1
```
+ 切换到```daily/0.0.1```分支，后续的操作将在这个分支上进行

## 5. git status
>查看文件变动状态

+ 通过任何你喜欢的编辑器对项目中的```REAME.md```文件做一些改动，保存。
```git
git status
```
+ 通过```git status```命令可以看到文件当前状态```Changes not stages for commit:```（改动文件未提交到缓存区）
```git
On branch daily/0.0.1
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)
    modified:   README.md
no changes added to commit (use "git add" and/or "git commit -a")
```

## 6. git add
>添加文件变动到暂存区
```git
git add README.md
```
+ 通过指定文件名```README.md```可以将该文件添加到暂存区，如果想添加所有文件可用 ```git add . ```命令，这时候可通过 ```git status``` 看到文件当前状态 ```Changes to be committed: （文件已提交到暂存区）```
```git
On branch daily/0.0.1
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)
    modified:   README.md
```

## 7. git commit
>提交文件变动到版本库
```git
git commit -m '这里写提交原因'
```
+ 通过``` -m ```参数可直接在命令行里输入提交描述文本

## 8. git push
>将本地的代码修改推送到服务器
```git
git push origin daily/0.0.1
```
* ```origin ```指代的是当前的git服务器地址，这行命令的意思是把``` daily/0.0.1 ```分支推送到服务器。
* 现在我们回到Github网站的项目首页，点击``` Branch:master``` 下拉按钮，就会看到刚才推送的``` daily/0.0.1``` 分支了

>删除服务器远端的分支，执行如下代码
```git
git push origin --delete daily/0.0.1
```

## 9. git pull
>将服务器上的最新代码拉取到本地
```git
git pull origin daily/0.0.1
```
* 如果其它项目成员对项目做了改动并推送到服务器，我们需要将最新的改动更新到本地，这里我们来模拟一下这种情况。
* 进入Github网站的项目首页，再进入 daily/0.0.1 分支，在线对 README.md 文件做一些修改并保存，然后在命令中执行以上命令，它将把刚才在线修改的部分拉取到本地，用编辑器打开 README.md ，你会发现文件已经跟线上的内容同步了。
* 如果线上代码做了变动，而你本地的代码也有变动，拉取的代码就有可能会跟你本地的改动冲突，一般情况下 Git 会自动处理这种冲突合并，但如果改动的是同一行，那就需要手动来合并代码，编辑文件，保存最新的改动，再通过 git add . 和 git commit -m 'xxx' 来提交合并。