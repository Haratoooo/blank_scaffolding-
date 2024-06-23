<template>
  <div>
    <b-table striped hover :items="items" :fields="fields"></b-table>
      <b-form @submit="onSubmit" @reset="onReset" v-if="show">
      <b-form-group
        id="input-group-1"
        label="Email address:"
        label-for="input-1"
        description="We'll never share your email with anyone else."
      >
        <b-form-input
          id="input-1"
          v-model="form.email"
          type="email"
          placeholder="Enter email"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-2" label="Password:" label-for="input-2">
        <b-form-input
          id="input-2"
          v-model="form.password"
          placeholder="Password"
          required
        ></b-form-input>
      </b-form-group>

      <b-button type="button" variant="primary" @click="register()">Sign Up</b-button>
    </b-form>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        items: null,
        fields: ['id', 'USERNAME']
      }
    },
    methods:{
      get_accounts(){
        axios.get('/get_accounts').then(response=>{
          console.log(response.data);
          this.items = response.data;
        }).catch(error=>{
          console.log(error.data);
        })
      }
    },
    beforeMount(){
      this.get_accounts();
    }
  }
</script>
