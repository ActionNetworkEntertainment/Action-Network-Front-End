<script setup>
import '../components/scripts/login'
import router from '../router';
var tempCode;
var currentUser;
if(localStorage.getItem("user")) router.push('myProfile');
async function login() { 
     
  try {
    const response = await fetch(`http://localhost:1337/user/login?phoneNumber=${$("#user_phone").val()}`, {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
    });

    
    if (response.ok) {
      const user = await response.json();
      $("#user_phone").prop("disabled", true);
      currentUser = user.data.currentUser;
      tempCode = user.data.temporaryCode
      
      $("#temporary_code").show();
      $("#login").hide();
      $("#submit_code").show();


    } else {
      console.error('Error fetching users:', response.statusText);
    }
  } catch (error) {
    console.error('Error:', error);
  }

  
}

async function submitCode(){
    if(`${$("#temporary_code").val()}` === `${tempCode}`){
        console.log("Access Granted");
        localStorage.setItem("user", JSON.stringify(currentUser));
        // This is an example script - don't forget to change it!
        LogRocket.identify(currentUser.id, {
            name: currentUser.fullName,
            email: currentUser.email,

        // Add your own custom user variables here, ie:
        
        });
        //router.push({path: 'myAccount'});
        router.push('myProfile');
    }
    else{
        $("#codeValidation").show();
        console.log("WRONG CODE.")
    }
}
</script>

<template>
  <main>
    <div class="loginWrapper">
        <div class='loginBox'>
          <img src="../assets/images/ANLogoCircleFlatGradient.png">
          <h1>Almost There...</h1>
          <p>Whether you're a newcomer or a returning member, just input your phone number, and we'll send a single-use code for account access.</p>
          <form class="loginForm">
            <input id="user_phone" name="phoneNumber" type="tel" placeholder="Enter Phone Number">
            <br>
            <input style="display: none;" id="temporary_code" name="temporaryCode" type="text" placeholder="Temporary Code">
            <p id='codeValidation' style="display:none; color:red;">Incorrect Code!</p>
          </form>
          <button id='login' class="btn btn-primary" @click="login"><h4>Enter</h4></button>
          <button style="display:none" id='submit_code' class="btn btn-primary" @click="submitCode()"><h4>Enter</h4></button>
        </div>
    </div>
    
    
  </main>
</template>

<style>
    .loginForm input{
        width:90%;
        height: 60px;
        flex-shrink: 0;
        border-radius: 8px;
        border: 1px solid var(--blue-b-700, #292F3B);
        background: var(--dark-g-800, #0F1626);
        color: var(--blue-b-60, #B5B6BB);
        font-family: Inter;
        font-size: 16px;
        font-style: normal;
        font-weight: 400;
        line-height: normal;
        padding:15px;
    }
  .loginWrapper{
    position:relative;
    width:100%;
    height:100%;
  }
  .loginBox{
    position:absolute;
    left:50%;
    margin-left:-225px;
    top:50%;
    margin-top:232.5px;
    width:450px;
    height:fit-content;
    background: var(--color-background-mute); 
    border-radius: 20px;
    text-align: center;
    padding-top:31px;
    padding-bottom:25px;
  }
  .loginBox img{
    width: 100px;
    height: 100px;
    flex-shrink: 0;
    margin-bottom:10px
  }
  .loginBox .btn{
    width:90%;
  }
</style>

<script>
    
</script>