# java

安装 Ali-Tomcat 和 Pandora
配置开发环境
安装 Ali-Tomcat 和 Pandora
Ali-Tomcat 和 Pandora 为 EDAS 中的服务运行时所依赖的容器，主要集成了服务的发布、订阅、调用链追踪等一系列的核心功能，无论是开发环境还是运行时，均必须将应用程序发布在该容器中。

注意：请使用 JDK 1.7及以上版本。

下载 Ali-Tomcat，保存后解压至相应的目录（如：d:\work\tomcat\）。

下载 Pandora 容器，保存后将内容解压至上述保存的 Ali-Tomcat 的 deploy 目录(d:\work\tomcat\deploy)下。

查看 Pandora 容器的目录结构。

Linux 系统中，在相应路径下执行 tree -L 2 deploy/ 命令查看目录结构。

d:\work\tomcat >  tree -L 2 deploy/
                       deploy/
                               └── taobao-hsf.sar
                                       ├── META-INF
                                       ├── lib
                                       ├── log.properties
                                       ├── plugins
                                       ├── sharedlib
                                       └── version.properties
Windows 中，直接进入相应路径进行查看。

Pandora 目录结构

如果您在安装和使用 Ali-Tomcat 和 Pandora 过程中遇到问题，请参见 Ali-Tomcat 问题和 Pandora 问题进行定位、解决。

配置开发环境
您在本地开发应用时，需要使用 Eclipse 或 IntelliJ IDEA。本节将分别介绍如何配置 Eclipse 或 IntelliJ IDEA 开发环境。

配置 Eclipse 环境
配置 Eclipse 需要下载 Tomcat4E 插件，并存放在安装 Ali-Tomcat 时 Pandora 容器的保存路径中，配置之后开发者可以直接在 Eclipse 中发布、调试本地代码。具体步骤如下：

下载 Tomcat4E 插件，并解压至本地（如：d:\work\tomcat4e\）。

压缩包内容如下：

Tomcat4E 目录结构

打开 Eclipse，在菜单栏中选择 Help > Install New Software。

在 Install 对话框中 Work with 区域右侧单击 Add，然后在弹出的 Add Repository 对话框中单击 Local。在弹出的对话框中选中已下载并解压的 Tomcat4E 插件的目录（d:\work\tomcat4e\）>，单击 OK。

返回 Install 对话框，单击 Select All，然后单击 Next。

后续还有几个步骤，按界面提示操作即可。安装完成后，Eclipse 需要重启，以使 Tomcant4E 插件生效。

重启 Eclipse。

重启后，在 Eclipse 菜单中选择 Run As > Run Configurations。

选择左侧导航选项中的 AliTomcat Webapp，单击上方的 New launch configuration 图标。

在弹出的界面中，选择 AliTomcat 页签，在 taobao-hsf.sar Location 区域单击 Browse，选择本地的 Pandora 路径，如：d:\work\tomcat\deploy\taobao-hsf.sar。

单击 Apply 或 Run，完成设置。

一个工程只需配置一次，下次可直接启动。

查看工程运行的打印信息，如果出现下图 Pandora Container 的相关信息，即说明 Eclipse 开发环境配置成功。

Pandora 容器打印信息

配置 IntelliJ IDEA 环境
注意：目前仅支持 IDEA 商业版，社区版暂不支持。所以，请确保本地安装了商业版 IDEA。

运行 IntelliJ IDEA。

从菜单栏中选择 Run > Edit Configuration。

在 Run/Debug Configuration 页面左侧的导航栏中选择 Defaults > Tomcat Server > Local。

配置 AliTomcat。

在右侧页面单击 Server 页签，然后在 Application Server 区域单击 Configure。

在 Application Server 页面右上角单击 +，然后在 Tomcat Server 对话框中设置 Tomcat Home 和 Tomcat base directory 路径，单击 OK。

将 Tomcat Home 的路径设置为本地解压后的 Ali-Tomcat 路径，Tomcat base directory 可以自动使用该路径，无需再设置。

在 Application Server 区域的下拉菜单中，选择刚刚配置好的 Ali-Tomcat。

在 VM Options 区域的文本框中，设置 JVM 启动参数指向 Pandora 的路径，如：-Dpandora.location=d:\work\tomcat\deploy\taobao-hsf.sar

说明：d:\work\tomcat\deploy\taobao-hsf.sar 需要替换为在本地安装 Pandora 的实际路径。

单击 Apply 或 OK 完成配置。
