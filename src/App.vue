<template>
  <div style="display: grid; width: 80%; margin: 0 auto;">
    <h1>{{ title }}</h1>
    <!-- <input type="text" ref="name"> -->
    <teleport to=".modals" v-if="showModal">
      <Modal :header="header" :text="text" :theme="theme" @close="toggleModal">
        <template v-slot:links>        
          <a href="">Sign up now</a>  
          <a href="">More Info</a>  
        </template>        
        <h1> Whatever giveaway.</h1>
        <p> Grab your stuff and run.</p>
      </Modal>  
    </teleport>
    
    <teleport to=".modals" v-if="showModalTwo">
      <Modal @close="toggleModal3">
        <h1> Alternative Modal</h1>
        <p> Grab your stuff and run far away.</p>       
      </Modal>  
    </teleport>

    <button @click="toggleModal">Open Modal</button> 
    <button @click="toggleModal2">Open Sale Modal</button> 
    <button @click="toggleModal3">Open Alternative Modal</button> 
  </div>
</template>

<script>
import Modal from './components/Modal.vue'

export default {
  name: 'App',
  data(){
    return {
      title: 'My first Vue App',
      header: "Sign up for the Giveaway!",
      text: "Grab your ninja swag for half price!!",
      showModal: false,
      showModalTwo: false,
      theme: ''
    }
  },
  components: {
    Modal
  },
  methods: {
    handleClick(){
      console.log('handleclick')
      // console.log(this.$refs.name.value)
      // this.$refs.name.classList.add('active')
      // this.$refs.name.focus()
    },
    toggleModal(){
      this.showModal = !this.showModal
      this.theme = ''
    },
    toggleModal2(){
      this.showModal = !this.showModal
      this.theme = 'sale'    
    },
    toggleModal3(){
      this.showModalTwo = !this.showModalTwo   
      this.theme = ''
    },
  },  
}
</script>

<style>
#app, .modals {
  margin: 0;
  padding: 0;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}

.active {
  background: lightgrey;
}

button {
  width: 80%;
  margin: 5px auto;
  padding: 5px;
  border-radius: 5px;
}
</style>
