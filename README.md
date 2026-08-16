# MiTroxy
基于 Mihomo (Clash.Meta) 核心打造的高性能、免维护 Android 透明代理模块，深度适配 KernelSU / APatch / Magisk。  旨在提供即开即用、内存极低占用、零配置负担的全设备透明分流体验。
✨ 核心特性
🚀 极简透明代理：基于 Linux TProxy 架构，底层接管全设备 TCP / UDP 流量，秒级响应，无多余耗电与性能损耗。

📱 深度集成 Web 控制台：适配 KernelSU / APatch 管理器前端架构，直接在 Root 管理器中一键调出可视化控制台，无需在数据目录存放冗余前端文件。

🪄 全自动节点装载：策略组原生支持 include-all: true，只需在 proxies: 中粘贴你的节点，控制台和分流规则自动聚合生效，彻底告别手动修改策略组的繁琐操作。

🛡️ 纯净更新保护：模块安装与版本更新仅释放 config.yaml.bak 参考模板，绝不覆盖用户现有的节点与自定义配置。

⚡ 极速 Fake-IP 架构：搭配精简精准的五层分流体系（广告拦截 ➔ 局域网直连 ➔ 核心海外服务 ➔ 国内域名/IP直连 ➔ 兜底代理），开启 no-resolve 杜绝 DNS 泄漏与查询延迟。

📂 目录结构说明
/data/adb/
├── modules/MiTroxy/           # 模块核心运行层 (KernelSU/APatch 管理)
│   ├── webroot/index.html     # Web 控制台前端文件 (供管理器渲染)
│   ├── service.sh             # 开机自启脚本
│   └── action.sh              # 管理器操作执行脚本
│
└── MiTroxy/                   # 用户数据与配置层 (纯净分离)
    ├── config.yaml            # 用户实际运行的配置文件
    ├── config.yaml.bak        # 官方最新默认配置模板
    ├── GeoIP.dat / GeoSite.dat# 离线规则数据库（一般会自动加载，如果没有重启一下）
    └── run.log                # 核心运行日志
🛠️ 快速上手
1.刷入模块：在 KernelSU / APatch / Magisk 中刷入 MiTroxy.zip 并重启设备（或点击 Action 按钮）。

2.配置节点：

打开文件管理器（推荐 MT 管理器），进入 /data/adb/MiTroxy/。

参考同目录下的 config.yaml.bak，将你的节点粘贴到 config.yaml 的 proxies: 区域下方并保存。

需要自行添加mihomo核心

3.启动代理：

在 KernelSU / APatch 中点击模块卡片上的 「执行」 按钮（或开关一次模块）。

4.管理节点：

点击模块右侧的 Web 控制台 按钮，在可视化界面中切换节点、查看实时流量与延迟。

📄 开源与致谢
代理核心：Mihomo（https://github.com/MetaCubeX/mihomo）

规则数据库：meta-rules-dat（https://github.com/MetaCubeX/meta-rules-dat）
