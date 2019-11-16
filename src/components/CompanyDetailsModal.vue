<template >
<div>
  <transition name="modal-fade">
    <div class="boxmodal">
      <div class="contentContainer">
        <div class="closeMessageModalWrapper" >
            <img src="@/assets/closeIcon.png" alt="Close Icon" >
            <button
                    type="button"
                    class="btn-close"
                    @click="close"
                    aria-label="Close modal"
                  >
                    x
                  </button>
            <!-- <close-icon @closeEvent ="close()" ></close-icon> -->
        </div>
        <h2>{{company.name}}</h2>
        <ul>
          <li>
          <p>ID:{{company.id}}</p>
        </li>
          <li>
        <p>Country:{{company.country}}</p>
        </li>
        <li>
      <p>City:{{company.city}}</p>
      </li>
      <li>
    <p>Adress:{{company.adress}}</p>
    </li>
      <li>
    <p>E-mail:{{company.email}}</p>
    </li>
    <li>
  <p>Phone:{{company.phoneNumber}}</p>
  </li>
 </ul>
  </div>
 </div>
 </transition>
</div>
</template>

<script>
export default {
  name:'DetailsModal',
  props:{
    company:{
      type:Object
    }
  },
  methods:{
    close(){
      this.$emit('close')
    }
  }
}
</script>

<style scoped>

.boxmodal {
  background-color: rgba(0, 0, 0, 0.8);
  position: fixed;
  z-index: 1000;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  display: flex;
  justify-content: center;
  align-items: center;
}
.contentContainer {
  position: relative;
  background-color: white;
  width: 500px;
  height: 300px;
  border-radius: 5px;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: center;
}

   .modal-body {
    position: relative;
    padding: 20px 10px;
  }

  .closeMessageModalWrapper {
    position: absolute;
    top: 0px;
    right: 5px;
  }

  .closeMessageModalWrapper img {
      width: 100px;
      height: 30px;
  }

p{

font-style: italic;
font-size: 20px;
text-align: center;
}
ul{
  text-align: center;
}
li{
  margin-right: 250px;
}

</style>
