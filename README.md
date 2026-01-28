<img src="https://github.githubassets.com/assets/mona-loading-default-c3c7aad1282f.gif" width="64">

# 下载

Windows端：从[GitHub Release](https://github.com/YaodeFu/Auto_Get_TJNU_Grade/releases)中下载`AutoGetTJNUGrade.py`

---

# 安装Python
Python官网：[www.python.org](https://www.python.org)

下载对应电脑版本的安装包，安装时务必勾选`Add Python.exe to PATH`，如下图：

![勾选Add Python.exe to PATH](./inst_python.png)

---

# 检验Python的安装
在开始菜单中搜索`命令提示符`，并`以管理员身份运行`，在打开的窗口中输入`pip`并回车，若显示类似的提示：
```
Usage:
  pip <command> [options]

Commands:
  install                     Install packages.
  lock                        Generate a lock file.
  download                    Download packages.
  uninstall                   Uninstall packages.
  freeze                      Output installed packages in requirements format.
  inspect                     Inspect the python environment.
  list                        List installed packages.
  show                        Show information about installed packages.
  check                       Verify installed packages have compatible dependencies.
  config                      Manage local and global configuration.
  search                      Search PyPI for packages.
  cache                       Inspect and manage pip's wheel cache.
  index                       Inspect information available from package indexes.
  wheel                       Build wheels from your requirements.
  hash                        Compute hashes of package archives.
  completion                  A helper command used for command completion.
  debug                       Show information useful for debugging.
  help                        Show help for commands.

General Options:
  -h, --help                  Show help.
  --debug                     Let unhandled exceptions propagate outside the main subroutine, instead of logging them
                              to stderr.
  --isolated                  Run pip in an isolated mode, ignoring environment variables and user configuration.
  --require-virtualenv        Allow pip to only run in a virtual environment; exit with an error otherwise.
  --python <python>           Run pip with the specified Python interpreter.
  -v, --verbose               Give more output. Option is additive, and can be used up to 3 times.
  -V, --version               Show version and exit.
  -q, --quiet                 Give less output. Option is additive, and can be used up to 3 times (corresponding to
                              WARNING, ERROR, and CRITICAL logging levels).
  --log <path>                Path to a verbose appending log.
  --no-input                  Disable prompting for input.
  --keyring-provider <keyring_provider>
                              Enable the credential lookup via the keyring library if user input is allowed. Specify
                              which mechanism to use [auto, disabled, import, subprocess]. (default: auto)
  --proxy <proxy>             Specify a proxy in the form scheme://[user:passwd@]proxy.server:port.
  --retries <retries>         Maximum attempts to establish a new HTTP connection. (default: 5)
  --timeout <sec>             Set the socket timeout (default 15 seconds).
  --exists-action <action>    Default action when a path already exists: (s)witch, (i)gnore, (w)ipe, (b)ackup,
                              (a)bort.
  --trusted-host <hostname>   Mark this host or host:port pair as trusted, even though it does not have valid or any
                              HTTPS.
  --cert <path>               Path to PEM-encoded CA certificate bundle. If provided, overrides the default. See 'SSL
                              Certificate Verification' in pip documentation for more information.
  --client-cert <path>        Path to SSL client certificate, a single file containing the private key and the
                              certificate in PEM format.
  --cache-dir <dir>           Store the cache data in <dir>.
  --no-cache-dir              Disable the cache.
  --disable-pip-version-check
                              Don't periodically check PyPI to determine whether a new version of pip is available for
                              download. Implied with --no-index.
  --no-color                  Suppress colored output.
  --use-feature <feature>     Enable new functionality, that may be backward incompatible.
  --use-deprecated <feature>  Enable deprecated functionality, that will be removed in the future.
  --resume-retries <resume_retries>
                              Maximum attempts to resume or restart an incomplete download. (default: 5)
```

即说明安装正确。

---

# 安装运行库

## pip换源

在国内，pip的官方源下载速度非常慢，建议换为第三方高速下载源，可自行搜索，这里推荐`清华源`。

在刚刚的黑色窗口中输入以下内容并回车：

```
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
pip config set global.trusted-host pypi.tuna.tsinghua.edu.cn
```

## 正式安装

在刚刚的黑色窗口中输入以下内容并回车：

```bash
pip install requests bs4 prettytable playwright
playwright install chromium
```

等待进度条跑完后，即安装完成。

---

# 程序配置

直接双击打开`AutoGetTJNUGrade.py`文件，会提示：

```
[*] 首次运行：已生成 config.ini
[!] 请先在配置文件中填写 [USER] 部分的学号和密码，然后重新运行。
请按任意键继续. . .
```

此时，运行目录中会生成一个名为`config.ini`的文件，双击打开它：

```ini
# ============================================================
# 使用说明：
# 1. 只需要配置 [USER] 层级下的 username(学号) 和 password(密码)
# 2. [PATH] 下的 audio_path 为成绩更新时的提醒铃声路径
# 3. [AUTH] 和 [DATA] 层级下的内容由脚本自动维护，请勿随意修改
# ============================================================

[USER]
username = 
password = 

[PATH]
audio_path = D:\sunrise.wav

[AUTH]
cookie = 

[DATA]
payload = sjxz=sjxz3&ysyx=yscj&zx=1&fx=1&rxnj=2025&btnExport=%%B5%%BC%%B3%%F6&xn=2025&xn1=2026&xq=0&ysyxS=on&sjxzS=on&zxC=on&fxC=on&xsjd=1&menucode_current=S40303
```

在`username = `后填入你的学号，在`password = `后填入你的密码，其他**不要配置**，保存文件。

再次运行，会进行首次登录，什么都无需操作，等待自动执行完成即可。

> 小提示：当检测到成绩更新时，会自动播放一段音频，音频可以自定义，在`config.ini`的`audio_path`条目修改，默认为`D:\sunrise.wav`，如果文件不存在或没有配置则不会播放。

## 许可证

MIT License © 2026 [YaodeFu]

详见 [LICENSE](LICENSE) 文件。

**EOF**
