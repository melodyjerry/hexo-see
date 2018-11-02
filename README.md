## 一、hexo-see简介

Python3 实现。

Hexo的可视化界面，摆脱命令行。

很粗糙，请见谅。

![](https://img-blog.csdnimg.cn/20181103004314533.png)

## 二、功能

#### 1、界面化创建文章！

![](https://img-blog.csdnimg.cn/2018110300433763.png)

#### 2、创建文章后可选择直接打开

![](https://img-blog.csdnimg.cn/20181103004448727.png)

#### 3、提交至远程仓库

![](https://img-blog.csdnimg.cn/20181103004517311.png)

#### 4、清除本地public文件

![](https://img-blog.csdnimg.cn/20181103004546939.png)

#### 5、开启本地服务

![](https://img-blog.csdnimg.cn/20181103004609249.png)



## 三、所用包

| 包        | 操作           |
| --------- | -------------- |
| tkinter   | 实现GUI界面    |
| os        | 进行命令操作   |
| threading | 进行多线程操作 |
| win32api  | 实现界面居中   |



## 四、按钮与命令的映射关系

| 按钮名称           | 对应命令             |
| ------------------ | -------------------- |
| 重新生成静态文件   | hexo g               |
| 清除本地public文件 | hexo clean           |
| 创建文章           | hexo n post  <title> |
| 提交仓库           | hexo d               |
| 本地预览           | hexo s               |
| 退出               | 退出本程序           |

## 五、使用

#### 配置

1. `tkinter`、`os`、`threading` 都是内置包，因此仅需安装 `win32api`，

   Python3 使用 `pip3 install pypiwin32`安装即可。

   > 如安装失败，请手动安装`whl`文件。
   >
   > `whl`文件源地址：https://www.lfd.uci.edu/~gohlke/pythonlibs/。

2. 更改 if \_\_name\_\_ == '\_\_main\_\_': 里初始化 Hexo 时的路径输入。

   改为自己博客 **站点配置根路径** 即可使用！

#### 使用说明

1. 输入 **标题、标签、分类** 直接创建！

   **标题** 不可为空！，**标签和分类** 可以为空。

   如果标题中出现 **空格** 会被替换掉。

2. **多个标签/多个分类使用空格分割！** **多个标签/多个分类使用空格分割！** **多个标签/多个分类使用空格分割！**

3. 如果想要使用 **.exe** 可执行文件，需自行转换（因为需要配置自己的路径）。

   可使用 **pyinstaller** 包进行转换，`pip install pyinstaller`。

   下面有关于本工具的打包说明。

4. 除本地预览为后台开启，其他都会有控制台出现，方便查看执行过程。

5. 本地预览暂时不支持关闭（因为是后台执行，虽然也不需要关，毕竟可以一直本地访问），

   即使程序退出，本地服务也不会关闭。

6. 因为本地服务有可能在后台运行，因此点击本地预览时将会使用`taskkill`杀掉 占用`4000`端口的服务，

   然后才开启`Hexo`本地服务。

## 六、exe 可执行程序转换说明

#### pyinstaller的参数说明

```python
-c 参数		使用控制台，无界面(默认)

-w 参数		使用窗口，无控制台.如果程序里有使用到控制台(如print)的就不可以使用-w,
			 否则会报错 '''failed to excute script xxx'''
			 如果想要捕捉错误信息可以先用控制台捕捉,没有报错后再使用无控制台.
        
-D 参数		创建一个目录，包含exe文件，但会依赖很多文件（默认选项）。

-F 参数		打包成一个exe文件

-p 			  多文件打包时,以-p [其他.py] 的形式跟在主文件后
		'''如:pyinstaller -w -F main.py -p view.py -p other.py'''

-i 参数 		修改打包后的exe图标,图标应放在py同级目录下,需要是ico格式,只改后缀不可用.
		'''如:pyinstaller -w -F -i zzz.ico main.py -p view.py -p other.py'''

```

#### 本程序的打包说明

1. 将配置完毕的 **Hexo.py** 与 **favicon.ico** 放在同一文件目录
2. 使用命令行进入文件目录
3. `pyinstaller -w -F -i favicon.ico Hexo.py`
4. 愉快使用

## 七、额外说明

本工具开源协议为 **不知道协议**，因为我还没有区分这些协议的意思……

总之，随便用，欢迎 `star`、 `fork`、`issue`。