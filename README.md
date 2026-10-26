Citystate II - National Treasury +9,000,000 (CE v0.2)
=====================================================

功能说明
--------
一次点击 CE 表格中的 [CLICK] Add +9,000,000 National Treasury：
  DataRegion.Treasury = 当前国库余额 + 9,000,000
不冻结金钱，不对城市资金余额和外汇储备执行加款。
每次成功执行后，CE 勾选框将在约 0.35 秒后自动取消，下一次点击会再增加 900 万。

经用户提供的 Mono 扫描报告确认的目标字段：
  程序集：Assembly-CSharp
  类：DataRegion
  字段：Treasury
  真实类型：System.Int32，静态字段，扫描时偏移为 0x34
  原报告扫描时的旧地址为 0x17E61ED8F34，旧数值为 999999。
  注：旧地址仅对原来的游戏运行有效，新版本会在每次点击时动态定位地址。

使用方法
--------
1. 备份游戏存档，进入已经加载完成的 Citystate II 国家或城市。
2. 用 Cheat Engine 附加到游戏进程。
3. 打开 CitystateII_Treasury_Plus9Million_v0.2.CT。
4. 点击 [CLICK] Add +9,000,000 National Treasury 前面的方框一次。
5. CE 通过 Mono 查找 DataRegion.Treasury，读取 Int32，再写入旧值+9000000。
6. 成功后动作标签会显示旧值/新值；随后方框自动取消勾选。
7. 如需再加 900 万，再次点击方框一次；若游戏 UI 未即时刷新，重新打开国库面板或让游戏推进一个时段查看。

保护与局限
----------
- Int32 最大值 2,147,483,647。若加款会溢出，脚本拒绝修改，不会截断、回绕或写坏相邻字段。
- 运行时再次核对字段名称、类型和静态属性。不能定位或存在多个匹配域时不猜地址。
- 游戏版本升级可能修改类或字段；本表格未经真实游戏写入测试，仍属实验版。
- CE 成功写入不保证游戏刷新或存档机制保留该金额；先用备份测试。
- 仅修改国库 DataRegion.Treasury；不是 DataCity.balance，也不是 DataRegion.DollarReserves。
- 成功信息在 Cheat Engine Lua 输出中（可通过 Table -> Show Cheat Table Lua Script / Lua Engine 查看）；失败会有弹窗。

ENGLISH QUICK START
-------------------
Back up your save; load a playable nation; attach Cheat Engine to Citystate II; open the CT;
click the checkbox next to '[CLICK] Add +9,000,000 National Treasury'. Each successful
activation adds exactly nine million to DataRegion.Treasury, then auto-unchecks to permit
another single click. Overflow protection applies because Treasury is Int32.
This version is based on the uploaded Mono discovery report and has not been tested in-game.
