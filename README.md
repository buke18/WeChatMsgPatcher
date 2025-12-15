
<p align="center">
	<a><img width="100px" src="https://raw.githubusercontent.com/huiyadanli/RevokeMsgPatcher/master/Images/logo.png"/></a>
</p>
<p align="center">
	<a href="https://www.microsoft.com/download/details.aspx?id=30653">
		<img src="https://img.shields.io/badge/platform-windows-lightgrey.svg?style=flat-square"/>
	</a>
	<a href="https://github.com/huiyadanli/RevokeMsgPatcher/releases">
		<img src="https://img.shields.io/github/downloads/huiyadanli/RevokeMsgPatcher/total.svg?style=flat-square"/>
	</a>
	<a href="https://ci.appveyor.com/project/huiyadanli/RevokeMsgPatcher">
		<img src="https://img.shields.io/appveyor/ci/huiyadanli/RevokeMsgPatcher.svg?style=flat-square"/>
	</a>
</p>

# 👀微信/QQ/TIM防撤回补丁
适用于 Windows 下 PC 版微信/QQ/TIM的防撤回补丁。**支持最新版微信/QQ/TIM**，其中微信能够选择安装多开功能。

<img width="180px" src="https://raw.githubusercontent.com/huiyadanli/RevokeMsgPatcher/master/Images/revoke.jpg"/>

下载地址：
**[⚡️点我下载最新版本](https://github.com/huiyadanli/RevokeMsgPatcher/releases/download/2.1/RevokeMsgPatcher.v2.1.zip)** |
[☁备用下载-蓝奏云](https://wwmy.lanzouq.com/b0fot7dpe)  密码:coco| 
[☁备用下载-百度云](https://pan.baidu.com/s/15ilr78t8F1-VW8eUZSkr_Q?pwd=3rrj) 

相关文档：
**[✔支持哪些版本](https://github.com/huiyadanli/RevokeMsgPatcher/wiki/%E7%89%88%E6%9C%AC%E6%94%AF%E6%8C%81)** | 
[❓常见问题](https://github.com/huiyadanli/RevokeMsgPatcher/wiki#%E5%B8%B8%E8%A7%81%E9%97%AE%E9%A2%98) | 
[📖查看完整文档](https://github.com/huiyadanli/RevokeMsgPatcher/wiki)

原理与方法：
[📗微信]
这是一个成果向教程，参考了一些网上的教程汇总而成。仅用于技术交流。

工具
x64dbg
一定的计算机相关知识
信息
通过网上各位大牛的研究，我们已经知道一下信息：

撤回、限制多开的逻辑都位于 WeChatWin.dll 文件中
撤回相关的关键词 revokemsg
多开相关的关键词 WeChat_App_Instance_Identity_Mutex_Name
调试
打开 x64dbg （32位用x32dbg，64位用x64dbg，现在新版本微信都是64位），点击 文件 -> 附加 点击 文件 -> 附加

附加微信的进程 附加微信的进程

切换到 符号 选项卡，在左下角搜索 WeChatWin.dll ，双击 wechatwin.dll 进入 CPU 选项卡 

右键 搜索 -> 当前区域 -> 字符串 

防撤回
直接搜索关键词 revokemsg，然后双击第一个"revokemsg"进入 

需要进行修改的是当前行的上面一行： je xxxxxx 

双击 je xxxxxx ，把 je 修改为 jmp 即可 修改为jmp 修改后

多开
直接搜索关键词 WeChat_App_Instance_Identity_Mutex_Name，然后双击第一个L"WeChat_App_Instance_Identity_Mutex_Name"进入 

需要进行修改的是当前行的上面第一个出现的 push ebp 

双击 push ebp ，把 push ebp 修改为 ret 即可 修改为jmp 修改后

生成补丁
点击生成补丁的按钮，然后点击修补文件就可以得到修改后的 WeChatWin.dll |

**（本人不参与方法寻找，仅做特征搬运）**

## 🔨使用方法

1. 首先，你的系统需要满足以下条件：

    * Windows 7 或更高版本，**不支持XP**。
    * [.NET Framework 4.5.2](https://www.microsoft.com/en-us/download/details.aspx?id=42642) 或更高版本。**低于此版本在打开程序时可能无反应，或者直接报错**。

2. 使用本程序前，先关闭微信

3. **以管理员身份运行本程序**

4. 选择微信的安装路径。如果你用的安装版的微信，正常情况下本程序会自动从注册表中获取安装路径，绿色版需要手动选择路径。

5. **由于修改了微信的 WeChatWin.dll 文件，杀毒软件可能会弹出警告，放行即可。**

注意：微信更新之后要重新安装补丁！

## 💡致谢

本项目早期内容源自 [wechat_anti_revoke](https://github.com/36huo/wechat_anti_revoke) 项目。

微信4.0版本后的防撤回特征来自于 [BetterWX](https://github.com/zetaloop/BetterWX)

## ❤️投喂

觉的好用的话，可以支持作者哟ヾ(･ω･`｡) 

## 📄License💡

![](https://raw.githubusercontent.com/huiyadanli/RevokeMsgPatcher/master/Images/give_a_star.png)
