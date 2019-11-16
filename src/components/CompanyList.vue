<template >
  <div >
  <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-3 col-md-offset-2">
    <h3>Company List</h3>
    <hr>
    <div class="panel-body" v-if='companies.length > 0'>
    <ul class="list-group" v-for='company  of companies'>
      <li class="list-group-item">
        <div class="company" >
          <p> Company Name:{{company.name}}</p>
        </div>
        <div class="btn-toolbar">
          <button class="btn btn-primary"
           v-on:click='deleteCompany(company)'
            name="button7">
            Delete</button>
            <button class="btn btn-primary"
          v-on:click="getDetails(company);showModal();">Details</button>
        </div>
      </li>
    </ul>
  </div>
  </div>
  <company-details-modal
   v-if='showDetails'
   @close="closeModal"
   :company='company_data'></company-details-modal>
</div>
</template>

<script >
import axios from 'axios'
import CompanyDetailsModal from './CompanyDetailsModal.vue'
import EventBus from '../eventbus'
export default{

  components:{
    CompanyDetailsModal
  },
  data(){
    return {
      companies:[],
      showDetails:false,
      selectedCompany:{},
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
    getCompanies(){
      axios.get('http://localhost:9292/companies')
      .then(response => {
        // handle success
        this.companies = response.data;
        console.log(this.companies.length);
      })
      .catch(function () {
        // handle error
      })
      .finally(function () {
        // always executed
      });
    },
    deleteCompany(company){
      //For id we have to add 1 because the index in database  starts from 1
      let id = company.id
      axios.delete('http://localhost:9292/companies/' + id)
      .then(response =>{
        console.log(response);
      });
      this.companies = this.companies.filter(function(item){
        return item !=company
      })
    },
    getDetails(company){
      //For id we have to add 1 because the index in database  starts from 1
      let id = company.id
      axios.get('http://localhost:9292/companies/' + id)
        .then(response => {
          // handle success
          this.company_data = response.data;
          console.log(this.company_data);
        })
        .catch(error =>  {
          console.log(error.response)
        });
    },
    showModal(){

      this.showDetails = true;
      console.log(this.selectedCompany)
      console.log(this.showDetails)
    },
    closeModal(){
      this.showDetails = false;
    }

  },
  mounted(){
    console.log('outside')
    EventBus.$on('Company_Added',()=>{
      console.log('inside')
      this.getCompanies();
    })
  }
}

</script>

<style scoped>
.list-group-item:hover, a.list-group-item:focus {text-decoration: none;background-color: rgb(245, 245, 245);}
.list-group { margin-bottom:0px; }
.list-group-item{
  overflow: hidden;
}

.company{
  float: left;
  margin-top: 7px
}
.btn-toolbar{
  float: right;
  margin-left: 10px;
}

.panel-body{
  width: 350px;
}

</style>
