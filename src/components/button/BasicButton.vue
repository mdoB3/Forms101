<template>
  <div>
    <h2 class="ui header">What is your favorite clothing?</h2>
    <ButtonRow />
  </div>
</template>

<script>
import ButtonRow from './ButtonRow.vue'
export default {
  name: 'BasicButton',
  props: {
    msg: String
  },
  components: {
    ButtonRow
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
