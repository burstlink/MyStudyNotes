# 配置Node.js HTTP全局代理

## 安装global-agent

```bash
npm install global-agent

```

## 使用方法

1. 写入代码中使用

```js
process.env.GLOBAL_AGENT_HTTP_PROXY= 'http://xxxxx:xxxx';
process.env.GLOBAL_AGENT_NO_PROXY= 'localhost';
process.env.NODE_TLS_REJECT_UNAUTHORIZED = 0;
require('global-agent/bootstrap');
```

2. 执行程序前添加环境变量

```bash
set GLOBAL_AGENT_HTTP_PROXY=http://xxxxx:xxxx
set GLOBAL_AGENT_NO_PROXY=localhost
set NODE_TLS_REJECT_UNAUTHORIZED=0
node -r global-agent/bootstrap server.js
```
