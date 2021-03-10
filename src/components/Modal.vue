<template>
  <div class="backdrop" @click.self = "closeModal">
    <div class="modal" :class="{cold: theme === 'cold', warm: theme ==='warm'}">
      <h1>{{title}}</h1>
      <p>{{text}}</p>
      <slot></slot>
      <div>
        <slot name = 'links'></slot>
      </div>
      <button @click="changeTheme"> change Theme</button>
    </div>
  </div>

</template>

<script>
export default {
  props:["title","text","theme","changeTheme","ToggleModal"],
  methods:{
    closeModal(){
      this.$emit('close')
    }
  }
}
</script>

<style >
.modal {
    width: 400px;
    padding: 20px;
    margin: 100px auto;
    background: white;
    border-radius: 10px;
  }
  .backdrop {
    top: 0;
    position: fixed;
    background: rgba(0,0,0,0.5);
    width: 100%;
    height: 100%;
  }
  .modal.cold{
    color: red;
    background-color: blue;
  }
  .modal.warm{
    color: blue;
    background-color: red;
  }
</style>