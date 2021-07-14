### INSTALL

```shell
yarn add veil-intent-dialog
```
```shell
npm install veil-intent-dialog --save
```

### USAGE
1.首先在全局组件中放置`VeilIntentDialog`组件,一般就放置在`App.vue`,引入css文件
```vue
<template>
  <router-view></router-view>
  <VeilNotifications/>
</template>

<script>
import { VeilIntentDialog } from "veil-intent-dialog";
import "veil-intent-dialog/dist/index.css";
export default {
  
}
</script>
```

2.在代码中发送通知
```javascript
import { dialog } from "veil-notifications"

dialog.confirm("I'm message content")
```


### API

`notification` 挂载了2个函数,分别是confirm/alert,参数都是一样的

* message, //消息内容

返回一个Promise<Boolean>
confirm时用户取消为false,确定为true
alert时用户点击外部取消为false,点击确定为true

