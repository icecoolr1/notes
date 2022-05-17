# Vue开发总结

> 所有vue应用=后面都是""
>
> v-bind v-on 简写后多要加属性 v-bind加要挂载的属性 v-on加事件

## v-bind

```vue
// v-bind的简写是 : 如
<img :class="test">
//可以使用三元表达式 注意''号
<div id="Slide2" class="carousel-item " :class="isactive===1?'active':''">
//使用对象 
<img :class="active:isAction">
```

## 组件

```js
<script>

export default {
  data(){
    return {
      list: [0,1,2],
      index: 0,
      isactive: 0,

    }
  },
  name: "pic_main",
	
  methods:{
    changePictureRight(){
      let a = 0
      this.index++
      a = this.index
      alert(a)
      this.isactive = this.list[a]
      alert(this.active)
    }

  }

}
</script>
```

## v-on

```html
<a class="carousel-control-next" href="#heroCarousel" role="button" data-bs-slide="next" 
@click="changePictureRight()">//写methods里的方法名
```

## vue main.js配置

```js
import { createApp } from 'vue'
import App from './App.vue'
import ElementPlus from 'element-plus';
import locale from 'element-plus/lib/locale/lang/zh-cn'
import router from "./router/index"

import * as ElIconModules from '@element-plus/icons-vue'

import 'element-plus/theme-chalk/index.css';

const app = createApp(App)
//路由
app.use(router)
// el icon
Object.keys(ElIconModules).forEach(function (key) {
    app.component(ElIconModules[key].name, ElIconModules[key])
})
// elplus
app.use(ElementPlus, { locale })
app.mount('#app')
```

## 路由配置

```js
//配置在route的index.js中
import {createRouter, createWebHashHistory} from "vue-router"
import AppContent from "@/components/AppContent";
import AddProduct from "@/components/AddProduct";
import updateCourse from "@/components/updateCourse";
import videoList from "@/components/videoList";
import addVideo from "@/components/addVideo";
import PlayVideo from "@/components/PlayVideo";
import UpdateVideo from "@/components/UpdateVideo";


const routes = [
    {path: "/", redirect: "/course"},
    {
        path: "/course",
        name: "myCourse",
        component: AppContent
    },
    {
        path: "/addCourse/:id",
        name: "addCourse",
        component: AddProduct
    },
    {
        path: "/updateCourse/:courseId",
        name: "updateCourse",
        component: updateCourse
    },
    {
        path: "/videoList/:courseId",
        name: "videoList",
        component: videoList
    },
    {
        path: "/addVideo/:courseId",
        name: "addVideo",
        component: addVideo
    },
    {
        path: "/play/:courseId",
        name: "play",
        component: PlayVideo
    },
    {
        path: "/updateVideo/:videoId",
        name: "update",
        component: UpdateVideo
    }

]
export const router = createRouter({
    history: createWebHashHistory(),
    routes: routes
})
export default router
```

## 表格居中

```css
/deep/.el-table th > .cell {
  text-align: center;
}
/deep/.el-table .cell {
  text-align: center;
}
```

## 表格获取数据输送后端

```html
<template v-slot="scope" >
  <el-button type="text" size="small" @click="DelVideo(scope.row)" >
    删除视频
  </el-button>
  <el-button type="text" size="small" @click="UpdateVideo(scope.row)">
    修改视频信息
  </el-button>
  <el-button type="text" size="small" @click="Play(scope.row)">
    观看视频
  </el-button>
</template>
```

## 其它开源前端项目方法

在methods中写

## props

![img](https://img-blog.csdnimg.cn/20181228143557186)

## html转vue

* 除了作者自定义vue文件其它第三方库无需主动声明导入
* 需要手动在自定义js中导包
