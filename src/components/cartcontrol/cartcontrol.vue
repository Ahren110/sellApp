<template>
  <div class="cartcontrol">
    <transition name="move">
      <div class="cart-decrease icon-remove_circle_outline" v-show="food.count > 0" @click="decreaseCart">
        <!-- <span class="inner"></span> -->
      </div>
    </transition>
    <div class="cart-count" v-show="food.count > 0">{{food.count}}</div>
    <div class="cart-add icon-add_circle" @click="addCart"></div>
  </div>
</template>

<script>
import Vue from 'vue'
export default {
  props: {
    food: {
      type: Object
    }
  },
  created () {

  },
  methods: {
    addCart (event) {
      console.log(1)
      if (!this.food.count) {
        Vue.set(this.food, 'count', 1)
      } else {
        this.food.count++
      }
      this.$emit('cartadd', event.target)
    },
    decreaseCart () {
      if (this.food.count) {
        this.food.count--
      }
    }
  }
}
</script>

<style lang="stylus">
  .cartcontrol
    font-size: 0
    .cart-decrease, .cart-add
      display: inline-block
      padding: 6px
      display: inline-block
      font-size: 24px
      line-height: 24px
      color: rgb(0, 160, 220)
    .move-enter-active, .move-leave-active
      transition: all 0.4s linear
    .move-enter, .move-leave-to
      opacity: 0
      transform: translate3d(24px, 0, 0) rotate(180deg)
    .move-enter-to, move-leave
      opacity: 1
      // transform: translate3d(0, 0, 0) rotate(0)
    .cart-count
      display: inline-block
      vertical-align: top
      width: 12px
      padding-top: 6px
      line-height: 24px
      font-size: 10px
      text-align: center
      color: rgb(147, 153, 159)
    .cart-add
      display: inline-block
</style>
