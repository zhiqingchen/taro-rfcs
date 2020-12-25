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
2. 将原本在config中的配置, 转移到metro中. 配置结构同 taro config.

## metro.config.js

```js
import Supporter from '@tarojs/rn-supporter'

const support = new Supporter({
    designWidth: 750,
    defineConstants: {
        A: '"a"' // JSON.stringify('a')
    },
    rn: {
        postcss: {},
        sass: {}
    }
})

module.exports = {

}
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

## 参考
