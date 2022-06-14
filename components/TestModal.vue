<template>
  <modal
    v-scroll-lock="true"
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
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
            a</br>
        </div>
    </div>
  </div>
  </modal>
</template>

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
    max-height: calc(100vh - 56px);
}
.mi{
    width: 100%;
    height: auto;
    max-height: calc(100vh - 56px);
    padding: 40px 20px;
    overflow-y: auto;
    -webkit-overflow-scrolling: touch;
    position: relative;
}
</style>
