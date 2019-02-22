<template>
  <section class="line" :class="{ show: isShow,fine: isFine,delay: isDelay }">
    <span></span>
    <span></span>
    <span></span>
    <span></span>
    <span></span>
  </section>
</template>
<script>
export default {
  data () {
    return {
      isShow: false,
      isFine: false,
      isDelay: false
    }
  },
  created() {
    setTimeout(()=>{
      this.isShow = true;
      this.isDelay = true;
    }, 500);
    setTimeout(()=>{
      this.isFine = true;
      this.isDelay = false;
    }, 1500);
  }
}
</script>

<style lang="scss" scoped>
.line{
  width: 100vw;
  height: 100vh;
  overflow: hidden;
  position: absolute;

  span{
    position: absolute;
    width: 1px;
    height: 100%;
    background-color: #d0d0d0;
    transform: translateY(100vh);
    transition: all 1000ms cubic-bezier(.09,.51,0,1.01);

    @for $i from 1 to 6 {
      &:nth-child(#{$i}) {
        left: calc((((#{$i} - 1) * 18vw) + 14vw));
      }
    }
  }

  &.show{
    span{
      transform: translateY(0);
    }
  }
  &.delay{
    span{
      @for $i from 1 to 6 {
        &:nth-child(#{$i}) {
          transition-delay: calc(#{$i} * 100ms);
        }
      }
    }
  }
}
</style>
