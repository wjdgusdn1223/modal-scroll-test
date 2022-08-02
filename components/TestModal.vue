<template>
  <modal
    name="testModal"
    styles="
    transition: 0.4s ease;
    visibility: visible;
    opacity: 1;
    width: 100%;
    height: 100%;
    position:fixed;
    top: 0;
    left: 0;
    z-index: 30;
    overflow: initial;
    box-sizing: initial;
    background-color: initial;
    border-radius: initial;
    box-shadow: initial;
    "
    :adaptive="true"
    :reset="true"
    :clickToClose="false"
    v-on:opened="opened"
    v-on:closed="closed"
  >
  <div id="displayArea" class="parent">
    <div class="mw">
      <div class="mb">
        <div class="head">title</div>
        <div id="scroll" class="inner">
          <transition name="guide"
            ><div v-if="true" class="guide"
          /></transition>
          <div class="image" />
        </div>
        <div class="close" @click="closeModal">
          close
        </div>
      </div>
    </div>
  </div>
  </modal>
</template>

<script>
// import { lock, unlock, clearBodyLocks } from 'tua-body-scroll-lock'
import { disableBodyScroll, clearAllBodyScrollLocks } from 'body-scroll-lock'
export default {
  data () {
    return {
      top: 0,
      isTouch: false,
      isScroll: false,
      isYScroll: false,
      touchDelay: 0
    }
  },
  methods: {
    closeThis() {
      this.$emit('closeModal')
    },
    opened() {
      const scroll = document.querySelector('#scroll')
      
      disableBodyScroll(scroll, { allowTouchMove: el => el.id === 'scroll' })

      const vh = window.innerHeight * 0.01

      document.querySelector("#displayArea").style.setProperty("--vh", `${vh}px`)

      if(window.innerHeight > window.innerWidth) {
        document.querySelector("#displayArea").style.cssText = ''
        document.querySelector("#displayArea").style.height = '100%'
      } else {
        document.querySelector("#displayArea").style.height = ''
      }
    },
    closed(){
      clearAllBodyScrollLocks()
    }
  },
}
</script>

<style scoped>
.parent {
  position: relative;
  width: 100vw;
  height: calc(var(--vh, 1vh) * 100);
}
.mw{
    width: calc(100vw - 40px);
    max-width: 370px;
    height: auto;
    max-height: calc(calc(var(--vh, 1vh) * 100) - 32vw);
    background-color: gray;
    border-radius: 10px;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    z-index: 10;
    overflow: hidden;
}
.mb{
    height: auto;
}
.head {
  font-size: 16px;
  line-height: 1.4;
  padding: 30px 20px;
  width: auto;
  background-color: green;
  font-weight: bold;
  text-align: center;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 5;
}
.close {
  font-size: 16px;
  line-height: 1.4;
  padding: 22px 20px;
  width: auto;
  background-color: green;
  font-weight: bold;
  text-align: center;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 5;
  left: 0;
  bottom: 0;
  transition: opacity 0.3s ease;
  cursor: poiter;
  position:sticky
}
.inner {
    width: auto;
    height: auto;
    max-height: calc(calc(var(--vh, 1vh) * 100) - 400px);
    padding: 24px 20px;
    overflow-y: auto;
    position: relative;
    @supports (-webkit-touch-callout: none) {
      touch-action: manipulation;
    }
}
.guide::before {
  content: '';
  width: 200px;
  height: 115px;
  background-repeat: no-repeat;
  background-position: center;
  background-size: 100% auto;
  backface-visibility: hidden;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 1;
  animation-duration: 0.3s;
  background-image: url('https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png')
}
.guide-leave-active {
  transition: opacity 0.3s;
}
.guide-leave-to {
  opacity: 0;
}
.image {
  height: 1000px;
  width: 100%;
  background-color: blue;
}
</style>
