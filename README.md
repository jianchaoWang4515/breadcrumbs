# sp-breadcrumbs
> vue组件 超级面包屑

## Install
```shell
npm install sp-breadcrumbs -S
```

## Quick Start
``` javascript
import Vue from 'vue'
import routes from 'routes' // vueRouter.routes
import breadcrumbs from 'breadcrumbs'

Vue.use(new breadcrumbs(routes))
```

## Description
``` javascript
// routes.js
const routes = [
  { 
    path: '/home',
    component: Home,
    name: 'home', // 必须指定唯一name
    meta: {
        breadName: '首页', // 面包屑名称
        isHome: true, // 指定首页 会固定在面包屑第一个
    }
  }, { 
    path: '/list',
    component: List,
    name: 'list',
    meta: {
        breadName: '列表',
        // 有关联的routeName 在/list页面访问/list-detail 会push到面包屑后面
        childNames: [
            'list-detail'
        ]
    } 
  }, { 
    path: '/list-detail',
    component: List,
    name: 'list-detail'
    meta: {
        breadName: '列表详情'
    } 
  }
]

export default routes;
```

## Use
1. 使用默认样式
``` javascript
<template>
    <breadcrumbs separator="/"></breadcrumbs>
</template>
```
2. 支持slot自定义
``` javascript
<template>
    <breadcrumbs>
        <template v-slot:default="slotProps">
          <div v-for="item in slotProps.data"></div>
        </template>
    </breadcrumbs>
</template>
```
``` javascript
export default {
    computed: {
        breadList () {
            return this.$spBreadcrumb.crumbs;
        }
    }
}
```


## props
1. **separator**: String, 分隔符
1. **separatorClass**: String, 图标分隔符class, eparatorClass存在时separator将不起作用
