<template>
  <div id="app">
    <h1>길이 {{ messageLength }}의 메시지 {{ message }}를 입력받음</h1>
    <h3>x2 : {{ doubleLength }}</h3>
    <input type="text" @keyup.enter="onSubmit" v-model="inputData">
    <h1>{{level}}</h1>
  </div>
</template>

<script>
import {mapState, mapActions} from 'vuex'

export default {
  name: 'App',
  components: {
  },
  created() {
    this.$store.dispatch('loadMessage')
  },
  computed: {
    ...mapState(['message']),
    ...mapState(['message']),
    level:state => state.myModule.level,
    // message: state => state.message

    // message() {
    //   return this.$store.state.message
    // },
    // messageLength() {
    //     return this.$store.getters.messageLength
    // },
    // doubleLength() {
    //     return this.$store.getters.doubleLength
    // },
    // ...mapGetters(['messageLength','doubleLength'])
  },
  data() {
    return {
      inputData: null,
    }
  },
  methods: {
    // changeMessage() {
    //   const newMessage = this.inputData
    //   this.$store.dispatch('changeMessage', newMessage)
    //   this.inputData = null
    // },
    // ...mapActions(['changeMessage'])
    ...mapActions({
      actionsChangeMessage : 'changeMessage'
    }),
    onSubmit(){
      const newMessage = this.inputData
      this.actionsChangeMessage(newMessage)
      this.inputData=null
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
