# 介绍

## 前言

这是一本老笨鸟口齿不清介绍如何构建一个满足大部分中小公司性能需求的网关系统的流水账。

希望可以通过一些口水话介绍 api gateway 技术，以及一点点实战演示能帮助大家理解。

由于老笨鸟水平不足，奋斗多年依然只达到别人的起跑线（会用但讲不清楚底层原理），所以只能先选用成熟的 openresty 技术避免大家撞见底层性能的冰山大关。

初期大纲如下：

- [x] [gateway 是什么？](0_gateway.md)
- [x] [反向代理是什么？](1_reverse_proxy.md)
- [x] [网络概念](2_network.md)
  - [x] 7 层模型
  - [x] 4 层网关
  - [x] 7 层网关
- [x] [网络协议](3_protocol.md)
- [ ] 如何选择小成本自建 api gateway
  - [ ] 采用什么样的简单架构
    - [ ] 为什么选择 openresty
    - [ ] 配置更新机制选择
    - [ ] 监控体系 opentelemetry
- [ ] 构建 gateway 实战
  - [ ] luarocks
  - [ ] tcp / udp gateway
    - [ ] openresty 如何配置 tcp / udp
    - [ ] 负载均衡之一 轮训
    - [ ] 热重启
  - [ ] 配置更新
    - [ ] 文件配置
    - [ ] 文件 watch
    - [ ] event 事件通知
    - [ ] 通过 etcd 扩展远程更新能力
  - [ ] http gateway
    - [ ] 简单路由实现
    - [ ] 成熟路由介绍
    - [ ] 负载均衡补齐 hash、最少连接数、ewma
  - [ ] dns
    - [ ] dns 解决 host 域名配置负载均衡问题
    - [ ] dns change checker
  - [ ] lua 动态插件机制
    - [ ] 跨域
    - [ ] websocket
    - [ ] 认证 jwt-auth
    - [ ] 限流
    - [ ] 蓝绿、金丝雀
    - [ ] lua serverless function
    - [ ] 缓存
  - [ ] Logging
    - [ ] log rotate
    - [ ] elk
    - [ ] loki
  - [ ] Metrics
  - [ ] Tracing
  - [ ] https
    - [ ] 动态证书
    - [ ] sni 代理
  - [ ] nginx patch
    - [ ] remove server token
    - [ ] keepalive config
  - [ ] 多语言支持
    - [ ] unix domain socket
    - [ ] wasm
  - [ ] 安全
    - [ ] simple lua waf
    - [ ] modsecurity
  - [ ] \[ ]
- [ ] Cloudflare 在 nginx 遇见的一些局限

## PS：

部分代码和组件引用于成熟的 gateway 平台 [apisix](https://apisix.apache.org/) 和 [Kong](https://konghq.com/)

本文以及相关代码项目借鉴仅做学习目的，如有商用请自行获取相关授权。

## 最后

感谢我家调皮鬼小蛮（一只布偶猫）和夭夭（一只金渐层）的陪伴，在放弃与朋友侃大山以及被朋友列为没有玩耍情趣的古板人生里，没有小蛮的骚扰陪伴，本人可能坚持不下来如此枯燥无味且没有转变金钱价值的学习与总结，以此追平至天才幼年时期起跑线。

希望在剩余的人生时间里，不会被天才们甩远几个世纪。
