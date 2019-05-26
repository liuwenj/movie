<template>
  <div class="wrapper" ref="wrapper">
      <slot></slot>
  </div>
</template>

<script>
import BScroll from 'better-scroll'

export default {
  name: 'Scroller',
  props:{
      handleToScroll:{
          tepe:Function,
          default:function(){}
      },
      handleToTouchEnd:{
          type:Function,
          default:function(){}
      }
  },
  components: {},
  data() {
    return {

    }
  },
  mounted(){
      var scroll =new BScroll(this.$refs.wrapper,{
        tap:true,
        probeType:1
      });
      this.scroll=scroll;
      scroll.on('scroll',(pos)=>{
          this.handleToScroll(pos)
      });
      scroll.on('touchEnd',(pos)=>{
          this.handleToTouchEnd(pos)
      })
  },
  methods:{
      toScrollTop(y){
          this.scroll.scrollTo(0,y);
      }
  }
}
</script>

<style scoped lang="stylus">
.wrapper{height:100%}
</style>
