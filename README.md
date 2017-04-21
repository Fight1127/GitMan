# GitMan
A git manual for ourselves.

### Git路径（XXX为项目名称）
https://github.com/Fight1127/XXX.git

### 分支分布（下列命名均为举例）

* 发布分支
‘master’
* 开发合并分支
‘developer’
* 开发个人分支
各人自己命名，最好命名为'name_version_dev_branch_extra'格式，其中name为自己英文名，extra为需求名，一般情况下可不写。（例如：'ysy_v1.0.0_dev_branch'）

### Git使用基础

* Clone远程仓库
git clone https://github.com/Fight1127/XXX.git
* 切换到developer分支
git checkout developer
* 新建自己的dev分支（这里举个例子叫：ysy_v1.0.0_dev_branch）
git checkout -b ysy_v1.0.0_dev_branch
* 将ysy_v1.0.0_dev_branch分支push到远程仓库
git push origin ysy_v1.0.0_dev_branch
* 原则是只可以在ysy_v1.0.0_dev_branch下开发，并Push到ysy_v1.0.0_dev_branch分支下，待Review后自动Merge到developer分支

### <模拟一个开发流程>

* 添加自己改动的代码到暂缓区，add自己要提交的代码，这里为了方便add所有的代码
git add .
* Review自己的代码
git diff --cached
* 提交更改（message一般为本次提交代码的改动要点）
git commit -m "message"
* 切换到developer分支
git checkout developer
* 拉取远程仓库的代码
git pull origin developer
* 切换到ysy_v1.0.0_dev_branch分支
git checkout ysy_v1.0.0_dev_branch
* 将developer代码Merge到ysy_v1.0.0_dev_branch分支
git merge developer
* 重新Build工程，运行，检查没问题后Push到远程仓库
git push origin ysy_v1.0.0_dev_branch
* 去GitHub上创建一个Merge Request（ysy_v1.0.0_dev_branch->developer）

#### 相应的Reviewer审查没问题后，同意Merge后会自动将远程仓库下ysy_v1.0.0_dev_branch分支合并到developer分支下，
至此一个流程就结束了，当然，如果遇到冲突就解决。如果review不过也要解决。

* 此时状态：
远程仓库的代码都要比本地的新，所以此时可以在拉取代码，不过也可以等到下一次提交前拉取代码，但是一定要确保在Push代码前，拉取一下developer下的代码，并Merge到本地ysy_v1.0.0_dev_branch后，再Push到远程ysy_v1.0.0_dev_branch。
