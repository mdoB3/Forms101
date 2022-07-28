<template>
  <div id="app">
    <BasicButton />
    <TextInput />
     <Fields />
  </div>
</template>

<script>
import BasicButton from './components/button/BasicButton.vue'
import TextInput from './components/input/TextInput.vue'
import Fields from './components/multipleFields/Fields.vue'

export default {
  name: 'App',
  components: {
    BasicButton,
    TextInput,
    Fields
    }
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
