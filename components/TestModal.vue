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
  <div class="mw">
    <div class="mb">
        <div class="mi" id="mi">
            <div class="table-scroll">
                <div class="table-scroll-inner" id="tsi">
                    <div class="table">
                    </div>
                </div>
            </div>
            <div v-for="i in 15" :key="i" class="block">
            </div>
            <a v-on:click="closeThis">close</a>
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
      const mi = document.querySelector('#mi')
      const tsi = document.querySelector('#tsi')
      
      disableBodyScroll(mi, { allowTouchMove: el => el.id === 'mi' })
      disableBodyScroll(tsi, { allowTouchMove: el => el.id === 'tsi' })
      // disableBodyScroll(tsi, )
    },
    closed(){
      clearAllBodyScrollLocks()
    }
  },
}
</script>

<style scoped>
.mw{
    width: calc(100% - 40px);
    max-width: 375px;
    height: auto;
    max-height: calc(100vh - 200px);
    background-color: gray;
    border-radius: 10px;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    z-index: 10;
    visibility: visible;
    opacity: 1;    
}
.mb{
    height: auto;
}
.mi{
    width: auto;
    height: auto;
    max-height: calc(100vh - 300px);
    padding: 20px 40px;
    overflow-y: auto;
    position: relative;
    z-index: 9999;
}
.mi::-webkit-scrollbar {
    display: none; /* Chrome, Safari, Opera*/
}
.block{
    width: 100%;
    height: 100px;
    margin-bottom: 10px;
    background-color: green;
}
.table-scroll{
  width: 100%;
  position: relative;
}
.table-scroll-inner{
  display: block;
  overflow-x: auto;
  touch-action: revert;
}
.table{
  width: 700px;
  height: 300px;
  min-width: max-content;
  background-color: white;
  border: red solid 1px
}
</style>
