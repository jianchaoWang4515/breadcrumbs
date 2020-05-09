# sp-breadcrumbs
> vue组件 超级面包屑

## Install
```shell
npm install breadcrumbs -S
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
``` javascript
<template>
    <breadcrumbs separator="/"></breadcrumbs>
</template>

export default {
    computed: {
        breadList () {
            return this.$spBreadcrumb.crumbs;
        }
    }
}
```


## Attributes
``` javascript

export default {
  props: {
    // 分隔符	
    separator: {
      type: String,
      default: '/'
    },
    // 图标分隔符 class	separatorClass存在时separator将不起作用
    separatorClass: String
  }
}
```
