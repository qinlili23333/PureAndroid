# 纯净 Android 公约 V0.9.1
  
#### 公约仍处于初步阶段,欢迎[PR](https://github.com/qinlili23333/PureAndroid/pulls)提交修改或在[Issues](https://github.com/qinlili23333/PureAndroid/issues)提交建议
#### 官方app已更新！  
  
[申请加入公约](HowToApply.md) | [公约成员](ApprovedList.md) | [Wiki](https://github.com/qinlili23333/PureAndroid/wiki) | [文章列表](article/list.md) | [SDK黑名单](SDKblacklist.md)  
[示例App](https://github.com/qinlili23333/PureAndroid/releases/tag/Apk) | [开发者网站](https://qinlili.bid)

## 0x0 总则
- 1. 纯净 Android 公约旨在规范(而非限制)Android app 开发,改善 Android 生态环境和用户体验. 
- 2. 纯净 Android 公约为开发者自愿加入,加入公约即视为开发者认可公约内容并自觉遵守.
- 3. **只有**完全符合公约的 App 才可以加入本公约.
- 4. `*`加入公约后,App 可在任意位置注明已加入本公约. 
- 5. 公约会随技术发展调整,建议您注明所遵循的公约版本.
- 6. 在编号后标有`*`的为建议支持特性,这些特性可以有效改善 App 性能和用户体验,但**不强制要求**支持.
  
## 0x1 项目主体
- 1. 至少设置28的 target sdk(通过逆向修改的原作者不再维护的App可放宽至23).  
- 2. 如果App存在`native lib`,必须提供 64 位 `lib`.
- 3. 安装包不得存在任何影响性能的安全措施
- 4. 安装包必须已经`对齐`**(zipalign)**.
- 5. 大于1M的安装包使用`v2`或`v3`签名.
- 6. 安装包的图标应适配自适应图标.
- 7. 若项目目标设备版本包含或高于**7.x**,则应适配圆形图标.
  
## 0x2 通知推送  
- 1. 用户应能且被告知能够自行选择是否接收推送.
- 2. 关闭推送后不得在后台保留推送服务.
- 3. 使用系统级统一推送服务时不得在后台保留推送服务.
- 4. 使用独立的子进程完成推送服务.
- 5. 推送通知的图标不得添加蒙板.
- 6. 若通知推送内容有多个类别,则需适配`Notification Channel`.

## 0x3 数据收集  
- 1. 数据收集包括对设备信息,App 使用记录,网络信息,错误日志等的收集`Bugly`,`Crashlytics`等错误收集服务属于数据收集.
- 2. 用户应能自行选择是否上传数据,若用户拒绝上传数据,数据仅能存储在本地.
- 3. 请在用户使用流量之前告知用户.

## 0x4 权限  
- 1. 不得申请与App功能无关的权限.
- 2. 不得为获取IMEI而申请电话权限..
- 3. 用户拒绝权限不得影响其他无需该权限功能的运行.
- 4. 仅允许在用户将要需要权限的功能之前申请权限
- 5. `manifest`中不得出现重复的权限.
- 6. `manifest`中不得出现无用权限.
- 7. `*`在申请权限时,应尽量向用户说明权限用途.
- 8. 尽可能使用`Shizuku`而不是`ADB`或`Root`
  
## 0x5 文件存储  
- 1. 对于用户主动直接或间接生成的文件,应使用`FileProvider`而不是直接传递文件 `Uri`.
- 2. 对于无需共享的文件,应存储于`data`目录内.
- 3. 对于缓存文件,应存储于`cache`目录内.
- 4. 对于用户被动直接或间接产生的文件,应在公共存储内以易辨识的目录命名存储,单个App仅允许在根目录下建立一个子文件夹,若需要额外分类,请在子文件夹内再建立文件夹.
- 5. 对于不是缓存的可清理文件,App应提供并告知用户其含有主动清理功能.
- 6. `*`提高缓存的复用率,不要缓存仅会使用一次的内容.  
   
## 0x6 自启动与后台  
- 1. 用户应自行选择是否允许自启动.
- 2. 在没有运行功能的情况下,App于后台静置12小时后,cpu时间应小于0:05s.
- 3. 非功能必须不得申请常驻后台.
  
## 0x7 功能特性  
- 1. 在App下载时使用使用`分割`**(split)**.
- 2. 尽量避免内存泄漏.制作对于`native`层的内存回收机制.
- 3. `*`支持 `documentLaunchMode` 多窗口.
- 4. `*`支持分屏功能.
- 5. `*`为所有功能提供开关,允许用户关闭所有的功能.
- 6. `*`合理使用子线程异步处理,避免在主线程上长时间处理任务而触发ANR.
- 7. 使用原生WebView
- 8. `*`支持纯 IPv6 网络  
## 0x8 App 资源文件  
- 1. `*`对图片等资源进行无损压缩.  
- 2. `*`使用`Vector`矢量代替传统位图.  
- 3. `*`使用`webp`代替`png`.  
- 4. `*`对于大量使用的图片资源,使用含有特殊图案的字体文件代替传统位图.  
   
## 0x9 广告  
- 1. `*`广告提供明显的关闭方式.  
- 2. 广告不得遮挡任何按钮.
   
## 0xa 显示  
- 1. 完全支持或完全不支持横屏.
- 2. `*`兼容自由式多窗口模式.
- 3. 视频支持画中画模式. 
- 4. 适配深色模式.
- 5. 至少为`Android P`优化刘海屏
