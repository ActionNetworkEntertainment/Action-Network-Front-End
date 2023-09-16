<script setup>
import router from '../router'
if(localStorage.getItem("user")) router.push('myProfile');
</script>

<template>
  <main>
    <div class="welcomeWrapper">
        <div class='welcomeBox'>
          <img src="../assets/images/ANLogoCircleFlatGradient.png">
          <h1>Welcome To Action Network</h1>
          <p>Unlock Resources, Connect with Passionate Artists, and Ignite Your Film Journey.</p>
          <br>
          <router-link to="/login"><button class="btn btn-primary">Get Started</button></router-link>
        </div>
      </div>
    
    
  </main>
</template>


<style>
  .welcomeWrapper{
    position:relative;
    width:100%;
    height:100%;
  }
  .welcomeBox{
    position:absolute;
    left:50%;
    margin-left:-225px;
    top:50%;
    margin-top:232.5px;
    width:450px;
    height:465px;
    background: var(--color-background-mute); 
    border-radius: 20px;
    text-align: center;
    padding-top:31px;
  }
  .welcomeBox img{
    width: 100px;
    height: 100px;
    flex-shrink: 0;
    margin-bottom:10px
  }
  .welcomeBox h1{
    width:280px;
    margin:0 auto;
    border-bottom: solid 1px var(--color-border);
  }
  .welcomeBox p{
    width: 345px;
    margin:10px auto;
    line-height: 30px;
  }
  .welcomeBox .btn{
    width:90%;
    margin-left:5%;
    margin-right:5%;
    margin-top: 5%;
    padding: 25px;
  }
</style>