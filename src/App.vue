<template>
  <div id="app" class="App d-flex align-items j-center">
      <Success :success="stayThere"/>

      <Modal 
        :modal="openModal" 
        @nowClose="closePopup" 
        :form="userData"
        @showSuccessModal="openSuccess"
      />

      <div class="App-content d-flex align-items">
        <TextBox/>
        <FormBox
         @nowShow="showPopup" 
         :form="userData" 
         :error="err"
         />
      </div>
  </div>
</template>

<script>

import TextBox from '@/components/Textbox';
import FormBox from '@/components/Form'
import Modal from '@/components/Modal'
import Success from '@/components/Success'

export default {
  name: 'App',
  data(){
    return {
      openModal: false,
      stayThere: false,
      userData:{
          firstName: '',
          lastName: '',
          emailAdd: '',
          password: ''
      }, 
      err: {
        firstName: '',
        lastName: '',
        emailAdd: '',
        password: '',
        icon: '',
        line: ''
      }
    }
  },
  components:{
    TextBox,
    FormBox,
    Modal,
    Success
  },
  methods: {
    validEmail(email) {
      var re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      return re.test(email);
    },
    setErrorFor(){
        this.err.icon = "fa fa-exclammation-circle"
        this.err.line = "red-border"
        this.openModal = false
    },
    setSuccessFor(){
      this.err.icon = ""
      this.err.line = "no-red-border"
      this.openModal = true
    },
    showPopup(){
        let _this = this;

        if(this.userData.firstName == ""){
          this.err.firstName = "First Name cannot be empty"
          _this.setErrorFor()
        }else{
          this.err.firstName = ""
          _this.setSuccessFor()
        }

        if(this.userData.lastName == ""){
          this.err.lastName = "Last Name cannot be empty"
          _this.setErrorFor()
        }else{
          this.err.lastName = ""
          _this.setSuccessFor()
        }

        if(this.userData.password == ""){
          this.err.password = "Password cannot be empty"
          _this.setErrorFor()
        }else{
          this.err.password = ""
          _this.setSuccessFor()
        }
        
        if(this.userData.emailAdd == ""){
          this.err.emailAdd = "Email cannot be empty"
          _this.setErrorFor()
        }
        else if(!this.validEmail(this.userData.emailAdd)){
          this.err.emailAdd = "Looks like this is not an email"
          _this.setErrorFor()
        }else{
          this.err.emailAdd = ""
          _this.setSuccessFor()
        }

        

    },
    
    closePopup(){
      this.openModal = false
    },
    openSuccess(){
      this.openModal = false
      this.stayThere = true
      setTimeout(() => {
        this.stayThere = false;
      }, 3000)
      this.userData.firstName = ''
      this.userData.lastName = ''      
      this.userData.emailAdd = ''      
      this.userData.password = ''
    }
  }
}
</script>

<style>
  body, *, *::after, *::before{
    padding: 0;
    margin: 0;
    outline: none;
    border: none;
  }

  @font-face{
     font-family: 'Poppins-Regular'; 
     src: url('./assets/font/Poppins-Regular.ttf') format('truetype') 
  }

  @font-face{
     font-family: 'Poppins-Bold'; 
     src: url('./assets/font/Poppins-Bold.ttf') format('truetype') 
  }

  .poppins-reg{
    font-family: 'Poppins-Regular'
  }

  .poppins-bold{
    font-family: 'Poppins-Bold'
  }

  .text-white{
    color: #fff;
  }

  .text-center{
    text-align: center;
  }

  .text-left{
    text-align: left;
  }

  .text-right{
    text-align: right
  }

  .App{
    min-height: 100vh;
    font-family: 'Nunito Sans', sans-serif;
    position: relative;
    background: url('./assets/images/bg-intro-desktop.png'), linear-gradient(hsl(0, 100%, 74%),hsl(0, 100%, 74%))
  }

  .cursor-pointer{
    cursor: pointer;
  }

  button{
    background: transparent;
    border: none;
    outline: none;
  }

  button:hover, button:focus{
    border: none;
    outline: none;
  }

  .d-flex{
    display: flex;
  }

  .j-btw{
    justify-content: space-between;
  }

  .j-center{
    justify-content: center;
  }

  .dc-flex{
    display: flex;
    flex-direction: column;
  }

  .align-items{
    align-items: center;
  }

  .align-self{
    align-self: center;
  }

  .cursor-point{
    cursor: pointer;
  }

  .mt-5{
    margin-top: 5px;
  }

  .mb-5{
    margin-bottom: 5px;
  }

  .mt-10{
    margin-top: 10px;
  }

  .mb-10{
    margin-bottom: 10px;
  }

  .App-content{
    width: 1100px;
    /* height: 120px; */
    /* background: blue; */
  }

  input{
    text-indent: 30px;
    width: 100%;
    height: 50px;
    margin-top: 13px;
    border-radius: 5px;
    border: 1.43px solid hsla(246, 25%, 77%, 0.6);
    font-family: 'Poppins-Bold';
    transition: border .3s ease-in-out;
  }

  input:focus{
      border-color: hsl(249, 10%, 26%) ;
  }

  button{
    height: 48px;
    line-height: 50px;
    border-radius: 5px;
    text-transform: uppercase;
    font-size: 16px;
    cursor: pointer;
  }

  .text-red{
    color: hsl(0, 100%, 74%)
  }


</style>