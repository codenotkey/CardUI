<template>
    <button class="card-btn-btn"
            :class="classed"
            :style="colorStyle"
            :disabled="disabled"
    >
      <span v-if="loading" class="card-btn-loadingIndicator"></span>
      <span>
        <slot class="card-btn-text"/>
      </span>
    </button>
</template>

<script>
import {computed} from "vue";

export default {
  name: 'Button',
  inheritAttrs:false,
  props:{
    shape:{
      type:String,
      default:'main'
    },
    level:{
      type:String,
      default:'default'
    },
    bgColor:{
      type:String,
      default:''
    },
    fontColor:{
      type:String,
      default:''
    },
    disabled:{
      type:Boolean,
      default:false
    },
    loading: {
      type: Boolean,
      default: false
    }
  },
  setup(props){
    const {shape,level,bgColor,fontColor} = props
    const colorStyle =computed(()=>{
      return{
        color: fontColor,
        background: bgColor
        }
      }
    )
    const classed = computed(()=>{
      return{
        [`card-btn-shape-${shape}`]:shape,
        [`card-btn-level-${level}`]:level,
      }
    })
    return {classed,props,colorStyle}
  }
}
</script>

<style lang="scss">
@import "style";
$width:10px;
$height:30px;
    .card-btn-btn{
      text-align: center;
      white-space: nowrap;
      font-size: 16px;
      padding: 10px 16px;
      background: white;
      color: #181818;
      border: 1px solid #d7d7d7;
      cursor: pointer;

      & + & {
        margin-left: 8px;
      }
      &.card-btn-level-primary{
        background: $color1;
        color: white;
      }
      &.card-btn-level-success{
        background: $color2;
        color: white;
      }
      &.card-btn-level-warn{
        background: #ff6a6b;
        color: white;
      }
      &.card-btn-level-danger{
        background: #dd4343;
        color: white;
      }
      &.card-btn-shape-rec{  //rectangle //长方形
        border-radius: $height;
      }
      &[disabled] {
        cursor: not-allowed;
        opacity: 0.5;
      }
    }
    .card-btn-loadingIndicator{
      width: 13px;
      height: 13px;
      display: inline-block;
      margin-right: 4px;
      border-radius: 8px;
      border-color: white white white transparent;
      border-style: solid;
      border-width: 2px;
      animation: card-btn-spin 1s infinite linear;
      //cursor:wait;
      }
    @keyframes card-btn-spin {
      0%{transform: rotate(0deg)}
      100%{transform: rotate(360deg)}
    }

</style>
