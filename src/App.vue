<template>
  <h1>{{ title }}</h1>
  <p>Welcome...</p>
  <teleport to=".modals" v-if="showModal">
    <!--
    <Modal v-bind:header="header" v-bind:text="text" theme="sale" v-on:closeModal="toggleModal" />
    -->
    <Modal theme="sale" v-on:closeModal="toggleModal">
            <template v-slot:links>
              <a href="#">sign up now</a>
              <a href="#">login</a>
            </template>
            <h1>{{ header }}</h1>
            <p>{{ text }}</p>
    </Modal>
  </teleport>
  <teleport to=".modals" v-if="showModal2">
    <Modal v-on:closeModal="toggleModal2">
            <template v-slot:links>
              <a href="#">2</a>
              <a href="#">2</a>
            </template>
            <h1>{{ header }}</h1>
            <p>{{ text }}</p>
    </Modal>
  </teleport>
  <button v-on:click.alt="toggleModal">open modal(alt)</button>
  <button v-on:click.alt="toggleModal2">open modal2(alt)</button>
  <!--
  <input type="text" ref="name">
  <button v-on:click="handleClick">click</button>
  -->
</template>

<script>
import Modal from './components/Modal'

export default {
  components:{
    Modal,
  },
  name: 'App',
  data(){
    return{
      title: 'Vue app',
      header: 'sign up for the giveaway',
      text: 'grab a ninja smoothie',
      showModal: false,
      showModal2: false
    }
  },
  methods:{
    /*
    handleClick(){
      console.log(this.$refs.name)
      this.$refs.name.classList.add('active')
      this.$refs.name.focus()
    }
    */
   toggleModal(){
     this.showModal = !this.showModal
   },
   toggleModal2(){
     this.showModal2 = !this.showModal2
   }
  }
}
</script>

<style>
#app, .modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1{
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
