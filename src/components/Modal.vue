<template>
  <transition name="modal">
    <div class="modal-mask">
      <div class="modal-wrapper">
        <div class="modal-container">

          <div class="modal-header">
            <button @click="$emit('prev')">prev</button>
            <button @click="$emit('next')">next</button>
            <button class="modal-default-button" @click="$emit('close')">
              close
            </button>
          </div>

          <Comic v-bind:xkcd="this.xkcd"></Comic>

        </div>
      </div>
    </div>
  </transition>
</template>

<script>
import Comic from './Comic'

export default {
  name: 'Modal',
  props: ['xkcd'],
  components: { Comic }
}
</script>

<style>
.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, .5);
  display: table;
  transition: opacity .3s ease;
}

.modal-wrapper {
  display: table-cell;
  vertical-align: middle;
}

.modal-container {
  display: inline-block;
  max-width: 90%;
  max-height: 90%;
  margin: 0px auto;
  padding: 20px 30px;
  background-color: #fff;
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, .33);
  transition: all .3s ease;
  text-align: left;
  font-family: Helvetica, Arial, sans-serif;
}

.modal-default-button {
  float: right;
}

.modal-container img {
  max-height: 75vh;
  max-width: 80vw;
}

.modal-container sub {
  font-size: .9em;
}

/*
 * The following styles are auto-applied to elements with
 * transition="modal" when their visibility is toggled
 * by Vue.js.
 *
 * You can easily play with the modal transition by editing
 * these styles.
 */

.modal-enter {
  opacity: 0;
}

.modal-leave-active {
  opacity: 0;
}

.modal-enter .modal-container,
.modal-leave-active .modal-container {
  -webkit-transform: scale(1.1);
  transform: scale(1.1);
}
</style>
