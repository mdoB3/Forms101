<!-- To avoid adding property on each input on data, lets create fields object to store the values for all fields in one place -->
<template>
  <div>
    <h2 class="ui header">Add items to List</h2>
    <div class="input-form">
        <form @submit="submitForm" class="ui form">
            <div class="field">
                <label>New item</label>
                <input v-model="fields.newItem" type="text" placeholder="Add an item!" />
            </div>
            <div class="field">
                <label>Email</label>
                <input v-model="fields.email" type="text" placeholder="your email?" />
            </div>
            <div class="field">
                <label>Urgency</label>
                <select v-model="fields.urgency" class="ui fluid search dropdown">
                    <option value="" disabled>Please select one</option>
                    <option>Nonessential</option>
                    <option>Moderate</option>
                    <option>Urgent</option>
                </select>
            </div>
            <div class="field">
                <div class="ui checkbox">
                    <input v-model="fields.termsAndConditions" type="checkbox" />
                </div>
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
  name: 'Fields',
  data() {
    return {
        // store data in fields object for all inputs
        fields: {
            email: '',
            newItem: '',
            urgency: '',
            termsAndConditions: false,
        },
        items: [],
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
</style>
