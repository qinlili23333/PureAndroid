# 纯净 Android 公约v0.1   
  
[申请加入公约][]  
  
## 0x0 总章  
0.纯净 Android 公约旨在规范（而非限制）Android app 开发，改善 Android 生态环境和用户体验。  
1.纯净 Android 公约为开发者自愿加入，开发者可为其一个或多个 app 加入，也可在加入后随时选择退出。  
2.只有完全符合公约的 app 可以加入本公约。  
3.加入公约后， app 可在任意位置注明已加入本公约，当然也可以不注明。  
4.公约会伴随技术发展不断调整，若 app 未能跟进公约的更新，会被移出公约。  
  
## 0x1 项目主体  
0.必须设置至少26的 target sdk 。（针对通过逆向修改的官方弃坑类 app 可放宽至23）  
1.如果 app 存在 native lib ，必须提供64位 lib 。（针对目前没有64位的 unity 游戏可放宽）  
2.安装包不得存在任何形式的加固或其他影响性能的安全措施。（推荐使用较为复杂的混淆保障安全）  
3.安装包必须已经对齐。（ zipalign ）  
4.安装包使用v2或v3签名。（这有助于改善安装速度）  
  
## 0x2 推送  
0.推送必须有开关，用户应能自行选择是否接收推送。  
1.关闭推送后不得在后台保留推送服务。  
2.在能使用系统级统一推送服务（ gcm ，推必达等）时不得在后台保留推送服务。  
  
## 0x3 数据收集  
0.数据收集包括设备信息， app 使用记录，网络信息，错误日志等。  
1.数据收集必须有开关，用户应能自行选择是否上传数据。  
2. app 仅能收集自身数据，不得收集其他无关数据，如设备已安装 app 列表等。  
3.数据收集服务仅允许在 app 前台运行时上传数据。  
4.数据收集服务仅允许使用 WiFi 上传数据，不得消耗用户流量。  
  
## 0x4 权限  
0.不得申请超越 app 功能的权限。  
1.不得为了获取 IMEI 而申请电话权限。（推荐读取设备 id 和谷歌框架 id 代替）  
2.用户拒绝权限不得影响其他无需该权限功能的运行。  
3.仅允许在用户打开需要权限的功能时申请权限，不得在启动时一次性申请全部权限（除非该 app 所有功能都需要全部权限）。  
4.项目 manifest 中不得出现重复的权限。（建议在使用较多 sdk 的项目中留心剔除重复权限）  
  
## 0x5 文件存储  
0.对于主动的共享文件，使用 FileProvider 。  
1.对于无需共享的文件，存储于内置或外置 data 目录内。  
2.对于缓存文件，存储于内置或外置 cache 目录内。  
3.对于被动的共享文件（如保存图片），应在外置公共存储内以易辨识的目录命名存储，不得直接存储于根目录下，单个 app 仅允许在根目录下建立一个子文件夹，若需要额外分类，请在子文件夹内再建立子文件夹。  
4.对于不是缓存的可清理文件， app 应提供清理功能。（自动清理或允许用户手动清理）  
  
## 0x6 自启动与后台  
0.若 app 需要自启动，必须提供开关，用户应自行选择是否允许自启动。  
1.不得在非用户允许场景下自启动。  
2.在没有运行功能的情况下，后台不得消耗 cpu 资源。（后台静置12小时 cpu 时间应小于0:05）  
3.非功能必须（如音乐播放，上传下载等）不得申请常驻后台。  
  
## 0x7 功能特性  
0.支持全面屏。  
1.对于上架谷歌 play 的 app ，使用分割（ split ）。（这有助于减少用户下载消耗流量）  
2.避免内存泄漏。  
  
## 0x8 建议支持的特性  
0.下列特性有利于改善 app 性能和用户体验，建议支持，但不支持不影响加入公约。  
1.对于文档类和聊天类功能，建议支持 documentLaunchMode 多窗口。  
2.建议对图片等资源进行无损压缩。  
3.建议使用 Vector 矢量代替传统位图。  
4.建议逐步用 webp 取代 png 。  
5.对于除了游戏以外的 app ，建议支持分屏。  


[申请加入公约]: https://github.com/qinlili23333/PureAndroid/blob/master/HowToApply.md



