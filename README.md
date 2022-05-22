@echo off
>nul 2>&1 "%SYSTEMROOT%\system32\cacls.exe" "%SYSTEMROOT%\system32\config\system"
if '%errorlevel%' NEQ '0' (
echo 正在请求管理员权限...使用前请关闭杀毒软件
goto UACPrompt
) else ( goto gotAdmin )
:UACPrompt
echo Set UAC = CreateObject^("Shell.Application"^) > "%temp%\getadmin.vbs"
echo UAC.ShellExecute "%~s0", "", "", "runas", 1 >> "%temp%\getadmin.vbs"
"%temp%\getadmin.vbs"
exit /B
:gotAdmin
::bilibili 果子狸的荔枝果

:B1
@echo off
color 3F
echo %username% 已获取管理员权限
echo.
title windows 10优化工具
echo 【功能说明】
echo 本脚本通过注册表优化win10
echo.
echo 【特别提醒】
echo 使用前请关闭杀毒软件或允许执行。
echo.
echo 第一页
echo 此页为禁用服务。
echo 【功能】
echo (1)全部执行
echo (2)禁用超级预缓存服务、索引服务、感知服务、备份服务和用户体验
echo (3)禁用windows应用商店及所需组件 
echo (4)禁用Xbox及组件
echo (5)禁用windows defender服务以及防火墙
echo (6)禁用windows更新、BITS及备份
echo (7)禁用windows诊断以及传递优化
echo (8)禁用Cortana小娜
echo (9)下一页
echo 当前时间为：
echo %date%
echo.

:on
cd /d %~dp0
choice /c 123456789 /m "请输入编号：(1)全部执行；(2)禁用超级预缓存服务，索引服务，感知服务，备份服务和用户体验；(3)禁用windows应用商店及所需组件；(4)禁用Xbox及组件；(5)禁用windows defender服务以及防火墙；(6)禁用windows更新、BITS及备份；(7)禁用windows诊断以及传递优化；(8)禁用Cortana小娜；(9)下一页；"
if %errorlevel%==1 goto N1
if %errorlevel%==2 goto N2
if %errorlevel%==3 goto N3
if %errorlevel%==4 goto N4
if %errorlevel%==5 goto N5
if %errorlevel%==6 goto N6
if %errorlevel%==7 goto N7
if %errorlevel%==8 goto N8
if %errorlevel%==9 goto NN9


:N1
choice /c 12 /m "你确定执行以上操作吗？：(1)确定执行；(2)我手滑了QAQ；"
if %errorlevel%==1 goto NN1
if %errorlevel%==2 goto NN2


:NN2
cls
goto B1

:NN1
cls
echo //禁用超级预缓存服务，索引服务，感知服务，备份服务和用户体验。
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SysMain" /v  "start" /t reg_dword /d "4" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WSearch" /v  "start" /t reg_dword /d "4" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\spectrum" /v  "start" /t reg_dword /d "4" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SDRSVC" /v  "start" /t reg_dword /d "4" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\DiagTrack" /v  "start" /t reg_dword /d "4" /f


echo //禁用windows应用商店及所需组件。(禁用后无法使用windows商店一些功能)
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\AppXSvc" /v  "start" /t reg_dword /d "4" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\AppVClient" /v  "start" /t reg_dword /d "4" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\InstallService" /v  "start" /t reg_dword /d "4" /f


echo //禁用Xbox及组件。(禁用后无法使用Xbox商店一些功能)
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\xbgm" /v  "start" /t reg_dword /d "4" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\XblAuthManager" /v  "start" /t reg_dword /d "4" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\XblGameSave" /v  "start" /t reg_dword /d "4" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\xboxgip" /v  "start" /t reg_dword /d "4" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\XboxGipSvc" /v  "start" /t reg_dword /d "4" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\XboxNetApiSvc" /v  "start" /t reg_dword /d "4" /f


echo //禁用windows defender服务。(禁用后可能导致病毒入侵)
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SecurityHealthService" /v  "start" /t reg_dword /d "4" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Sense" /v  "start" /t reg_dword /d "4" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WdNisSvc" /v  "start" /t reg_dword /d "4" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WinDefend" /v  "start" /t reg_dword /d "4" /f


