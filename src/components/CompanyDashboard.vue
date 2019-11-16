<template >
<div class="wrapper">

<div class="container">
        <div class="row">
          <create-company></create-company>
          <create-owner></create-owner>
          <company-list></company-list>
        </div>

</div>
</div>
</template>

<script>
import axios from 'axios'
import CreateCompany from './CreateCompany.vue'
import CreateOwner from './CreateOwner.vue'
import CompanyList from './CompanyList.vue'
export default {
  components:{
    CreateCompany,
    CreateOwner,
    CompanyList
  },
  methods:{
  editCompany(){
    var params = new URLSearchParams
    let id = this.selectedCompanyIndex
    let company_data2 = {
      name:'mer',
      adress:'gg',
      country:'',
      city:'',
      email:'',
      phoneNumber:'',
      owners:[]
    };

    var params = new URLSearchParams();
    params.append('name', company_data2.name);
    params.append('adress', company_data2.adress);
    params.append('country', company_data2.country);
    params.append('city', company_data2.city);
    params.append('email', company_data2.email);
    params.append('phoneNumber', company_data2.phoneNumber);
    console.log(this.company_data)

    axios.patch('http://localhost:9292/companies/1',{
      data:this.company_data
    })
      .then(response => {
        // handle success
        console.log(response);
      })
      .catch(error =>  {
        console.log(error.response)
      });
    },
    addOwner(){
      var params = new URLSearchParams();
      let name = this.owner_data.name;
      let id = this.owner_data.company_id;
      let tryout = this.owner_data;
      params.append('name',name)
      params.append('company_id',id)
      console.log(params);
      axios.post('http://localhost:9292/owners',params)
        .then(response => {
           console.log(response)
         })
         .catch(error => {
           console.log(error.response)
         });
    }
},

}
</script>
<style >

</style>
