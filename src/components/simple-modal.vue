<template>
  <div class="modal-container" :class="[modalStatus ? 'fade-in' : 'fade-out', status]">
    <div class="modal-backdrop" @click="$emit('close')" ></div>
    <div class="modal-content" tabindex="0" :class="[modalStatus ? 'fade-up' : 'fade-down']">
      <!-- MODEL CONTENT -->
      <slot id="content"></slot>
      <!-- MODEL CONTENT -->
      <div class="modal-close-btn" @click="$emit('close')">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 320 512"><path d="M310.6 150.6c12.5-12.5 12.5-32.8 0-45.3s-32.8-12.5-45.3 0L160 210.7 54.6 105.4c-12.5-12.5-32.8-12.5-45.3 0s-12.5 32.8 0 45.3L114.7 256 9.4 361.4c-12.5 12.5-12.5 32.8 0 45.3s32.8 12.5 45.3 0L160 301.3 265.4 406.6c12.5 12.5 32.8 12.5 45.3 0s12.5-32.8 0-45.3L205.3 256 310.6 150.6z"/></svg>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'simple-modal',
  props: {
    modalStatus: {
      type:Boolean,
      required: true
    }
  },
  data() {
    return {
      status: ""
    }
  },
  watch: {
    modalStatus(newValue) {
      if(newValue === false) {
        setTimeout(()=>{
          this.status = "modal-hide"
        },300)
      } else {this.status = ""}
    }
  },
  mounted() {this.status = "modal-hide"
  }
}
</script>
<style scoped>
.modal-container {
  position: absolute;
  inset:0;
  display: grid;
  place-items: center;
  backdrop-filter: blur(.5rem);
  z-index: 99;
}
.modal-backdrop {
  position: absolute;
  inset:0;
  z-index: 100;
}
.modal-content {
  width: max-content;
  height: max-content;
  max-width: 60vw;
  max-height: 90vh;
  overflow: auto;
  background: rgba(255, 255, 255, 0.85);
  padding: 2rem;
  box-shadow: rgba(50, 50, 93, 0.25) 0px 50px 100px -20px, rgba(0, 0, 0, 0.3) 0px 30px 60px -30px;
  border-radius: 1rem;
  position: relative;
  border: .3rem solid #fff;
  z-index:101;
}
.modal-close-btn {
  width: 1rem;
  position: absolute;
  fill:gray;
  right: 1rem;
  top:1rem;
  cursor: pointer;
  transition: all .3s;
}
.modal-close-btn:hover {fill: coral}

.fade-in { display: grid; animation: fade-in .3s ease forwards;}
.fade-out {animation: fade-out .3s ease forwards;}
.fade-up {animation: fade-up .3s ease forwards;}
.fade-down {animation: fade-down .3s ease forwards;}
.modal-hide {
  display: none;
}
@keyframes fade-in {
  0% {opacity: 0}
  100% {opacity: 1}
}
@keyframes fade-out {
  0% {opacity: 1;}
  100% {opacity: 0;}
}
@keyframes fade-up {
  from {transform: translateY(3rem)}
}
@keyframes fade-down {
  to {transform: translateY(3rem)}
}
@media screen and (max-width: 767px) {
  .modal-content {
    max-width: 90vw;
    max-height: 90vh;
  }
}
</style>
