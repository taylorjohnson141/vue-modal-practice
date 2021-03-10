<template>
  <h1>{{title}}</h1>
  <div v-if="showModal">
  <Modal :title = "title" :text = "text" :theme = 'theme' :changeTheme = "changeTheme" @close = "ToggleModal">
    <p>Hello</p>
    <p>World</p>
    <template v-slot:links>
      <a href = '#'>Text</a>
      <a href = '#'>Mas</a>
      <a href ='#'>more</a>
      
    </template>
  </Modal>
  </div>
  <button @click = "ToggleModal"> Show Modal</button>
</template>

<script>
  import Modal from './components/Modal.vue'

export default {
  name: 'App',
  components:{Modal},
  data() {
    return {
      title:"It's a title",
      title:"I am a title",
      text:"I am text",
      theme:'cold',
      showModal:false
    } 
  },
  methods:{
    handleClick(){
      console.log(this.$refs.name)
      this.$refs.name.classList.add('active')
      this.$refs.name.focus()
    },
    changeTheme(){
      console.log('here')
      if(this.theme === "cold"){
        this.theme = "warm"
      }
      else{
        this.theme = "cold"
      }
    },
    ToggleModal() {
      this.showModal = !this.showModal
    }
  }
}
</script>

<style>
.active{
  background-color: royalblue;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1{
  color: red;
}
</style>