echo //禁用防火墙。(禁用后可能导致病毒入侵)
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\mpssvc" /v  "start" /t reg_dword /d "4" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\wscsvc" /v  "start" /t reg_dword /d "4" /f


echo //禁用windows更新。
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\UsoSvc " /v  "start" /t reg_dword /d "4" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\wuauserv" /v  "start" /t reg_dword /d "4" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WaaSMedicSvc" /v  "start" /t reg_dword /d "4" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\wuauserv" /v  "WOW64" /t reg_dword /d "332" /f 
echo //禁用windows备份。
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SDRSVC" /v  "start" /t reg_dword /d "4" /f
echo //禁用BITS。
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BITS" /v  "start" /t reg_dword /d "4" /f


echo //禁用windows诊断以及传递优化(如禁用，则软件崩溃情况下不会出现恢复框，办公党慎用)
net stop WdiServiceHost
net stop WdiSystemHost
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\DoSvc" /v  "start" /t reg_dword /d "4" /f
net stop DPS


echo //禁用Cortana小娜，可能会导致相关功能不可用，恢复脚本可重新打开。
echo y|reg delete "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\Windows Search" 
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\Windows Search" 
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\Windows Search" /v  "AllowCortana" /t reg_dword /d "0" /f 

goto on


:N2
echo //禁用超级预缓存服务，索引服务，感知服务，备份服务。
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SysMain" /v  "start" /t reg_dword /d "4" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WSearch" /v  "start" /t reg_dword /d "4" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\spectrum" /v  "start" /t reg_dword /d "4" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SDRSVC" /v  "start" /t reg_dword /d "4" /f
goto on


:N3
echo //禁用windows应用商店及所需组件。(禁用后无法使用windows商店一些功能)
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\AppXSvc" /v  "start" /t reg_dword /d "4" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\AppVClient" /v  "start" /t reg_dword /d "4" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\InstallService" /v  "start" /t reg_dword /d "4" /f
goto on


:N4
echo //禁用Xbox及组件。(禁用后无法使用Xbox商店一些功能)
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\xbgm" /v  "start" /t reg_dword /d "4" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\XblAuthManager" /v  "start" /t reg_dword /d "4" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\XblGameSave" /v  "start" /t reg_dword /d "4" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\xboxgip" /v  "start" /t reg_dword /d "4" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\XboxGipSvc" /v  "start" /t reg_dword /d "4" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\XboxNetApiSvc" /v  "start" /t reg_dword /d "4" /f
goto on



:N5
echo //禁用windows defender服务。(禁用后可能导致病毒入侵)
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SecurityHealthService" /v  "start" /t reg_dword /d "4" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Sense" /v  "start" /t reg_dword /d "4" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WdNisSvc" /v  "start" /t reg_dword /d "4" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WinDefend" /v  "start" /t reg_dword /d "4" /f
echo //禁用防火墙。(禁用后可能导致病毒入侵)
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\mpssvc" /v  "start" /t reg_dword /d "4" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\wscsvc" /v  "start" /t reg_dword /d "4" /f
goto on


:N6
echo //禁用windows更新。
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\UsoSvc " /v  "start" /t reg_dword /d "4" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\wuauserv" /v  "start" /t reg_dword /d "4" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WaaSMedicSvc" /v  "start" /t reg_dword /d "4" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\wuauserv" /v  "WOW64" /t reg_dword /d "332" /f 
echo //禁用windows备份。
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SDRSVC" /v  "start" /t reg_dword /d "4" /f
echo //禁用BITS。
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BITS" /v  "start" /t reg_dword /d "4" /f

goto on


:N7
echo //禁用windows诊断以及传递优化(如禁用，则软件崩溃情况下不会出现恢复框，办公党慎用)
net stop WdiServiceHost
net stop WdiSystemHost
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\DoSvc" /v  "start" /t reg_dword /d "4" /f
net stop DPS
goto on

:N8
echo //禁用Cortana小娜，可能会导致相关功能不可用，恢复脚本可重新打开。
echo y|reg delete "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\Windows Search" 
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\Windows Search" 
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\Windows Search" /v  "AllowCortana" /t reg_dword /d "0" /f 
goto on

