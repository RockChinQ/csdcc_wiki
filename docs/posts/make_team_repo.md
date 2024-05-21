# 创建队伍代码仓库（队长操作）

需要先保证队长已经在 GitLab 上登录了账号，并且已经获取了 Access Token 及配置好了 Git。  
以下以数据库管理系统赛道为例。

## 配置仓库代码内容

<img src="assets/make_team_repo_01.png" alt="Fork" width="300"/>

在详情页，选择你的队伍空间作为 Namespace，可以按需修改 Project Name 和 Project Slug 以及描述，然后点击 Fork 项目。

<img src="assets/make_team_repo_02.png" alt="Fork" width="300"/>

点击 clone，复制你的仓库地址。

<img src="assets/make_team_repo_03.png" alt="Fork" width="300"/>

到自己的环境上（按照主办方要求配置一下，一般是 Ubuntu + vscode），打开终端，clone你的仓库。用vscode打开。

<img src="assets/make_team_repo_04.png" alt="Fork" width="300"/>

<img src="assets/make_team_repo_05.png" alt="Fork" width="300"/>

删掉根目录的那几个 PDF 和 README.md，把 `rmdb` 目录下的所有文件移到根目录下。

<img src="assets/make_team_repo_06.png" alt="Fork" width="300"/>

PDF 和 图片这种二进制也可以删了，只留下代码文件，需要看PDF的话，去原仓库就好了。

<img src="assets/make_team_repo_07.png" alt="Fork" width="300"/>

切到左边的 Git 的 Tab，暂存所有更改，写个 commit message，提交，然后推送。

<img src="assets/make_team_repo_08.png" alt="Fork" width="300"/>

<img src="assets/make_team_repo_09.png" alt="Fork" width="300"/>

推送的时候可能会让你输入账号密码，账号和密码都填你在 GitLab 上获取的 Access Token。

可以看到你的仓库的文件已经更新了。

<img src="assets/make_team_repo_10.png" alt="Fork" width="300"/>

## 额外的配置

### .gitignore

建议在项目根目录加一个 `.gitignore`，写入以下内容：

```gitignore
/build
/rmdb_client/build
.vscode
```

这样将排除不应该被提交的、编译生成的文件。

### 有用的脚本

以下脚本将编译rmdb服务端并在编译成功后启动。  
可以保存到项目根目录的`br_rmdb.sh`，加权限`chmod +x br_rmdb.sh`，然后执行`./br_rmdb.sh`。

```bash
cd build
cmake ..
make rmdb -j8 && echo "加载数据库文件：" && echo $1 && ./bin/rmdb $1 || { echo "构建失败"; exit 1; }
```

## 添加队员作为开发者

到你仓库的 GitLab 页面，点击左侧`Project Information`，然后点击`Members`，添加队员。

<img src="assets/make_team_repo_11.png" alt="Fork" width="300"/>

直接授权给 owner 方便一些，这样队友都可以更改仓库了。
