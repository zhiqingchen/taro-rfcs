# 支持在 RN 项目中直接使用 Taro 代码

0. 新增包`@tarojs/rn-supporter`

## 包功能

0. 支持样式处理方案.
1. 支持`taro`编译配置.
2. 支持`taro`运行时配置.
2. 支持`taro`跨平台开发方案.
3. 导出供`metro.config.js`使用的类.

## 与`rn-runner`的区别

0. 去除bundler server
1. 去除打包相关内容
2. 去除入口文件处理
2. 不处理导航
3. 需自行集成到原RN项目中

## 业务需要处理

0. 自行处理路由.
1. 对 taro page 使用 runtime 的`createPageConfig`进行包装.
2. 需要有 config 目录，编译配置与 taro 保持一致。
3. Taro 用到的原生依赖，需要自行安装。（且需要集成 react-native-unimodules）

## metro.config.js

```js
const { mergeConfig } = require("metro-config");
const Supporter = require('@tarojs/rn-supporter')

const supporter = new Supporter()
const taroMetroConfig = supporter.getMetroConfig()

const busConfig = {
  resetCache:true,
}
module.exports = mergeConfig(busConfig,taroMetroConfig)
```

## babel.config.js

```js
module.exports = {
  presets: [
    ['taro', {
      framework: 'react',
      ts: true
    }]
  ]
}
```

## config/index.js

> 与 Taro 项目完全保持一致。

## 参考
