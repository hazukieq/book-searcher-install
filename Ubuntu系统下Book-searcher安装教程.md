#### Ubuntu系统下 Book-searcher 安装教程

1. 前往 [Book-searcher 开源项目 Release 页面](https://github.com/book-searcher-org/book-searcher/releases) 下载后缀名为 `amd64.deb` 的安装包

   **注：请记住安装包下载路径，稍后会用到**

   > 如果还没有安装有 wget 工具，可使用 `sudo apt install wget` 命令进行安装

   ```shell
   # 可在终端上运行以下命令下载安装包
   wget https://github.com/book-searcher-org/book-searcher/releases/download/0.9.1/Book-Searcher-desktop_0.9.1_amd64.deb
   ```

   

2. 安装 Book_searcher安装包

   ```shell
   sudo dpkg -i Book_searcher安装包路径
   ```

   

3. 下载 `Zlibrary 书籍索引文件`，对应项目链接：https://github.com/zlib-searcher-new/index

   **注意：所有索引分块文件必须同一个文件夹目录下，否则可能会解压失败**

   ```shell
   # 你可以使用 wget,curl,axel工具
   # 在这里我将使用 axel 演示如何下载索引文件
   # 由于索引文件被作者分卷压缩成14个文件，所以我们需要下载完所有的索引分块压缩包
   axel -n 20 https://github.com/zlib-searcher-new/index/releases/download/0.9.1/index-0.9.1.z01
   axel -n 20 https://github.com/zlib-searcher-new/index/releases/download/0.9.1/index-0.9.1.z02
   axel -n 20 https://github.com/zlib-searcher-new/index/releases/download/0.9.1/index-0.9.1.z03
   axel -n 20 https://github.com/zlib-searcher-new/index/releases/download/0.9.1/index-0.9.1.z04
   axel -n 20 https://github.com/zlib-searcher-new/index/releases/download/0.9.1/index-0.9.1.z05
   axel -n 20 https://github.com/zlib-searcher-new/index/releases/download/0.9.1/index-0.9.1.z06
   axel -n 20 https://github.com/zlib-searcher-new/index/releases/download/0.9.1/index-0.9.1.z07
   axel -n 20 https://github.com/zlib-searcher-new/index/releases/download/0.9.1/index-0.9.1.z08
   axel -n 20 https://github.com/zlib-searcher-new/index/releases/download/0.9.1/index-0.9.1.z09
   axel -n 20 https://github.com/zlib-searcher-new/index/releases/download/0.9.1/index-0.9.1.z10
   axel -n 20 https://github.com/zlib-searcher-new/index/releases/download/0.9.1/index-0.9.1.z11
   axel -n 20 https://github.com/zlib-searcher-new/index/releases/download/0.9.1/index-0.9.1.z12
   axel -n 20 https://github.com/zlib-searcher-new/index/releases/download/0.9.1/index-0.9.1.z13
   axel -n 20 https://github.com/zlib-searcher-new/index/releases/download/0.9.1/index-0.9.1.zip
   ```

​	 注意：下载网速可能会不太稳定(下载时间视个人网络环境)，反正我在这里卡了挺久的......所以一定要有耐心\^_\^

​	下载完后，列表如下：	![image-20230528123204382](/home/hazukie/gitprojects/book-searcher-install/image-20230528123204382.png)

​	

4. 创建索引目录，解压缩索引文件

   >  这里需要用到 7zip 解压缩工具，如果你没有安装，可以使用 `sudo apt install p7zip-full` 安装 7zip 工具

   ```shell
   # 建立索引目录(文件存储位置可选)
   mkdir 索引目录存储路径
   cd 索引目录存储路径
   
   # 解压缩索引文件
   #-o和导出路径是相连接的!
   7za e index-0.9.1.zip -o索引目录存储路径
   ```

   运行解压命令，输出信息以下：

   ![image-20230528123727279](/home/hazukie/gitprojects/book-searcher-install/image-20230528123727279.png)



4. 运行 Book-searcher，配置索引、IPFS网关

   > Book-searcher 安装成功的话，你可以在桌面上找到该软件。
   >
   > 你也可以使用 `book-searcher &` 命令运行

- 配置索引，选择刚才你创建的索引目录

  ![image-20230528122511359](/home/hazukie/gitprojects/book-searcher-install/image-20230528122511359.png)

  

- 配置 IPFS 网关，IPFS网关的作用是生成下载链接。请复制以下链接，粘贴到 软件中的网关配置处

  ```shell
  http://cloudflare-ipfs.com  
  http://ipfs.io  
  http://dweb.link  
  http://gateway.pinata.cloud  
  https://ipfs.best-practice.se
  ```

  

  ![IPFS网关配置结果](/home/hazukie/gitprojects/book-searcher-install/image-20230528121924597.png)



6.  待上面配置完成后，重启软件后测试一下配置是否生效

   ![image-20230528122801730](/home/hazukie/gitprojects/book-searcher-install/image-20230528122801730.png)

   
