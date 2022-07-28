<!-- To avoid adding property on each input on data, lets create fields object to store the values for all fields in one place -->
<template>
   <div>
      <h2 class="ui header">Add items to List</h2>
      <div class="input-form">
         <form @submit="submitForm" class="ui form">
            <div class="field">
               <label>New item</label>
               <input v-model="fields.newItem" type="text" placeholder="Add an item!" />
               <span style="color: red"> {{ fieldErrors.newItem }}</span>
            </div>
            <div class="field">
               <label>Email</label>
               <input v-model="fields.email" type="text" placeholder="your email?" />
               <span style="color: red"> {{ fieldErrors.email }}</span>
            </div>
            <div class="field">
               <label>Urgency</label>
               <select v-model="fields.urgency" class="ui fluid search dropdown">
                  <option value="" disabled>Please select one</option>
                  <option>Nonessential</option>
                  <option>Moderate</option>
                  <option>Urgent</option>
               </select>
               <span style="color: red"> {{ fieldErrors.urgency }}</span>
            </div>
            <div class="field">
               <div class="ui checkbox">
                  <input v-model="fields.termsAndConditions" type="checkbox" />
                  <span style="color: red"> {{ fieldErrors.termsAndConditions }}</span>
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
           // Object to store Validation errors if they exist
           fieldErrors: {
               email: undefined,
               newItem: undefined,
               urgency: undefined,
               termsAndConditions: undefined,
           },
           items: [],
       }
     },
     methods: {
        submitForm(evt) {
        // use validateForm to determine if form is valid for submission
          evt.preventDefault();
          this.fieldErrors = this.validateForm(this.fields);

          if(Object.keys(this.fieldErrors).length) return;
          this.items.push(this.newItem);
          this.newItem = '';
          this.email = '';
          this.urgency = '';
          this.termsAndConditions = false;
       },
       validateForm(fields) {
           // insure that fields are present.
           // either return an empty obj if there are no issues, or if there are issues, it will return obj with keys corresponding to each field name and values c. to each error msg.
           const errors = {};
           if (!fields.newItem) errors.newItem = "New item required";
           if (!fields.email) errors.email = "email required";
           if (!fields.urgency) errors.urgency = "urgency required";
           if (!fields.termsAndConditions) {
               errors.termsAndConditions = "Terms and conditions have to be approved"
           }
           if(fields.email && !this.isEmail(fields.email)) {
               errors.email = "invalid email";
           }
           return errors;
       },
       isEmail(email) {
           const re = /\S+@\S+\.\S+/;
           return re.test(email);
       },
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
