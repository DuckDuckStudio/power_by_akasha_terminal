# Powered by 虚空终端

![展示图](https://duckduckstudio.github.io/powered_by_akasha_terminal/Powered_by_虚空终端.png)

把你的Windows终端变成虚空终端！<br>
~~玩__玩的~~<br>
LICENSE: MIT<br>

> [!NOTE]
> 本项目原名[Power by 虚空终端]。但在后续发现，似乎不是`Power by`而是`Powered by`(这下尴尬了)<br>
> 随机即按项目Issues #1的建议将项目修改为了[Powered by 虚空终端]<br>
> 感谢哔哩哔哩上的网友的指出，也感谢UP主[鸭鸭_カモ](https://space.bilibili.com/2054654702)对本项目的介绍！<br>
> ~~发疯时写的项目，自然容易出错。一看就是整天想着 **“This, is power!”** 导致的。~~<br>
> 如有因项目名称修改导致的链接失效，请提交 Issues .<br>

中文 | [English](https://github.com/DuckDuckStudio/powered_by_akasha_terminal/blob/main/README_EN.md)

## 实现效果

[PowerShell中]<br>
![PowerShell中的效果展示图](https://duckduckstudio.github.io/powered_by_akasha_terminal/PowerShell中的效果展示图.png)<br>

[cmd中]<br>
![cmd中的效果展示图](https://duckduckstudio.github.io/powered_by_akasha_terminal/cmd中的效果展示图.png)<br>

## 如何实现

### PowerShell
* 永久<br>
  * 原先没有配置文件<br>
    你可以下载[仓库发行版](https://duckduckstudio.github.io/powered_by_akasha_terminal/releases/)中的`Microsoft.PowerShell_profile.ps1`，然后将这个文件放在`C:\Users\user_name\Documents\WindowsPowerShell\`中。(文件夹不存在的话就新建文件夹)<br>
      如果希望一并修改标题的话可以加上：<br>
      ```powershell
      $host.UI.RawUI.WindowTitle = "虚空终端"
      ```
      * 如果出现错误<br><div id="if-error"></div>
      如果出现类似这样的错误：<br>
      ```
      . : File C:\Users\user_name\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1 cannot be loaded because running scripts is disabled on this system. For more information, see about_Execution_Policies at https:/go.microsoft.com/fwlink/?LinkID=135170.
      ```
      请尝试：<br>
        * 以管理员身份启动 PowerShell<br>
        * 运行以下命令以查看当前的执行策略：<br>
      ```powershell
      Get-ExecutionPolicy
      ```
      如果返回的结果不是 `RemoteSigned` 或 `Unrestricted`，则表示 PowerShell 正在运行限制了脚本执行的执行策略。你可以使用以下命令来更改执行策略：<br>
      ```powershell
      Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
      ```
      这将允许当前用户在本地运行自签名的脚本文件，而不会询问用户确认。<br>
      最后，重新启动 PowerShell 应该就可以解决这个问题了。<br>
      * 如果遇到其他错误请提交 Issues<br>
      * 如果你是从项目[中文git](https://github.com/DuckDuckStudio/Chinese_git/)来的，到这里你就该回去了，Issues也请不要提交到这个项目上，请提交到中文git的Issues上。<br>
      [点我快速返回 中文git 项目](https://github.com/DuckDuckStudio/Chinese_git/blob/main/README.md#tp-point)<br>
  * 原先存在配置文件<br>
  你可以运行以下命令打开 PowerShell 的配置文件：<br>
  ```powershell
  notepad $PROFILE
  ```
  在打开的配置文件中添加以下代码：
  ```powershell
  function prompt {
    Write-Host "[Powered by 虚空终端] " -NoNewline -ForegroundColor Cyan
    return "PS $($executionContext.SessionState.Path.CurrentLocation)$('>' * ($nestedPromptLevel + 1)) "
  }
  # Code by DuckStudio
  # Version 1.1
  ```
  保存并关闭配置文件后重启 PowerShell 即可<br>
  如果希望一并修改标题的话可以加上：<br>
  ```powershell
  $host.UI.RawUI.WindowTitle = "虚空终端"
  ```
* 一次性<br>
如果你不想每次都有`[Powered by 虚空终端]`，只想要当前的 PowerShell 有`[Powered by 虚空终端]`，则你可以在 PowerShell 中运行以下指令：
```powershell
function prompt {
  Write-Host "[Powered by 虚空终端] " -NoNewline -ForegroundColor Cyan
  return "PS $($executionContext.SessionState.Path.CurrentLocation)$('>' * ($nestedPromptLevel + 1)) "
}
# Code by DuckStudio
# Version 1.1
# 注意：这是多行代码
```
如果希望一并修改标题的话可以加上：<br>
```powershell
$host.UI.RawUI.WindowTitle = "虚空终端"
```
这只会在当前 PowerShell 会话中有效。<br>

### cmd

* 一次性<br>
如果你不想每次都有`[Powered by 虚空终端]`，只想要当前的 cmd 有`[Powered by 虚空终端]`，则你可以在 cmd 中运行以下指令：<br>
```bash
prompt [Powered by 虚空终端] $P$G
```
如果希望一并修改标题的话可以加上：<br>
```bash
title 虚空终端
```
这只会在当前 cmd 会话中有效。<br>

## 如果设置为永久该如何取消

1. 运行以下命令打开 PowerShell 的配置文件：<br>
  ```powershell
  notepad $PROFILE
  ```
2. 删除在配置文件中添加的代码<br>
3. 保存并关闭配置文件后重启 PowerShell 即可<br>

## 如何修改内容

~~什么？！你竟然不喜欢虚空终端？！~~<br>
修改代码中的`[Powered by 虚空终端] `部分即可<br>

> [!NOTE]
> 需要注意的是，PowerShell 的代码在内容的后面还有一个空格<br>

例如：<br>
* 在 PowerShell 中<br>
```powershell
function prompt {
    Write-Host "[Powered by 纳西妲] " -NoNewline -ForegroundColor Cyan
    return "PS $($executionContext.SessionState.Path.CurrentLocation)$('>' * ($nestedPromptLevel + 1)) "
}
# Code by DuckStudio
# Version 1.1
# 注意：这是多行代码
```
效果：<br>
![Powered by 纳西妲](https://duckduckstudio.github.io/powered_by_akasha_terminal/PowerShell-纳西妲.png)<br>
* 在 cmd 中<br>
```bash
prompt [Powered by 纳西妲] $P$G
```
效果：<br>
![Powered by 纳西妲](https://duckduckstudio.github.io/powered_by_akasha_terminal/cmd-纳西妲.png)<br>

## 关于翻译

为什么不翻译`[Powered by]`?<br>
我保留了一部分英语，这样你才能知道你用的是终端(<br>
