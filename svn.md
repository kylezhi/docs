SVN简介：

为什么要使用SVN？

　　公司多人协同开发有需要，类似于GIT, 关于git可以看我之前的博客[git的使用[转\]](http://www.cnblogs.com/0zcl/p/6874588.html)，也可以看网上的廖雪峰写的博客。

Subversion是什么？

　　它是一个自由/开源的版本控制系统，一组文件存放在中心版本库，记录每一次文件和目录的修改，Subversion允许把数据恢复到早期版本，或是检查数据修改的历史，Subversion可以通过网络访问它的版本库，从而使用户在不同的电脑上进行操作。

 

一：SVN服务器搭建和使用。

   1.     首先来下载和搭建SVN服务器,下载地址如下: <http://subversion.apache.org/packages.html>，进入网址后，滚动到浏览器最底部看到如下截图：

  ![img](https://images0.cnblogs.com/blog/561794/201409/130940097464156.png)

　　个人认为最好用VisualSVN server 服务端和 TortoiseSVN客户端搭配使用. 点开上面的VisualSVN连接,下载VisualSVN server,下载完成后双击安装，如下图：

![img](https://images0.cnblogs.com/blog/561794/201409/130940357152923.png)

 

点击Next下一步，如下：

![img](https://images0.cnblogs.com/blog/561794/201409/130940544815722.png)

然后再点击Next项，下一步，如下：

![img](https://images0.cnblogs.com/blog/561794/201409/130942171846989.png) 

点击【Next】 如下：

![img](https://images0.cnblogs.com/blog/561794/201409/130941151521908.png)

 

![img](https://images0.cnblogs.com/blog/561794/201409/130942509964894.png)

Location是指VisualSVN Server的安装目录,Repositorys是指定你的版本库目录.Server Port指定一个端口,Use secure connection勾山表示使用安全连接,

点击Next,进入下一步,如下图:

![img](https://images0.cnblogs.com/blog/561794/201409/130943132776319.png)

再点击【Install】,进入如下安装图：

![img](https://images0.cnblogs.com/blog/561794/201409/130943304963093.png)

等待安装完成后，点击【next】，进入下一步：如下图

![img](https://images0.cnblogs.com/blog/561794/201409/130943551219603.png)

点击【Finish】即可完成安装。安装完成后,启动VisualSVN Server Manager,如图:

![img](https://images0.cnblogs.com/blog/561794/201409/130944137937132.png)

可以在窗口的右边看到版本库的一些信息,比如状态,日志,用户认证,版本库等.

要建立版本库,需要右键单击左边窗口的Repositores,如下图:

![img](https://images0.cnblogs.com/blog/561794/201409/130944400126654.png)

在弹出的右键菜单中选择Create New Repository或者新建->Repository:

![img](https://images0.cnblogs.com/blog/561794/201409/130945042624979.png)

进入下一步，如下图：

![img](https://images0.cnblogs.com/blog/561794/201409/130945270592548.png)

点击【下一步】，如下图：

![img](https://images0.cnblogs.com/blog/561794/201409/130945478095475.png)

点击【create】，如下图：

![img](https://images0.cnblogs.com/blog/561794/201409/130946035597264.png)

点击【Finish】即可完成基本创建。

  2. 需要建立用户和组，并且需要分配权限。

  1. 在VisualSVN Server Manager窗口的左侧右键单击用户组,选择Create User或者新建->User,如图:

  ![img](https://images0.cnblogs.com/blog/561794/201409/130949016213832.png)

点击User后，进入如下图：

![img](https://images0.cnblogs.com/blog/561794/201409/130949204342618.png)

填写Username和password后，点击ok按钮后，进入如下图：

![img](https://images0.cnblogs.com/blog/561794/201409/130949386523219.png)

点击上面的【Add】按钮后，如下图

![img](https://images0.cnblogs.com/blog/561794/201409/130949555901779.png)

增加longen0707到用户中(如果有多个用户，操作一样)。

  2 .   然后我们建立用户组,在VisualSVN Server Manager窗口的左侧右键单击用户组,选择Create Group或者新建->Group,如图:

  ![img](https://images0.cnblogs.com/blog/561794/201409/130950456215926.png)

点击【Group】按钮后，进入如下图：

![img](https://images0.cnblogs.com/blog/561794/201409/130951043091983.png)

在弹出窗口中填写Group name为Developers,然后点Add按钮,在弹出的窗口中选择Developer,加入到这个组,然后点Ok.

接下来我们需要给用户组设置权限，在MyRepository上单击右键,选择属性,如图:

![img](https://images0.cnblogs.com/blog/561794/201409/130951240591083.png)

在弹出的对话框中,选择Security选项卡,点击Add按钮,选中longen0707,然后添加进来,权限设置为Read/Write,如下图:

![img](https://images0.cnblogs.com/blog/561794/201409/130951476219251.png)

点击【确定】按钮即可。

二：客户端SVN安装。

 1.首先我们需要下载 ”svn小乌龟”后，进行安装。比如我下载如下的：

 ![img](https://images0.cnblogs.com/blog/561794/201409/130952559814500.png)

   安装完成后，比如在我的项目在qiandaun1中，我右键就可以看到如下：

  ![img](https://images0.cnblogs.com/blog/561794/201409/130953259653808.png)

说明snv已经安装成功了！

2：checkout项目文件。

啥是checkout?? 最开始我也一脸蒙逼，这里有几个概念要必须掌握：checkout--->将SVN仓库的代码烤到本地，比如你现在参与一个团队项目，项目代码在你之前肯定已经写了很多了，你可以通过checkout项目代码，获得整个项目。update--->在你写代码的过程中，同事很可能已经提交过代码到SVN服务器，而你本地项目显然没有同事新提交的代码，你可以通过update SVN获得SVN最新的代码。commit--->当你完成一部分开发后，你可以通过commit提交代码到SVN服务器，这样别人就可以获得你写的代码，记得先update再commit。

新建或者进入目录下(比如qianduan1)，右键 --> Svn Checkout -->

![img](https://images0.cnblogs.com/blog/561794/201409/130954311373629.png)

其中URL我可以在SVN服务器获取到，我在myRepositories下右键新建文件

![img](https://images0.cnblogs.com/blog/561794/201409/130955243404677.png) 

qianduan文件被建立，然后比如我这样右键 --> copy下

![img](https://images0.cnblogs.com/blog/561794/201409/130955550127438.png)

即可。

将复制的版本库URL粘贴上,如下图：

![img](https://images0.cnblogs.com/blog/561794/201409/130956201842848.png)

点击【ok】按钮后，就可以检索出来，如下：

![img](https://images0.cnblogs.com/blog/561794/201409/130956434024588.png)

如下图：

 ![img](https://images0.cnblogs.com/blog/561794/201409/130957017156161.png)

注意事项：

   .svn这个隐藏目录记录着两项关键信息：工作文件的基准版本和一个本地副本最后更新的时间戳，千万不要手动修改或者删除这个.svn隐藏目录和里面的文件!!,否则将会导致你本地的工作拷贝(静态试图)被破坏，无法再进行操作。

  1)    TortoiseSVN图标介绍

  ![img](https://images0.cnblogs.com/blog/561794/201409/130958036843028.png)  

   一个新检出的工作复本使用绿色的对勾重载，表示Subversion状态正常。

   ![img](https://images0.cnblogs.com/blog/561794/201409/130958194344817.png) 

  在你开始编辑一个文件之后，状态就变成了已修改，而图标重载已变成了红色感叹号。通过这种方式，你可以很容易地看出那些文件从你上次更新工作复本被修改过，且需要提交。

   ![img](https://images0.cnblogs.com/blog/561794/201409/130958514341307.png)  如果在提交的过程中出现了冲突，图标就会变成了黄色感叹号。

  ![img](https://images0.cnblogs.com/blog/561794/201409/130959104658494.png)  

加号告诉你有一个文件或者目录已经被计划加入到版本控制中。

2)     TortoiseSVN Client基础操作:

​    1. SVN检出(SVN Checkout)

​     在文件夹或者目录下单击右键 –> 选择SVN检出，如下图所示

​     ![img](https://images0.cnblogs.com/blog/561794/201409/131000197469827.jpg)

  点击后，在弹开窗口的版本库url框中输入版本库的目录地址，然后点击确定，如下图

 ![img](https://images0.cnblogs.com/blog/561794/201409/131000495273963.png)

再点击ok按钮后，如下图：

在弹出的对话框中输入用户名和密码，验证成功后，项目文件开始从远程服务器下载到本地工作目录中。

![img](https://images0.cnblogs.com/blog/561794/201409/131001138871787.png)

点击ok按钮后，即可获取完成，如下图所示：

 2.  增加(Add)

  在test项目文件下，新建一个b.txt文件，提交到版本库的方法如下2种：

   1. 先提到变更列表中，再commit到配置库中，选择新增文件，右键SVN菜单执行“Add“操作提交到”变更列表中”，然后右键SVN菜单执行”SVN Commit”提交到版本库中。

   2. 不提交到变更列表中，而是直接commit配置库中，选择该文件，右键svn菜单执行”SVN Commit”操作。

  3.  删除(Delete)

​     如果被删除的文件还未入版本库，则可以直接使用操作系统的删除操作删除该文件。

​     如果被删除的文件已入版本库，则删除的方法如下：

1. 选择被删除文件，右键svn菜单执行”delete”操作，然后选择被删除文件的父目录，右键svn菜单执行”SVN Commit”.

使用操作系统的删除操作删除该文件，然后选择被删除文件的父目录，右键svn菜单执行”SVN Commit”,在变更列表中选择被删除的文件。如下图：

   ![img](https://images0.cnblogs.com/blog/561794/201409/131003076212175.png)

 4.  改名(Rename)

​    修改文件名，选中需要重命名的文件或文件夹，然后右键“TortoiseSVNàRename“，在弹出的对话框中输入新名称，点击”ok”按钮，并将修改文件名后的文件或文件夹通过 “SVN Commit”提交到SVN服务器上。

 5.  SVN还原(SVN Revert)

​    右击想要回退的文件或者文件夹，在TortoiseSVN弹出菜单中选择”Update to reversion…” 然后会弹出一个窗口，如下：

  ![img](https://images0.cnblogs.com/blog/561794/201409/131004377467407.png)

比如说我们要回退到第10个版本只需要在Revision中填写相应的版本号，然后点击ok即可。

 6.  检查更新(Check for modifications)

​     此功能可以显示你所做的修改有哪些还没有提交的，此功能不光能看到对文件的修改变化，所有的变化都能看到，包括增加文件或者目录，删除文件或者目录，移动文件或者目录等，如果你点击了检查版本库，那你还可以看到版本库里的改动，既别人提交了哪些文件的改动，你还没更新到本地，如下：

  ![img](https://images0.cnblogs.com/blog/561794/201409/131005199818404.png)

 7.  SVN更新(SVN Update)

​    更新本地代码与SVN服务器上最新的版本一致，只要在需要更新的文件夹上点击右键或者在文件下空白处点击右键，选择”SVN Update” (获取指定版本中的内容，点击右键执行SVN菜单中的“Update to reversion“)，就可以了。

 7.1 如何解决冲突文件

​     对于每个冲突的文件Subversion在你的目录下放置了三个文件：如下：

   ![img](https://images0.cnblogs.com/blog/561794/201409/131008249027809.png)

​     为什么会产生冲突代码呢？原因很简单就是因为不同的人，同时修改了同一个文件的同一个地方，这时候，他提交了，我没有提交，我就提交不了，这个时候我们要进行先更新，然后在进行提交即可，那如果产生冲突，会生成如上3个文件。 

解决方案如下：

​      首先我们可以看下1.txt代码如下：

​        <<<<<<< .mine

​        aaaasdf11222333 dderderder

​        =======

​       b>>>>>>> .r5

​      然后我去掉多余的代码，1.txt变成这样

​      aaaasdf11222333 dderderder

​      进行提交，还是提交不了，如下所示：

​    ![img](https://images0.cnblogs.com/blog/561794/201409/131009310127945.png)

  为什么？因为冲突会产生上面的三个文件，有上面3个文件存在肯定提交不了，这三个文件代码及解释如下：

1. 1.txt.mine 是冲突前自己的文件。可以看下内容如下：

​      aaaasdf11222333 dderderder

​      2.  1.txt.r4 是冲突前本地的版本文件

​     内容如下：aaaasdf11222333

​      3.  1.txt.r5  是别人赶在你之前提交的版本

​      内容如下： b

其中,<<<<<<<<.mine .....=======之间的代码是你自己的，而======......>>>>>>>.r5是别人与你冲突的代码部分

这样就不难理解为什么会产生冲突这种奇怪的东西了，因为你们修改的同一块代码，当然会产生冲突。

解决方案如下：

1. 假如我现在的1.txt中的冲突内容如下：

​      <<<<<<< .mine

​       6666666666666600000

​       =======

​      66666666666aaaaaaaaaa666

​      >>>>>>> .r16
​    前面说过  <<<<<<< .mine …… =======

​    ……之间的代码是我未产生冲突之前修改的代码，

​    ======= ………>>>>>>> .r16 这中间……的代码是别人与我冲突代码的部分，从上面的代码可以看到 aaaaaaaaa是我同事新增的 ,00000是我后增加的。

1. 使用revert(回滚)操作，该操作表示用户放弃自己的更新代码，然后直接提交，这个时候你的代码就会使服务器上最新的代码，即A用户提交的新代码，你的代码不会被提交，如下所示：

   ​

   ​

   点击ok按钮后 可以看到其他三个文件都自动删掉了，1.txt代码变成如下代码：

   66666666666aaaaaaaaaa666

   也就是a用户提交的代码，我自己更新的代码需要自己动手复制进去即可提交commit。

2. 假如我现在3.txt产生冲突代码如下：

   <<<<<<< .mine

   333333338888888888888=======

   3333cccccccccc3333>>>>>>> .r16

   通过第一点我们知道，333333338888888888888这个内容是我修改后，未产生冲突之前的内容，3333cccccccccc3333这个代码是A用户提交的代码，从上面得知 A用户新增内容是ccccccc，而我新增的内容是8888888。

   那么第二种解决方法如下：

​                    选择文件->右键Editconficts：这种方法需要冲突双方经过协商之后将代码更改统一之后再提交。不仅解决了冲突而且还保证了代码是正确的，因为只有一方的代码被提交.

​     ![img](https://images0.cnblogs.com/blog/561794/201409/131015325908149.png)

   如上图所示，红色的部分是冲突代码：theirs表示当前服务器端最新的代码，Mine表示自己修改后的代码，Merged表示合并后的代码。点击红色后右键选择：use this text block就可以将该部分代码作为合并后的代码

接下来再说说由于冲突导致重要代码被覆盖的情况。冲突发生时如果采取的措施不对可能会导致部分代码丢失，如果想要还原之前的代码也很容易。

选择文件->右键选择show log在这里面你可以看见之前提交的所有版本，找到你想要恢复的版本右键选择revert to this version 就可以恢复了.

SVN提交(SVN Commit)

​    Svn的提交是将在工作空间做的修改进行提交，包括文件内容的修改，文件或目录的添加，删除，命名，移动等操作。如下图所示:

   ![img](https://images0.cnblogs.com/blog/561794/201409/131016065274081.png)

  8.   显示日志(Show log)

​       通过此功能可以查到谁，什么时候，对那个目录下的那些文件进行了那些操作，如下图：

  ![img](https://images0.cnblogs.com/blog/561794/201409/131016571997100.png)

 9.  版本库浏览(Repo-browser)

​     此功能是用来浏览需要查看的资料库，在本地文件夹下点击右键，选择TortoiseSVNàRepo-browser,在弹出的对话框中输入资料库地址，再输入用户名和密码，就能查看到你需要查看到版本库的内容，在这你还能看到那些文件被谁锁定了，如下图：

   ![img](https://images0.cnblogs.com/blog/561794/201409/131017565593898.png)

三： 创建分支合并相互操作

   项目中为何要创建分支，及合并？

​      比如我现在项目所有的文件放在主干上(trunk)中，由于需求的变更，需要增加新的需求，但是我们主干上还要继续往下开发，在此我们可以新建一个分支，来做增加新的需求那一块，主干上继续开发，等分支上代码没有问题的时候，再合并到主干上来。

创建分支的最大的目的就是跟主线进行并行开发时候不影响主线的开发。

   如何操作？

​      假如我本地新建一个文件夹test下有2个文件夹trunk(存放主干上的代码)和branch(存放分支上的代码)，如下所示：

  ![img](https://images0.cnblogs.com/blog/561794/201409/131019523091470.png)

一：先提取主干上的代码。

   点击trunk --> 鼠标右键 --> 点击SVN Checkout --> 弹出一个对话框，如下图所示：

  ![img](https://images0.cnblogs.com/blog/561794/201409/131020229963162.png)

其中上面的URL是从服务器VisualSVN Server上获取的，如下所示：

 ![img](https://images0.cnblogs.com/blog/561794/201409/131021106529468.png)

  直接右键qianduan3 --> Copy URL to Clipboard 即可。

  其中qianduan3项目有如下文件，如下图所示：

![img](https://images0.cnblogs.com/blog/561794/201409/131021430904360.png)

最后点击上面的checkout按钮后，就可以在主干上把代码从远程服务器上获取到，如下所示：

 ![img](https://images0.cnblogs.com/blog/561794/201409/131022050432586.png)

二：新建分支

  从trunk（主干上）创建分支(branch)步骤如下：

  1. 右键trunk --> branch/Tag 如下图：

  ![img](https://images0.cnblogs.com/blog/561794/201409/131022528242622.jpg)

  在弹出的对话框如下图：

  ![img](https://images0.cnblogs.com/blog/561794/201409/131023226843499.jpg)

  点击ok按钮后，就可以在VisualSVN Serval服务器上新增newBranch，是从如上服务器qianduan3上的文件拷贝一份的，如下所示：

  ![img](https://images0.cnblogs.com/blog/561794/201409/131023477156652.png)

现在我们可以再来看看本地branch文件夹了，我现在直接进入branch文件下，右键 --> Chenckout下，就可以把newBranch下的所有文件提取出来了，如下所示：

 ![img](https://images0.cnblogs.com/blog/561794/201409/131024100745821.png)

![img](https://images0.cnblogs.com/blog/561794/201409/131024289968807.png)

点击ok按钮就可以把文件提取出来了，如下图所示：

![img](https://images0.cnblogs.com/blog/561794/201409/131024519655091.png)

分支目前建立在svn的服务器端，本地并没有更新，对本地branch文件夹 右键--> update即可，就可以更新到分支代码，如下所示：

![img](https://images0.cnblogs.com/blog/561794/201409/131025128569273.png)

四：合并分支到主干上

   比如我现在对branch分支上新增3.txt文件，然后提交上去，如下所示：

  ![img](https://images0.cnblogs.com/blog/561794/201409/131026181374296.png)

我现在想把分支上的代码3.txt合并到主干上trunk，现在要怎么合并呢？步骤如下：

  1. 回到我们刚刚的主干（trunk）文件夹下，鼠标右键该文件夹 --> TortoiseSVN --> Merge 如下图所示：

  ![img](https://images0.cnblogs.com/blog/561794/201409/131027053879661.jpg)

在弹出的窗口，如下图所示：

 ![img](https://images0.cnblogs.com/blog/561794/201409/131027387158880.jpg)

接着点击【Next】下一步，如下图所示：

![img](https://images0.cnblogs.com/blog/561794/201409/131028033098932.jpg)

再接着【Next】下一步，如下图所示：

![img](https://images0.cnblogs.com/blog/561794/201409/131028273408259.jpg)

 

![img](https://images0.cnblogs.com/blog/561794/201409/131028429349860.png)

就可以看到主干trunk上多加了一个3.txt，就是从分支上合并过来的。

五：合并主干到分支。

 如果主干上有一些更新，比如说jar包更新等等，那么这些要更新到分支上去，如何操作呢？比如我现在在主干上新建一个4.txt文件，比如如下：

 ![img](https://images0.cnblogs.com/blog/561794/201409/131029453409829.png)

我现在的分支上目录如下：

![img](https://images0.cnblogs.com/blog/561794/201409/131030012933089.png)

现在是想把主干上的4.txt合并到分支上来，要如何操作？

步骤如下，还是和刚刚操作类似.

 1. 我们在分支点击branch --> 右键TortoiseSVN --> Merge 如下图所示：

![img](https://images0.cnblogs.com/blog/561794/201409/131030374654605.jpg)

 

在弹出新窗口后，如下图所示：

![img](https://images0.cnblogs.com/blog/561794/201409/131030572623989.jpg)

接着点击【Next】下一步，如下图所示：

![img](https://images0.cnblogs.com/blog/561794/201409/131031194024159.jpg)

 

继续下一步，如下图：

![img](https://images0.cnblogs.com/blog/561794/201409/131031351991933.jpg)

最后直接merge，就可以看到分支branch上也有主干上的4.txt文件了，也就是说，合并主干到分支上也是可以的，如下图所示：

![img](https://images0.cnblogs.com/blog/561794/201409/131031508096763.png)