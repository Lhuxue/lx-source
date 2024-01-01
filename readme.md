```
(屏幕宽度问题头图无法正常显示请忽略)
     __      __  __      ______  ______  __  __  ____    ______  ______
    / /     / / / /     / ____/ / __  / / / / / / __ \  / ____/ / ____/
   / /     / /_/ / __  / /___  / / / / / / / / / /_/ / / /     / /___
  / /      \_\ \  /_/ /___  / / / / / / / / / /  ___/ / /     / ____/
 / /___  / / / /     ____/ / / /_/ / / /_/ / / / \   / /___  / /___
/_____/ /_/ /_/     /_____/ /_____/ /_____/ /_/ \_\ /_____/ /_____/
=======================================================================
```
## ZxwyWebSite/LX-Source
### 简介
+ LX-Music 解析源 (洛雪音乐自定义源)
+ **由于本项目的特殊性，请低调使用，切勿宣传**
+ 测试阶段，不代表最终品质
+ 验证部分暂未完善，建议仅本地部署，不要公开发布
+ 视频教程：[使用教程.mp4](https://r2eu.zxwy.link/gh/lx-source/v1.0.2-b0.1/%E4%BD%BF%E7%94%A8%E6%95%99%E7%A8%8B.mp4)
<!-- + **锟斤拷** -->

### 使用
#### 服务端
+ 到Release下载对应平台可执行文件运行
+ 或下载源码自行编译
#### 客户端
+ 使用自定义源脚本：`data/public/lx-custom-source.js`
+ (请先运行服务端以释放资源文件)
+ **修改 apiaddr 为服务端地址，apipass 为验证Key**

### 配置
+ 第一次运行自动生成配置后按注释填写即可
+ 位置：`{运行目录}/data/conf.ini`
+ **注：默认使用本地缓存，请修改 [Cache].Local_Bind 为实际访问地址**

### 功能 *(未全部实现)*
+ 兼容原版测试接口
+ 提供自定义源脚本
+ 支持多种工作模式 *(PART)*
   - 仅解析(0): 解析后返回原始外链
   - 仅缓存(1): 缓存并返回本地数据外链
   - 都使用(2): 无缓存返回原始外链并缓存, 有缓存返回本地数据外链
+ 设置缓存直链类型 *(TODO)*
   - 永久链(0): `file/:s/:id/:q`, 和解析参数相同
   - 临时链(1): `file/:{time.unix}/:{md5(cquery)}`, 参考网易云样式, 有效期默认10分钟
#### Api
+ `/` 获取服务端信息
+ `/link/:s/:id/:q` 查询音乐链接
+ `/file/` 本地缓存访问地址
<!-- + ... -->

### 音乐源
+ 内置源 (抓取自网络公开接口) **注：文明上网，请勿滥用**
+ 账号源 (登录Vip账号解析) **注：可能导致封号，如出问题本项目不负责**

### 开发
+ 环境要求：Golang 1.21 (建议 >=1.20)
+ 可不开启CGO编译
+ 源码较乱，暂未整理...
+ zTool包不存在：解压发布页 `ztool.zip` 放在源码上级目录即可使用
#### 源码结构
+ /
   - pkg/ 依赖包，一般在外部调用，不轻易修改
   - src/ 源码包，用于实现各种功能
      * env 公用变量，需要全局调用的参数
      * caches 文件缓存封装
      * router Gin路由
      * middleware 请求中间件
      * sources 音乐源
   <!-- - public/ 静态资源，打包进程序，新环境运行自动释放 -->
   <!-- - scripts/ 一些快捷脚本 -->
   - build.go 快速构建脚本 (请先根据本地环境编辑配置)
   - main.go 主程序

### 其它
+ 基于 Golang + Gin框架 编写
+ 部分功能参考 [Python版](https://github.com/lxmusics/lx-music-api-server-python) 实现

### 更新
+ 见 `update.md`

### 项目协议

本项目基于 [MIT] 许可证发行，以下协议是对于 MIT 原协议的补充，如有冲突，以以下协议为准。

词语约定：本协议中的“本项目”指本开源项目；“使用者”指签署本协议的使用者；“官方音乐平台”指对本项目内置的包括酷我、酷狗、咪咕等音乐源的官方平台统称；“版权数据”指包括但不限于图像、音频、名字等在内的他人拥有所属版权的数据。

1. 本项目的数据来源原理是从各官方音乐平台的公开服务器中拉取数据，经过对数据简单地筛选与合并后进行展示，因此本项目不对数据的准确性负责。
2. 使用本项目的过程中可能会产生版权数据，对于这些版权数据，本项目不拥有它们的所有权，为了避免造成侵权，使用者务必在**24 小时**内清除使用本项目的过程中所产生的版权数据。
3. 由于使用本项目产生的包括由于本协议或由于使用或无法使用本项目而引起的任何性质的任何直接、间接、特殊、偶然或结果性损害（包括但不限于因商誉损失、停工、计算机故障或故障引起的损害赔偿，或任何及所有其他商业损害或损失）由使用者负责。
4. 本项目完全免费，且开源发布于 GitHub 面向全世界人用作对技术的学习交流，本项目不对项目内的技术可能存在违反当地法律法规的行为作保证，**禁止在违反当地法律法规的情况下使用本项目**，对于使用者在明知或不知当地法律法规不允许的情况下使用本项目所造成的任何违法违规行为由使用者承担，本项目不承担由此造成的任何直接、间接、特殊、偶然或结果性责任。

若你使用了本项目，将代表你接受以上协议。

音乐平台不易，请尊重版权，支持正版。  
本项目仅用于对技术可行性的探索及研究，不接受任何商业（包括但不限于广告等）合作及捐赠。  
若对此有疑问请 mail to: admin+zxwy.tk (请将`+`替换为`@`)
 