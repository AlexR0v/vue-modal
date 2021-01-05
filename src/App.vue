<template>
  <div class='container'>
    <button
        class='btn btn_primary'
        @click='firstModal = !firstModal'
    >Modal First
    </button>
    <Modal
        v-if='firstModal'
        title='My Modal'
    />
  </div>
</template>

<script lang='ts'>
import Vue from 'vue'
import Modal from '@/components/Modal.vue'

export default Vue.extend({
  name: 'App',
  components: {Modal},
  data() {
    return {
      firstModal: false
    }
  }
})
</script>

<style lang='scss'>
body {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #2c3e50;
}
</style>
