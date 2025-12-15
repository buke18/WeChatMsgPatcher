
<p align="center">
	<a><img width="100px" src="https://raw.githubusercontent.com/huiyadanli/RevokeMsgPatcher/master/Images/logo.png"/></a>
</p>
<p align="center">
	<a href="https://www.microsoft.com/download/details.aspx?id=30653">
		<img src="https://img.shields.io/badge/platform-windows-lightgrey.svg?style=flat-square"/>
	</a>
	<a href="https://github.com/buke18/WeChatMsgPatcher/releases">
		<img src="https://img.shields.io/github/downloads/huiyadanli/RevokeMsgPatcher/total.svg?style=flat-square"/>
	</a>
	<a href="https://github.com/buke18/WeChatMsgPatcher">
		<img src="https://img.shields.io/appveyor/ci/huiyadanli/RevokeMsgPatcher.svg?style=flat-square"/>
	</a>
</p>

# 👀微信防撤回补丁
适用于 Windows 下 PC 版微信的防撤回补丁。**支持最新版微信**，而且能够选择支持多开的方式

![revoke](https://github.com/user-attachments/assets/4e77048f-b96b-4db2-b87c-31a580f85439)

下载地址：
**[⚡️点我下载最新版本](https://release-assets.githubusercontent.com/github-production-release-asset/1116956800/8195c102-c282-4cae-90d5-5bcef560619e?sp=r&sv=2018-11-09&sr=b&spr=https&se=2025-12-15T18%3A18%3A24Z&rscd=attachment%3B+filename%3D4.1.6.10.7z&rsct=application%2Foctet-stream&skoid=96c2d410-5711-43a1-aedd-ab1947aa7ab0&sktid=398a6654-997b-47e9-b12b-9515b896b4de&skt=2025-12-15T17%3A17%3A44Z&ske=2025-12-15T18%3A18%3A24Z&sks=b&skv=2018-11-09&sig=%2Fv7q%2FeQvO8fAlOuUEdivUdZ5XAVOtRSthCz%2FHFKE%2Fx4%3D&jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmVsZWFzZS1hc3NldHMuZ2l0aHVidXNlcmNvbnRlbnQuY29tIiwia2V5Ijoia2V5MSIsImV4cCI6MTc2NTgyMjI1OSwibmJmIjoxNzY1ODIwNDU5LCJwYXRoIjoicmVsZWFzZWFzc2V0cHJvZHVjdGlvbi5ibG9iLmNvcmUud2luZG93cy5uZXQifQ.MpRko5ldOhfz7V6BC-LlVAlITLxhv4s4tjSrRbejheQ&response-content-disposition=attachment%3B%20filename%3D4.1.6.10.7z&response-content-type=application%2Foctet-stream)** |


# **原理与方法❓❓❓**：
[📗微信]
这是一个成果向教程，参考了一些网上的教程汇总而成。仅用于技术交流。

# 一、工具
	[x64dbg]
	一定的计算机相关知识
# 二、信息
通过网上各位大牛的研究，我们已经知道一下信息：

	·撤回、限制多开的逻辑都位于 WeChatWin.dll | 文件中
	·撤回相关的关键词 revokemsg |
	·多开相关的关键词 WeChat_App_Instance_Identity_Mutex_Name |
# 三、调试
	1.打开 x64dbg （32位用x32dbg，64位用x64dbg，现在新版本微信都是64位），点击 文件 -> 附加 点击 文件 -> 附加
<img width="1198" height="655" alt="image" src="https://github.com/user-attachments/assets/a9bfec21-d7a6-4f24-8d2e-81f0a574eb59" />

	2.附加微信的进程 附加微信的进程
<img width="1198" height="655" alt="image" src="https://github.com/user-attachments/assets/61af41b5-4308-46a5-b474-2e7749be89e9" />

	3.切换到 符号 选项卡，在左下角搜索 WeChatWin.dll ，双击 wechatwin.dll 进入 CPU 选项卡 
<img width="1198" height="655" alt="image" src="https://github.com/user-attachments/assets/7293a7c9-9111-4933-8d28-39a7d8d9bd56" />

	4.右键 搜索 -> 当前区域 -> 字符串 
<img width="1198" height="749" alt="image" src="https://github.com/user-attachments/assets/4e12b00e-a404-48a1-8edc-8fc87f8df2c0" />

# 四、防撤回
	5.直接搜索关键词 revokemsg，然后双击第一个"revokemsg"进入 
<img width="1198" height="655" alt="image" src="https://github.com/user-attachments/assets/39c755a1-3b2e-41d4-94ff-fd5a8e434627" />

	6.需要进行修改的是当前行的上面一行： je xxxxxx 
<img width="1198" height="655" alt="image" src="https://github.com/user-attachments/assets/a00aa435-c3f0-46c2-90e1-3a61df605b75" />

	7.双击 je xxxxxx ，把 je 修改为 jmp 即可 修改为jmp 修改后
<img width="1198" height="655" alt="image" src="https://github.com/user-attachments/assets/a6b0af6b-91b4-4a78-9498-e48c08ba4d3d" />
<img width="1198" height="655" alt="image" src="https://github.com/user-attachments/assets/e6eff17f-4bde-45dc-bd00-8f3ec02d1267" />

# 五、多开
	8.直接搜索关键词 WeChat_App_Instance_Identity_Mutex_Name，然后双击第一个L"WeChat_App_Instance_Identity_Mutex_Name"进入 
<img width="1198" height="655" alt="image" src="https://github.com/user-attachments/assets/6a836b52-5e9c-4589-a768-69a1eeed7225" />

	9.需要进行修改的是当前行的上面第一个出现的 push ebp 
<img width="1198" height="655" alt="image" src="https://github.com/user-attachments/assets/cd9a0420-ac90-4ac8-8a33-85a49df9dcef" />

	10.双击 push ebp ，把 push ebp 修改为 ret 即可 修改为jmp 修改后
<img width="1198" height="655" alt="image" src="https://github.com/user-attachments/assets/eebffb74-ea6a-4342-9448-c6cd7bbaaa96" />
<img width="1198" height="655" alt="image" src="https://github.com/user-attachments/assets/2e002122-54ba-4089-857e-ea731efe8a88" />

# 六、生成补丁
	11.点击生成补丁的按钮，然后点击修补文件就可以得到修改后的 WeChatWin.dll |
<img width="1198" height="655" alt="image" src="https://github.com/user-attachments/assets/cfee4d4a-56a6-4a24-898c-5a719b075507" />


## 🔨dll插件使用方法📖

1. 首先，你的系统需要满足以下条件：

    * Windows 7 或更高版本，**不支持XP**。
    * [.NET Framework 4.5.2](https://www.microsoft.com/en-us/download/details.aspx?id=42642) 或更高版本。**低于此版本在打开程序时可能无反应，或者直接报错**。

2. 使用本程序前，先关闭微信

3. **以管理员身份运行本程序**

4. 选择微信的安装路径。如果你用的安装版的微信，正常情况下本程序会自动从注册表中获取安装路径，绿色版需要手动选择路径。
<img width="781" height="345" alt="image" src="https://github.com/user-attachments/assets/196ec83d-ac96-49d6-a34c-15c8a64758ca" />
<img width="1095" height="845" alt="image" src="https://github.com/user-attachments/assets/b85daf0a-8c45-47fb-be25-83bd2450202e" />


5. **由于修改了微信的 WeChatWin.dll 文件，杀毒软件可能会弹出警告，放行即可。**

注意：微信更新之后要重新安装补丁！

## 💡致谢

本项目早期内容源自 [wechat_anti_revoke](https://github.com/36huo/wechat_anti_revoke) 项目。

微信4.0版本后的防撤回特征来自于 [BetterWX](https://github.com/zetaloop/BetterWX)

## ❤️投喂

觉的好用的话，可以支持作者哟ヾ(･ω･`｡) 
![](https://raw.githubusercontent.com/huiyadanli/RevokeMsgPatcher/master/Images/give_a_star.png)
