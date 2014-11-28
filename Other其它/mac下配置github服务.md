# Mac下配置GitHub服务


注册GitHub账号并登录
--

到 [https://github.com](https://github.com) 注册一个账号，然后到 [https://mac.github.com/](https://mac.github.com/) 下载 GitHub for Mac 并安装登录。

在github中创建Repository，同步到本地
--

在GitHub中新建一个Repository，输入名字和描述。根据需要勾选 Initialize this repository with a README。完成后点击 Create 来创建。

重新启动 GitHub for Mac，点击左上角的加号，选择 Clone，通过搜索或者直接选择需要同步到本地的 Repository，然后选择一个本地要保存的地方，点击 Clone。

在本地提交和同步工程
--

在本地完成修改之后，在 Summary 和 Description 中对修改进行说明，之后可以通过点击 Commit 或者 Commit&Sync 对代码进行提交和同步。

> 在 Commit 按钮左侧有个同步开关，点亮（变成绿色）之后，可以通过点击 Commit&Sync 一次性对代码进行提交和同步。

>如果没有打开，则只能通过 Commit 来对代码进行提交，点击右上角的 Sync 可以进行同步，这种方式适用于单次修改多个文件后统一同步的情况

将线上修改同步到本地
--

在 GitHub for Mac 的右上角点击 Sync，可以将线上修改同步到本地。

创建分支，修改，合并
--

GitHub 支持创建一个分支来进行修改，完成后可以将分支和主代码仓库合并。

点击主工具栏上的 Create New Branch 来建立一个分支，输入分支名，选择继承的来源，点击 Create，就可以建立一个分支。分支建立后，在 Branch 选项卡下，可以查看并选择目前的修改是在哪一个分支中进行的，也可以对分支进行发布等操作。

在修改、提交和同步的时候，一定要注意自己是在主仓库或者具体某个分支下操作，避免混淆。建议操作都在分支中进行，操作确定成功后再合并到主仓库，保证主仓库代码和文件的安全。

在 Branch 选项卡中，点击 Merge View，在出现的 Merge Branch 窗口中，将需要合并的分支和合并的目标分支分别拖动到相应的框中，点击 Merge Branchs。完成后在 Changes 中选择主代码仓库，进行同步（Sync），就完成了分支的合并。

