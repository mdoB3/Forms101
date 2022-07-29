<template>
  <div>
    <h2 class="ui header">Add items to List</h2>
    <div class="input-form">
        <form @submit="submitForm" class="ui form">
            <div class="field">
                <input v-model="newItem" type="text" placeholder="Add an item!">
            </div>
            <button class="ui button">Submit</button>
        </form>
        <div class="ui segment">
            <h4 class="ui header">Items</h4>
            <ul>
                <li v-for="(item ,index) in items" class="item" :key="index">
                    {{ item }}
                </li>
            </ul>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TextInput',
  data() {
    return {
        items: [],
        newItem: ''
    }
  },
  methods: {
    submitForm(evt) {
        this.items.push(this.newItem);
        this.newItem = '';
        evt.preventDefault();
    }
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
   div {
    border: 1px solid black;
    max-width: 30vw;
    margin: auto;
   }
</style>
