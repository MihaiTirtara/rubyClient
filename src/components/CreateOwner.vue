<template >
  <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-2 col-md-offset-1" >
    <form >
      <h3>Add an owner</h3>
      <hr>
      <div class="form-group">
          <label for="name">Name</label>
          <input
                  type="text"
                  placeholder='Required'
                  id="name"
                  class="form-control"
                  v-model='owner_data.name'>
      </div>
      <div class="form-group">
          <label for="address">Company ID</label>
          <input
                  type="text"
                  placeholder='Required'
                  id="company id"
                  class="form-control"
                  v-model='owner_data.company_id'>
      </div>
    </form>
    <button
            class="btn btn-primary"
            @click.prevent='addOwner'>Submit!
    </button>
  </div>
</template>
<script >
import axios from 'axios'
export default{
  data() {
    return{
      owner_data:{
        name:'',
        company_id:''
      }
    }
  },
  methods:{
    addOwner(){
      var params = new URLSearchParams();
      let name = this.owner_data.name;
      let id = this.owner_data.company_id;
      let tryout = this.owner_data;
      params.append('name',name)
      params.append('company_id',id)
      console.log(params);
      axios.post(' https://ancient-escarpment-92868.herokuapp.com/owners',params)
        .then(response => {
           console.log(response)
         })
         .catch(error => {
           console.log(error.response)
         });
    }
  }
}
</script>

<style scoped>

</style>
