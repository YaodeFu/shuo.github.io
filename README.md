<img src="https://github.githubassets.com/assets/mona-loading-default-c3c7aad1282f.gif" width="64">

> 所有需要的文件：[访问密码：6ppw](https://wwboo.lanzouv.com/iB7dx3g8kpbe)

# 应用和命令解释

## 安装应用：
* **Http Canary** - 用于抓包，获取请求头
* **Termux:API** - 用于获取成功后的通知
* **ZeroTermux** - 后台持续获取成绩
* **MT管理器**（可选） - 用于方便地管理手机文件和修改Python源代码

## Termux换源：
`sed -i 's@^\(deb.*stable main\)$@#\1\ndeb https://mirrors.bfsu.edu.cn/termux/termux-packages-24 stable main@' $PREFIX/etc/apt/sources.list &&apt update && apt upgrade`

> 如果执行换源后下载依然很慢，就双击屏幕左边缘，切换源，北京源，即可

## 安装termux-api库：
`pkg install termux-api`

## 安装Python：
`pkg install python`

## 安装requests库：
`pip install requests`

## pip换源：
`pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple`
`pip config set global.trusted-host pypi.tuna.tsinghua.edu.cn`

---

# 正式配置

1. 安装所有软件，把 `AutoGetGrade.py` 放到熟悉的文件夹，比如 `/storage/emulated/0/Documents`，把所有软件该给的权限都给了。

2. 抓包获取 Header：
   * 打开 **HttpCanary**，点右下角的小飞机（开始抓包），授予建立VPN连接的权限。
   * 打开 **喜鹊儿**，找到原始成绩页，等成绩成功载出来后回到 **HttpCanary**。
   * 点小飞机（停止抓包），主页会有一些喜鹊儿图标的抓包内容。
   * 随便找一个查看：**请求 -> 预览**。
   * 把 `appsjxh`、`encrptSecretKey`、...、`token` 依次写入 `AutoGetGrade.py` 的对应位置并保存。

3. 打开 **Termux**，依次进行：
   * Termux换源
      > 如果执行换源后下载依然很慢，就双击屏幕左边缘，切换源，北京源，即可
   * 安装Python
   * 安装termux-api库
   * pip换源
   * 安装requests库

   **完整代码（逐行复制粘贴，不要长按识图，不要手动打）：**
   ```bash
   sed -i 's@^\(deb.*stable main\)$@#\1\ndeb https://mirrors.bfsu.edu.cn/termux/termux-packages-24 stable main@' $PREFIX/etc/apt/sources.list &&apt update && apt upgrade
   pkg install python
   pkg install termux-api
   pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
   pip config set global.trusted-host pypi.tuna.tsinghua.edu.cn
   pip install requests
   ```
   > 中途有时候需要输入y并回车

4. 如果一切顺利，就可以直接用了。打开 **Termux**，`cd` 到存放 `AutoGetGrade.py` 的目录，例如：
   `cd /storage/emulated/0/Documents`
   
   然后运行脚本：
   `python AutoGetGrade.py`
   
   能看到已经出的学科成绩并且收到了测试通知，就代表正常运行了，把 **Termux** 挂后台就行了。

5. 如果手滑关了 **Termux**，只需要重新执行第 4 步即可。
