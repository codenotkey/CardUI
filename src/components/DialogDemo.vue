<template>
  <div>
    <Button @click="toggle" level="primary">打开Dialog</Button>
    <Dialog  v-model:visible="defaultResult" :closeOnClickOverlay="true" :ok="ok" :cancel="cancel" >
      <template v-slot:content>
        <h3> 这是内容一</h3>
        <div> 自定义内容</div>
        <strong> 这是内容二</strong>
      </template>
      <template v-slot:title>
        <h5>这个弹窗的标题</h5>
      </template>
    </Dialog>
  </div>
</template>

<script>
import Dialog from "../lib/Dialog.vue";
import Button from "../lib/Button.vue";
import {ref} from "vue";
export default {
  name: 'DialogDemo',

  components:{Button, Dialog},

  setup(){
    const defaultResult = ref(false)
    const toggle = ()=>{
      defaultResult.value = !defaultResult.value
    }
    const ok= ()=>{
      //do something
      return true
    }
    const cancel = ()=>{

    }
    return { defaultResult,toggle,ok,cancel}
  }
}
</script>

<style lang="scss">

</style>

