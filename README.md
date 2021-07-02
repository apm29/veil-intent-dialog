### INSTALL

```shell
yarn add veil-intent-dialog
```
```shell
npm install veil-intent-dialog --save
```

### USAGE
1.首先在全局组件中放置`Dialogs`组件,一般就放置在`App.vue`
```vue
<template>
  <router-view></router-view>
  <Dialogs/>
</template>

<script>
import { Dialogs } from 'veil-intent-dialog'
export default {
  
}
</script>
```

2.在代码中发送通知
```javascript
import { dialog } from "veil-intent-dialog"

dialog.alert("I'm message content")
```


### API

`dialog` 挂载了2个函数,分别是confirm,alert,参数都是一样的

* message, //消息内容

`dialog.alert/confirm`返回一个`Promise<Boolean>`,点击取消时为false,确定为true,内部发生错误时将会抛出Error
