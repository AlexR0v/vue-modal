<template>
  <div class='modal__wrapper'>
    <div class='modal-content'>

      <div class='modal-header'>
        <div class='modal-title'>{{ title }}</div>
        <div class='btn-close'>&#10005;</div>
      </div>

      <div class='modal-body'>

      </div>

    </div>
  </div>
</template>

<script lang='ts'>
import Vue from 'vue'

export default Vue.extend({
  name: 'Modal',
  props: {
    title: {
      type: String,
      required: true
    }
  }
})
</script>

<style
    lang='scss'
    scoped
>

.modal__wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  position: fixed;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  transition: opacity .3s ease;
  z-index: 998;
  background-color: rgba(0, 0, 0, .48);
}

.modal-content{
  position: relative;
  max-width: 600px;
  padding: 20px 18px;
  background-color: #fff;
  border: 1px solid #dcdfe6;
  transition: all .3s ease;
  border-radius: 8px;
  z-index: 999;
  overflow: hidden;
}

.modal-header{
  display: flex;
  align-self: center;
  justify-content: space-between;
  padding-bottom: 20px;
  span{
    font-size: 20px;
  }
  .btn-close{
    cursor: pointer;
  }
}

.modal-body{
  text-align: center;
}
</style>
