<template>
  <modal
    ref="modalArea"
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
  >
  <div class="mw">
    <div class="mb">
        <div class="mi">
            <div v-for="i in 15" :key="i" class="block">
            </div>
        </div>
    </div>
  </div>
  </modal>
</template>

<script>
import { disableBodyScroll, clearAllBodyScrollLocks } from 'body-scroll-lock'

export default {
  mounted() {
    const modalArea = this.$refs.modalArea
    disableBodyScroll(modalArea, { allowTouchMove: () => true })
  },
  beforeDestory() {
    clearAllBodyScrollLocks()
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
    -webkit-overflow-scrolling: touch;
    position: relative;
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
</style>
