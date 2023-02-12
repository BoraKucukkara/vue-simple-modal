<template>
  <main>
    <button @click="open()" class="btn-light">Open Modal</button>
  </main>
  <!-- MODAL COMPONENT  -->
  <modal :modal-status="this.modal" @close="close">
    <h1>Are you sure?</h1>
    <p>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
    </p>
    <button @click="close()">Nope</button>
    <button @click="close()" class="btn-primary">Yeap</button>
  </modal>
  <!-- MODAL COMPONENT  -->

  <div class="copyright">
    <a href="https://github.com/BoraKucukkara/vue-simple-modal" title="Bora Kucukkara / vue-simple-modal on Github">
      <svg height="24" aria-hidden="true" viewBox="0 0 16 16" version="1.1" width="24" data-view-component="true" class="octicon octicon-mark-github v-align-middle">
        <path fill-rule="evenodd" d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"></path>
      </svg>
    </a>
    <a href="https://www.borakucukkara.com/" title="Bora Kucukkara personal web site">
      <img src="https://www.borakucukkara.com/borakucukkara.png" width="24">
    </a>
  </div>
</template>

<script>
import modal from './components/simple-modal.vue'

export default {
  name: 'App',
  components: {
    modal
  },
  data() {
    return {
      modal: false
    }
  },
  methods: {
    close() {this.modal = false},
    open() {this.modal = true}
  }
}
</script>

<style>
/* RESET */
*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;

}
h1, p {
  margin-bottom: 1rem;
}
body {
  margin:0;
  font-family: system-ui;
  display:flex;
  align-items: center;
  justify-content: center;
  width: 100vw;
  height: 100vh;
  background-image: url("@/assets/bg.jpg");
  background-size: cover;
  background-position: center;
  color:#666;

}
button {
  min-width: 7rem;
  padding: .5rem 1rem;
  font-size: 1.1rem;
  color:#fff;
  border-radius: .5rem;
  border:none;
  cursor: pointer;
  background: #555;
  justify-self: end;
  margin:.5rem .5rem 0 0;
  box-shadow: rgba(0, 0, 0, 0.45) 0px 25px 20px -20px;
  transition: all .2s;
}
.btn-light {
  background: #ffffff;
  color: #666;
  zoom:1.2;
  padding:1rem 2rem;
}
.btn-light:hover {color: coral}
.btn-primary {
  background: coral;
}
.copyright { position: absolute; bottom:1rem; right:1rem; z-index: 0}
.copyright a {padding: .3rem; opacity: .7; transition: all .3s;}
.copyright a:hover {opacity: 1}
</style>
