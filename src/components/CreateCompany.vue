<template >
  <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-4 col-md-offset-0">
      <form >
        <h3>Add a company</h3>
        <hr>
        <div class="form-group">
            <label for="name">Name</label>
            <input
                    type="text"
                    placeholder='Required'
                    id="name"
                    class="form-control"
                    v-model='company_data.name'>
        </div>
        <div class="form-group">
            <label for="address">Adress</label>
            <input
                    type="text"
                    placeholder='Required'
                    id="adress"
                    class="form-control"
                    v-model='company_data.adress'>
        </div>
        <div class="form-group">
            <label for="country">Country</label>
            <input
                    type="text"
                    placeholder='Required'
                    id="country"
                    class="form-control"
                    v-model='company_data.country'>
        </div>

        <div class="form-group">
            <label for="city">City</label>
            <input
                    type="text"
                    placeholder='Required'
                    id="city"
                    class="form-control"
                    v-model='company_data.city'>
        </div>

        <div class="form-group">
            <label for="email">E-mail</label>
            <input
                    type="text"
                    id="email"
                    class="form-control"
                    v-model='company_data.email'>
        </div>

        <div class="form-group">
            <label for="phoneNumber">Phone Number</label>
            <input
                    type="text"
                    id="phoneNumber"
                    class="form-control"
                    v-model='company_data.phoneNumber'>
        </div>
      </form>
        <button
                class="btn btn-primary"
                @click.prevent='addCompany'>Submit!
        </button>

  </div>
</template>

<script >
import axios from 'axios'
import EventBus from '../eventbus.js'
export default {

  data() {
    return{
      company_data:{
        name:'',
        adress:'',
        country:'',
        city:'',
        email:'',
        phoneNumber:'',
      },
    }
  },
  methods:{
    addCompany(){
      // let name = this.company_data.name
      // let adress = this.company_data.adress
      // let country = this.company_data.country
      // let city = this.company_data.city
      // let email = this.company_data.email
      // let phoneNumber = this.company_data.phoneNumber

      var params = new URLSearchParams();
      params.append('name', this.company_data.name);
      params.append('adress', this.company_data.adress);
      params.append('country', this.company_data.country);
      params.append('city', this.company_data.city);
      params.append('email', this.company_data.email);
      params.append('phoneNumber', this.company_data.phoneNumber);
      // params.append('company',this.company_data)

      axios.post(' https://ancient-escarpment-92868.herokuapp.com/companies',params)
        .then(response => {
	         console.log(response)
           EventBus.$emit('Company_Added','company')
         })
         .catch(error => {
           console.log(error.response)
         });

  },
  }
}
</script>

<style scoped>

</style>
