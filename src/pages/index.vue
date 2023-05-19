<template>
  <form ref="formRef" @submit.prevent="sendSolutions" class="solux-pay-container">
    <span class="solux-pay-text">Payment Successful</span>
    <div class="solux-pay-container1">
      <img
        src="../assets/parcel.png"
        alt="image"
        class="solux-pay-image"
      />
      <span class="solux-pay-text1">
        Your packet is ready, enter your email address below in other to receive
        the solutions
      </span>
      <input
      v-model="name"
        type="text"
        placeholder="Your Name"
        name="to_name"
        class="solux-pay-textinput input"
      />
      <input
      v-model="email"
        type="text"
        placeholder="Your Email"
        name="to_email"
        class="solux-pay-textinput1 input"
      />
      <button :loading="loading" 
      type="submit"
       class="solux-pay-find button">
        <span>
          <span class="solux-pay-text3">Receive Solutions</span>
          <br />
        </span>
      </button >
    </div>
    <div class="solux-pay-container2">
      <span class="solux-pay-text5">
        Copyright © 2023 All Rights Reserved By Novus Technologies
      </span>
    </div>
  </form>
</template>
<script setup lang="ts">
import {ref} from 'vue'
import emailjs from '@emailjs/browser'

const loading = ref(false)
const name = ref('')
const email = ref('')
const formRef=ref()
const templateParams =ref({
    to_name: name.value,
    to_email: email.value,
    reply_to:`uili.kam8@gmail.com`
})
const templateParams2 = {
  to_name: 'name.value',
    to_email: 'akpojohn6@gmail.com',
    reply_to:`uili.kam8@gmail.com`
}

 function sendSolutions(){
  //loading.value=true;
  const serviceID = 'default_service';
   const templateID = 'template_3dk0hnq';

   console.log(name.value, ' ', email.value)

   emailjs.sendForm('service_wl0d549', 'template_3dk0hnq', formRef.value, "eOW2SzISsaKlOpkoX" )
    .then(() => {
      loading.value=false
      alert('Sent!');
    }, (err) => {
      alert(JSON.stringify(err));
    }).catch(
      (err)=> {alert(err)}
    )
 }
 
//  function sendSolutions(){
//   var data = {
//     service_id: 'default_service',
//     template_id: 'template_3dk0hnq',
//     user_id: 'eOW2SzISsaKlOpkoX',
//     template_params: {
//     to_name: name.value,
//     to_email: email.value,
//     reply_to:`uili.kam8@gmail.com`
//     }
// };
 
// $.ajax('https://api.emailjs.com/api/v1.0/email/send', {
//     type: 'POST',
//     data: JSON.stringify(data),
//     contentType: 'application/json'
// }).done(function() {
//     alert('Your mail is sent!');
// }).fail(function(error) {
//     alert('Oops... ' + JSON.stringify(error));
// });
//  }

</script>

<style scoped>
.solux-pay-container {
  width: 100%;
  display: flex;
  overflow: auto;
  min-height: 100vh;
  align-items: center;
  flex-direction: column;
  justify-content: center;
}
.solux-pay-text {
  color: #2f2f2f;
  font-size: 48px;
  font-style: normal;
  margin-top: 5vw;
  text-align: center;
  font-family: Roboto;
  font-weight: 700;
  text-transform: uppercase;
}
.solux-pay-container1 {
  width: 100vw;
  height: 783px;
  display: flex;
  align-items: center;
  padding-top: 2%;
  flex-direction: column;
}
.solux-pay-image {
  width: 289px;
  height: 227px;
  margin-top: var(--dl-space-space-unit);
  object-fit: cover;
  margin-bottom: var(--dl-space-space-unit);
}
.solux-pay-text1 {
  color: #2f2f2f;
  font-size: 32px;
  font-style: normal;
  margin-top: 4%;
  text-align: center;
  font-family: Poppins;
  font-weight: 500;
  text-transform: capitalize;
}
.solux-pay-textinput {
  width: 80%;
  height: 58px;
  margin-top: var(--dl-space-space-twounits);
  border-color: #b1865b;
  border-width: 2px;
  border-radius: var(--dl-radius-radius-radius8);
}
.solux-pay-textinput1 {
  width: 80%;
  height: 58px;
  margin-top: var(--dl-space-space-twounits);
  border-color: #b1865b;
  border-width: 2px;
  border-radius: var(--dl-radius-radius-radius8);
}
.solux-pay-find {
  color: var(--dl-color-gray-white);
  align-self: center;
  font-style: normal;
  margin-top: var(--dl-space-space-threeunits);
  transition: 0.3s;
  font-weight: 500;
  padding-top: var(--dl-space-space-unit);
  border-width: 0px;
  padding-left: var(--dl-space-space-oneandhalfunits);
  border-radius: 56px;
  padding-right: var(--dl-space-space-oneandhalfunits);
  padding-bottom: var(--dl-space-space-unit);
  background-color: #b1865b;
}
.solux-pay-find:hover {
  opacity: 0.5;
}
.solux-pay-text3:hover {
  opacity: 0.5;
}
.solux-pay-container2 {
  flex: 0 0 auto;
  width: 100%;
  height: 100px;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #b1865b;
}
.solux-pay-text5 {
  color: #ffffff;
  font-family: Poppins;
}
@media(max-width: 991px) {
  .solux-pay-find {
    width: 139px;
    text-align: center;
    margin-right: 0px;
  }
  .solux-pay-text3 {
    width: 139px;
    text-align: center;
    margin-right: 0px;
  }
  .solux-pay-container2 {
    height: 117px;
  }
}
@media(max-width: 767px) {
  .solux-pay-container1 {
    padding-left: 5vw;
    padding-right: 5vw;
  }
  .solux-pay-find {
    width: 137px;
  }
  .solux-pay-text3 {
    width: 137px;
  }
  .solux-pay-container2 {
    height: 126px;
  }
}
@media(max-width: 474px) {
  .solux-pay-text {
    font-size: 42px;
    padding-top: 5vw;
    padding-left: 5vw;
    text-transform: capitalize;
  }
  .solux-pay-container1 {
    width: 100%;
    height: 843px;
    padding-left: 5vw;
    padding-right: 5vw;
  }
  .solux-pay-image {
    margin-top: var(--dl-space-space-twounits);
    margin-bottom: var(--dl-space-space-twounits);
  }
  .solux-pay-textinput {
    width: 80%;
    height: 72px;
  }
  .solux-pay-textinput1 {
    width: 80%;
    height: 72px;
  }
  .solux-pay-find {
    margin-top: var(--dl-space-space-twounits);
  }
  .solux-pay-text3 {
    margin-top: var(--dl-space-space-oneandhalfunits);
  }
  .solux-pay-container2 {
    height: 110px;
    background-color: #b1865b;
  }
  .solux-pay-text5 {
    color: #ffffff;
    font-size: 12px;
  }
}
</style>