:NN9
cls
echo 【特别提醒】
echo 第二页操作无恢复功能。
echo (3)选项不要过多使用。
echo.
echo 第二页
echo 此页为系统优化。
echo 【功能】
echo (1)全部执行
echo (2)禁止弹出警告窗口
echo (3)设置电源模式为卓越性能(1803系统以上)
echo (4)清理缓存及过时文件
echo (5)上一页
echo (6)重新启动计算机，使所有设置生效。
echo.

:N9
choice /c 123456 /m "请输入编号：(1)全部执行；(2)禁止弹出警告窗口；(3)设置电源模式为卓越性能(1803系统以上)；(4)清理缓存及过时文件；(5)上一页；(6)重新启动计算机，使所有设置生效。；"
if %errorlevel%==1 goto A1
if %errorlevel%==2 goto A2
if %errorlevel%==3 goto A3
if %errorlevel%==4 goto A4
if %errorlevel%==5 goto A5
if %errorlevel%==6 goto A6


:A1
choice /c 12 /m "你确定执行以上操作吗？：(1)确定执行；(2)我手滑了QAQ；"
if %errorlevel%==1 goto AA1
if %errorlevel%==2 goto AA2

:AA2
echo 正在返回...
goto NN9

:AA1
reg add HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\Associations /v ModRiskFileTypes /t REG_SZ /d .exe;.bat;.vbs /f
echo 禁止弹出警告窗口成功

powercfg -duplicatescheme e9a42b02-d5df-448d-aa00-03f14749eb61
echo 电源模式"卓越性能"已添加。(不要多次使用此选项，否则电源管理会多出很多选项。)

echo 清理缓存文件中..
echo 清理时间可能稍长，请耐心等待......
del /f /s /q  %systemdrive%\*.tmp
del /f /s /q  %tmp%\*.tmp
del /f /s /q  %systemdrive%\*._mp
del /f /s /q  %systemdrive%\*.log
del /f /s /q  %systemdrive%\*.gid
del /f /s /q  %systemdrive%\*.chk
del /f /s /q  %systemdrive%\*.old
del /f /s /q  %systemdrive%\recycled\*.*
del /f /s /q  %windir%\*.bak
del /f /s /q  %windir%\prefetch\*.*
rd /s /q %windir%\temp & md  %windir%\temp
del /f /q  %userprofile%\cookies\*.*
del /f /q  %userprofile%\recent\*.*
del /f /s /q  "%userprofile%\Local Settings\Temporary Internet Files\*.*"
del /f /s /q  "%userprofile%\Local Settings\Temp\*.*"
del /f /s /q  "%userprofile%\recent\*.*"
echo 清除完成。

goto NN9

:A2
reg add HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\Associations /v ModRiskFileTypes /t REG_SZ /d .exe;.bat;.vbs /f
echo 禁止弹出警告窗口成功
goto N9

:A3
powercfg -duplicatescheme e9a42b02-d5df-448d-aa00-03f14749eb61
echo 电源模式"卓越性能"已添加。
goto N9

:A4
echo 清理缓存文件中..
echo 清理时间可能稍长，请耐心等待......
del /f /s /q  %systemdrive%\*.tmp
del /f /s /q  %tmp%\*.tmp
del /f /s /q  %systemdrive%\*._mp
del /f /s /q  %systemdrive%\*.log
del /f /s /q  %systemdrive%\*.gid
del /f /s /q  %systemdrive%\*.chk
del /f /s /q  %systemdrive%\*.old
del /f /s /q  %systemdrive%\recycled\*.*
del /f /s /q  %windir%\*.bak
del /f /s /q  %windir%\prefetch\*.*
rd /s /q %windir%\temp & md  %windir%\temp
del /f /q  %userprofile%\cookies\*.*
del /f /q  %userprofile%\recent\*.*
del /f /s /q  "%userprofile%\Local Settings\Temporary Internet Files\*.*"
del /f /s /q  "%userprofile%\Local Settings\Temp\*.*"
del /f /s /q  "%userprofile%\recent\*.*"
echo 清除完成。
goto NN9

:A5
cls
goto B1

:A6
choice /c 12 /m "请输入编号：(1)确定重启；(2)我手滑了QAQ；；"
if %errorlevel%==1 goto BB1
if %errorlevel%==2 goto BB2

:BB1
shutdown/r

:BB2
cls
goto NN9
