<template>
  <q-page padding>
  <input v-model="message"
  @keyup.esc="handleKeyup"
  @keyup.enter="alertMessage"
  v-autofocus
  :class="{ 'error' : message.length>22 }"
  ref="messageInput"/>

  <button @click="clearMessage">CLEAR</button>
  <div>{{ message.length }} </div>

  <h5 class="border-grey"
  v-if="message.length">{{ message }}</h5>
  <h6 v-else> No message entered :( </h6>
  <hr>

  <p> Uppercase message: {{ messageUppercase() }}</p>
  <p> Lowercase message: {{ message | messageLowercase }}</p>
  </q-page>
</template>

<script>
export default {
  data () {
    return {
      message: 'I love Vue.js so hard!'
    }
  },
  computed: {
    errorStyle () {
      if (this.message.length > 22) {
        return {
          color: 'red',
          'background-color': 'pink'
        }
      }
      return 'test'
    }
  },
  methods: {
    clearMessage () {
      this.message = ''
    },
    handleKeyup () {
      this.clearMessage()
    },
    alertMessage () {
      alert(this.message)
    },
    messageUppercase () {
      return this.message.toUpperCase()
    }
  },
  filters: {
    messageLowercase (value) {
      return value.toLowerCase()
    }
  },
  directives: {
    autofocus: {
      inserted (el) {
        el.focus()
      }
    }
  },
  beforeCreate () {
    console.log('beforeCreate')
  },
  created () {
    console.log('created')
  },
  beforeMount () {
    console.log('beforeMount')
  },
  mounted () {
    console.log(this.$refs)
    this.$refs.messageInput.className = 'bg-green'
  },
  beforeUpdate () {
    console.log('beforeUpdate')
  },
  updated () {
    console.log('updated')
  },
  beforeDestroy () {
    console.log('beforeDestroy')
  },
  destroyed () {
    console.log('destoryed')
  }
}

</script>

<style>
  .border-grey {
    border : 1px solid grey;
  }
  .error{
    color: red;
    background-color: pink;
  }
</style>
