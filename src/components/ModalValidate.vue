<template>
  <form @submit.prevent='onSubmit'>
    <div
        class='form-item'
        :class="{errorInput: $v.name.$error}"
    >
      <label>
        Name:
        <input
            :class='{error: $v.name.$error}'
            @change='$v.name.$touch()'
            v-model='name'
        >
        <p
            class='errorText'
            v-if='!$v.name.required'
        >Field is required</p>
        <p
            class='errorText'
            v-if='!$v.name.minLength'
        >Name must have at least {{ $v.name.$params.minLength.min }}!</p>
      </label>
    </div>
    <div
        class='form-item'
        :class="{errorInput: $v.email.$error}"
    >
      <label>
        Email:
        <input
            :class='{error: $v.email.$error}'
            @change='$v.email.$touch()'
            v-model='email'
        >
        <p
            class='errorText'
            v-if='!$v.email.required'
        >Field is required</p>
        <p
            class='errorText'
            v-if='!$v.email.email'
        >Email is not correct!</p>
      </label>
    </div>
    <button
        type='submit'
        class='btn btn_primary'
    >Submit
    </button>
  </form>
</template>

<script lang='ts'>
import Vue from 'vue'
import { required, minLength, email } from 'vuelidate/lib/validators'

export default Vue.extend({
  name: 'ModalValidate',
  props:['modalValidate'],
  data() {
    return {
      name: '',
      email: ''
    }
  },
  validations: {
    name: {
      required,
      minLength: minLength(4)
    },
    email:{
      required,
      email
    }
  },
  methods:{
    onSubmit(){
      this.$v.$touch()
      if(!this.$v.$invalid){
        const user = {
          name: this.name,
          email: this.email
        }
        console.log(user)
        this.email = ''
        this.name = ''
        this.$v.$reset()
        this.modalValidate = false
      }
    }
  }
})
</script>

<style
    lang='scss'
>

.form-item .errorText {
  display: none;
  margin-bottom: 8px;
  font-size: 13px;
  color: #f61118;
}

.form-item {
  &.errorInput .errorText {
    display: block;
  }
}


input.error {
  border-color: #f61118;
}

</style>
