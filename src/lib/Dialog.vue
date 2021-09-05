<template>
  <template v-if="visible">
    <Teleport to="body">
      <div class="card-dialog-overlay" @click="closeOnClickOverlay"></div>
      <div class="card-dialog-wrapper">
        <div class="card-dialog">
          <header>
            <slot name="title"></slot>
            <span @click="close"  class="card-dialog-close"> </span>
          </header>
          <main>
            <slot name="content"/>
          </main>
          <footer>
            <Button shape="rec" level="primary" @click="ok">确认</Button>
            <Button shape="rec"  @click="cancel">取消</Button>
          </footer>
        </div>
      </div>
    </Teleport>
  </template>
</template>

<script>
import Button from "./Button.vue";
export default {
  name: 'Dialog',
  components: {Button},
  props:{
    visible:{
      type:Boolean,
      default:false
    },
    closeOnClickOverlay:{
      type:Boolean,
      default:true
    },
    ok:{
      type:Function
    },
    cancel:{
      type:Function
    }
  },
  setup(props,context){
    const close = ()=>{
      context.emit('update:visible',false)
    }
    const closeOnClickOverlay = ()=>{
      if(props.closeOnClickOverlay){
        close()
      }
    }
    const ok = () => {
      if (props.ok && props.ok() !== false) {
        close()
      }
    }
    const cancel = () => {
      props.cancel && props.cancel()
      close()
    }
    return {close,ok,cancel,closeOnClickOverlay}
  }
}
</script>

<style lang="scss" >
$radius: 4px;
$border-color: #d9d9d9;

.card-dialog {
  background: white;
  border-radius: $radius;
  box-shadow: 0 2px 6px 0 rgb(26, 24, 24);
  min-width: 20em;
  max-width: 90%;

  &-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: fade_out(black, 0.5);
    z-index: 10;
  }

  &-wrapper {
    position: fixed;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    z-index: 11;
  }

  >header {
    padding: 12px 16px;
    border-bottom: 0.5px solid $border-color;
    display: flex;
    align-items: center;
    justify-content: space-between;
    font-size: 20px;
  }

  >main {
    padding: 16px;
  }

  >footer {
    border-top: 1px solid $border-color;
    padding:4px 16px;
    text-align: right;
  }

  &-close {
    position: relative;
    display: inline-block;
    width: 16px;
    height: 16px;
    cursor: pointer;

    &::before,
    &::after {
      content: '';
      position: absolute;
      height: 1px;
      background: black;
      width: 100%;
      top: 50%;
      left: 50%;
    }

    &::before {
      transform: translate(-50%, -50%) rotate(-45deg);
    }

    &::after {
      transform: translate(-50%, -50%) rotate(45deg);
    }

  }
}

</style>
