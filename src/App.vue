<template>
  <div class='container'>

    <button
        class='btn btn_primary'
        @click='firstModal = true'
    >Modal First
    </button>
    <Modal
        v-show='firstModal'
        title='My Modal'
        @close='firstModal = false'
    >
      <div slot='body'>
        <h3>Hello from first modal!</h3>
        <button
            class='btn btn_primary'
            @click='firstModal = false'
        >Well Done!
        </button>
      </div>
    </Modal>

    <button
        class='btn btn_primary'
        @click='secondModal.show = true'
    >Second Modal
    </button>
    <Modal
        v-show='secondModal.show'
        title='My Second Modal'
        @close='secondModal.show = false'
    >
      <div slot='body'>
        <form @submit.prevent='submitSecondForm'>
          <label>
            Name:
            <input
                required
                type='text'
                v-model='secondModal.name'
            >
          </label>
          <label>
            Email:
            <input
                required
                type='email'
                v-model='secondModal.email'
            >
          </label>
          <button
              type='submit'
              class='btn btn_primary'
          >Submit
          </button>
        </form>
      </div>
    </Modal>

    <button
        class='btn btn_primary'
        @click='modalValidate = true'
    >Modal Validate
    </button>
    <Modal
        v-show='modalValidate'
        title='My Modal Validate'
        @close='modalValidate = false'
    >
      <div slot='body'>
        <ModalValidate :modalValidate='modalValidate' />
      </div>
    </Modal>
  </div>
</template>

<script lang='ts'>
import Vue from 'vue'
import Modal from '@/components/ui/Modal.vue'
import ModalValidate from '@/components/ModalValidate.vue'

export default Vue.extend({
  name: 'App',
  components: {Modal, ModalValidate},
  data() {
    return {
      firstModal: false,
      secondModal: {
        show: false,
        name: '',
        email: ''
      },
      modalValidate: false
    }
  },
  methods: {
    submitSecondForm() {
      console.log({
        name: this.secondModal.name,
        email: this.secondModal.email
      })
      this.secondModal.email = ''
      this.secondModal.name = ''
      this.secondModal.show = false
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
