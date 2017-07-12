## git bash 操作文件及文件夹命令

- cd:切换到哪个目录下，如cd e:\fff切换到E盘下面的fff目录。当我们用cd进入文件夹时，我们可以使用通配符*,cd f* 如果E盘下只有一个f开头的文件夹，它就会进入到这个文件夹
- cd .. 回退到上一个目录，注意，cd 和两个点点..之间有一个空格。
- pwd: 显示当前目录路径
- ls(ll):都是列出当前目录中的所有文件，只不过ll(两个l)列出的内容更为详细。
- touch: 新建一个文件如touch index.js就会在当前目录下新建一个index.js文件。
- rm: 删除一个文件，rm index.js就会把index.js文件删除。
- mkdir: 新建一个目录，就是新建一个文件夹，如mkdir src 新建src文件夹
- rm -f 删除一个文件夹， rm -r src删除src目录，好像不能用通配符
- mv移动文件，，mv index.html src index.html使我们要移动的文件，src是目标文件夹，当然这样写必须保证文件夹和目标文件夹在同一目录下。
- reset清屏，把git bash 命令窗口中的额度搜有内容清空。
## 首先建立版本库

1. 进入一个建立好的文件夹(也可以用命令创建mkdir FileName) 
  命令: git init(初始化版本仓库)

2. git add test.txt(将文件添加到暂存区中)

3. git commit -m 'test.txt 提交'(将文件提交到仓库)
   - git commit -a -m 'add somethings'( 一条命令搞定git add -A 和git commit -m 'add')

4. git status (用来查看是否有文件没有提交)

5. git diff test.txt(查看文件的修改部分)

6. git log(查看日志详情)

7. git log --  pretty=oneline(单行显示日志)
    - git log --pretty=oneline --abbrev-commit(只显示提交id的后七位进行单项显示日志)
    - q (退出git log 命令)

8. git reset --hard HEAD^(回退到上一个版本)

9. git reset --hard HEAD~n(回退到指定的版本)

10. git reflog (获取版本号)

11. git reset --hard HEAD^(撤销修改也就是没有提交我就回到上一个版本就是全部撤销)

12. git checkout --test.txt(test.txt文件工作区做的修改全部撤销，如果git add以后，那么就恢复到添加暂存区后的状态，就是git add后的状态，反之就是恢复到上一个版本)

13. git rm a.txt(删除a.txt在没有commit以前可以恢复git checkout -- a.txt)
    - git rm -r 文件夹名(删除文件夹，删除文件夹的时候一定要带上-r)否者无法删除
    - git clean -fd使用git rm -rf删除空文件夹之后，本地哈市会有空的目录存在，这时候空目录已经是untracked状态了解决办法是再删除掉untracked状态的目录，使用git clean -fd 执行了该命令以后本地的空目录就没有了。

14. git remote add origin https://github.com//zkydrx/MyDemo(把本地仓库的内容推送到GitHub仓库)

15. git push -u origin master(把本地仓库分支master内容推送到远程仓库上去 第一次推送加-u参数，git不但会把本地的master分支内容推送的远程新的master分支上去，还会把本地的master 分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令)

16. git push origin master(简化后的推送命令)

17. git clone https://github.com/zkydrx/MyDemo(从github远程把文件克隆到本地)
    - git clone git@github.com:zkydrx/MyDemo(另外的一种形式从github远程把文件克隆到本地)

18. git checkout -b dev(创建并切换分支)
    - git checkout 命令加上 -b参数表示创建并切换，相当于如下两条命令
    - git branch dev
    - git checkout dev

19. git branch (查看当前分支)

20. git checkout master(切换分支)

21. git merge dev(在master分支上合并dev分支内容)

22. git branch -d dev(删除分支)
    - git branch -D dev(强制删除没有合并的分支)

23. git merge --no-ff -m "merge with no-ff" dev(合并dev分支，-no-ff表示禁用fast forward模式此种模式删除分之后，分支信息还在可以恢复)

24. git stash(将当前的工作现场隐藏起来，以便于创建issue-404分支修复bug)

25. git stash list(查看工作现场)

26. git stash apply(恢复工作现场)
    - git stach drop stach内容并不删除，你需要使用git stash drop 来删除stash
    - git stash pop (恢复的同时吧stash内容也删除了)

27. git remote(查看远程库的信息)

28. git remote -v (查看远程库的详细信息)

29. git push origin dev(把分支推送到远程去)

30. git pull (把最新的提交从origin/dev抓取下来)

31. git branch --set-upstream dev origin/dev(指定本地dev分支与远程origin/dev分支的链接进行抓取)

32. git tag (查看标签)

33. git tag v1.0(打标签，默认标签是打在最新的commit上的)
    - git tag v0.9 commit_id (可以按照commit id来打标签)

34. git show v0.9 (查看标签详情)

35. git tag -a v0.1 -m 'version 0.1 released' commit id(创建带说明的标签，用-a指定标签名，用-m指定说明文字)

36. git tag -s v0.1 -m 'version 0.1 released' 15ed377(用私钥签名一个标签)

37. git tag -d v0.1(删除一个标签)

38. git push origin v1.0(推送标签到远程)

39. git push origin --tags(一次性推送全部尚未推送到远程的本地标签)

40. git tag -d v0.2(远程删除版本先删除本地的版本)
    - git push origin  :refs/tags/v0.2(远程删除标签第二步push到远程)

41. git add -f a.class(强制添加a.classes)
    - git add -a -m '提交的描述信息'(-a 选项可将所有被修改或者已删除的且已经被git管理的文档提交到仓库中，如果只是修改或者删除了已被git管理的文档，是没必要用git add命令的)
    - ctrl +z (退出git add -a 命令)
    - git add **.**(git add 点添加当前的所有改变到下一次提交中)
    - git add -A(add changes from all tracked and untracked files)

42. git config --global alias.st status (给 git status 配置别名 --global 参数是全局参数，也就是这些命令在这台点电脑上的所有git仓库下都是有效的)

43. cat .git/config(配置git的时候，加上--global是针对当前用户起作用的，如果不加，那只对当前仓库起作用。每个仓库的git配置文件都放在.git/config 文件夹中)

44. cat .gitconfig(在用户主目录中存在的隐藏配置文件，alias后面的就是别名，要删除别名，直接删除对应的行即可)

45. git commit --amend (按下子母c 进入可编辑状态修改注释)
    - ESC +Z(按两下大写的Z 保存并退出编辑器)
    - git commit -h (查看提交帮助命令)
    - git commit -am()

46. git --help(查看所有的帮助命令)

47. rm -rf broken_submodule_folder(Delete all the broken submodule folders)

48. git submodule update(Update the registered submodules and You should see the submodules being checked out.)

49. curl  -u 'zkydrx:PASSWORD'  https://api.github.com/user/repos -d '{"name":"work"}'(在git bush上用命令创建github上的远程仓库。)

    git remote add origin git@github.com:zkydrx/projectname.git(添加远程仓库)

    git push origin master(将本地主干推送到远程仓库)

    [create a remote repo on GitHub from the CLI without opening browser]([gitbush](gitbush/create a remote repo on GitHub from the CLI without opening browser.md)

    ​
