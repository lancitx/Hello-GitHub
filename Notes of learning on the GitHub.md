# Notes of learning on the GitHub

**书山有路勤为径，学海无涯苦作舟。**



## 1. GitHub的几种许可

- **MIT许可证：**
  MIT许可证是一种非常宽松的许可证，**允许任何人使用、修改、分发代码**，甚至可以将代码用于闭源商业项目，只需在代码副本中包含原始版权和许可声明。这使得MIT许可证非常适合需要广泛传播的开源项目。
- **Apache许可证：**
  Apache许可证是一种类似于MIT许可证的开源许可证，但它**还包含了一些专利权方面的条款**，以保护贡献者和使用者免受潜在的专利诉讼。它允许自由使用、修改、分发代码，并在遵循许可证条件的情况下进行专利授权。
- **GNU通用公共许可证（GPL）：**
  GPL是一种“强制性”的开源许可证，要求任何以GPL许可的代码派生作品也必须以GPL许可发布。这意味着**使用或修改GPL许可的代码的项目也必须是开源的，不能将其用于封闭源的商业项目**。GPL确保代码的自由性和共享性，有助于避免闭源的“僵尸代码”。
- **GNU较宽松的公共许可证（LGPL）：**
  LGPL是GPL的变种，更宽松一些。LGPL通常用于库和框架，允许这些库被用于闭源商业应用，但对于对库进行的任何修改，修改的部分必须保持开源并遵循LGPL。
- **Mozilla公共许可证（MPL）：**
  MPL是一种开源许可证，**允许代码与闭源代码混合使用，但要求任何修改的部分必须以MPL许可发布**。这种许可证鼓励代码的共享和改进，同时保护原始作者的权益。
- **GNU Affero通用公共许可证（AGPL）：**
  AGPL是GPL的变种，专门用于网络应用程序。如果你在服务器上运行使用了AGPL许可的代码的修改版网络应用程序，AGPL要求你提供源代码，即使你没有分发应用程序。
- 待补充...

---

## 2. GitHub的常用操作

- **issue**：别人的开源项目有bug，可以提交issue。
- **fork**：拉分支，复制该项目到自己账号，且独立于原项目。
- **Pull Request**：建立在**fork**上，可将自己修改后的项目申请合并（**Merge**）。
- **Watch**：留意某个项目变化。
- **Gist**：开源一些代码片段。
- 待补充...

---

## 3. Git的常见操作

- 在windows下，右击**仓库目录**，进入bash，在Linux系统下，直接cd。
- `git status`：查看仓库状态（必须**事先声明该目录为仓库**）。
- `git init`：初始化仓库，算是声明，需注意在初始化前的目录下文件将显示**untracked files**。



- `git add xx`：添加`xx`文件到暂存区，**并不是真的到仓库**。
- `git add -A .`：添加**所有改变了的文件**到暂存区。
- `git add .`：表示添加**新文件和编辑过的文件，但不包括删除的文件**。
- `git add -u`：表示添加**编辑或者删除的文件，不包括新添加的文件**。

- `git commit -m "提交信息"`：将文件提交到仓库，**并附带备注信息**。



- `git log`：查看仓库的**日志**。
- `git branch`：查看**分支**。
- `git branch a`：创建**a分支**，同时当分支前显示 * 时，即表示当前分支。
- `git checkout xx`：**切换到xx分支。**
- `git checkout -b xx`：**创建xx分支，并直接进入**。
- `git merge xx`：**将xx分支合并到==当前分支==**，需检查是否冲突。
- `git branch -d xx & git branch -D xx`：**删除xx分支 & 强制删除xx分支**。
- `git tag XXX`：**给当前分支添加标签**，可以用`git tag`显示分支标签。



- `git remote -v`：查看远程仓库信息。

---

## 4. 通过Git托管GitHub代码

- 一般使用SSH将git与github绑定。
- 一般先进行**pull**，再进行**push**，针对本地无对应**git仓库**有：
- `git clone https://...`：克隆（**pull**）对应仓库件到**选定的目录中**，不用初始化，且自动匹配。
- 此后就可以在本地进行项目管理，然后使用`git add XX`和`git commit -m`**将需要添加的文件加在本地仓库中**。
- 将本地项目**push**到github中，使用`git push origin master`，**origin**是仓库名字，第一次上传需要输入账号和密码：

```c
git config --global user.name"fengye97"
git config --global user.email"***@***.com"
```

- 如果是本地已有Git仓库，且多次**commit**，则：
- 输入`git remote add origin https://..`，关联远程仓库，再输入`git pull origin master`，同步，

---

## 5. 简单演示

- 选定目录进入**bash**，输入`git clone https://..`，克隆远程仓库。

![image-20240418232455134](C:\Users\86151\AppData\Roaming\Typora\typora-user-images\image-20240418232455134.png)

- 在该目录中添加文件，

![image-20240418232750375](C:\Users\86151\AppData\Roaming\Typora\typora-user-images\image-20240418232750375.png)

- 从**目录进入bash**，输入`git status`查看状态，

![image-20240418232839247](C:\Users\86151\AppData\Roaming\Typora\typora-user-images\image-20240418232839247.png)

- 使用`git add Notes of learning on the GitHub.md & git commit -m "1st edited."`，

![image-20240418233318921](C:\Users\86151\AppData\Roaming\Typora\typora-user-images\image-20240418233318921.png)

​		然鹅，我们会发现报错，因为文件带空格，可以使用双引号，

![image-20240418233633774](C:\Users\86151\AppData\Roaming\Typora\typora-user-images\image-20240418233633774.png)

- 使用`git log`查看提交日志，使用**q**退出。
- 再输入`git push origin master`进行同步，其中origin为仓库名，master为分支名，与`git push`不同。

![image-20240419000059274](C:\Users\86151\AppData\Roaming\Typora\typora-user-images\image-20240419000059274.png)

