<script setup>
import Navbar from '../components/Navbar.vue';
import router from '../router'
if(!localStorage.getItem("user")) router.push('/');
const user = JSON.parse(localStorage.getItem('user'));
</script>

<template>
  <main>
    <Navbar :user="user"/>
    <br>
    <div class="container">
        <div class="row">
            <div class="col-sm-9">
                <div class="bannerImage">
                    <div class="row userInfo">
                        <div class="col-sm-2">
                            <img :src="user.profileImageURL" class="headerProfileImage">
                            <h3>{{ user.fullName }}</h3>
                            <p>{{ user.specialty }}</p>
                        </div>
                        <div class="col-sm-10">
                            <div class="statistics row">
                                    <div class="col-sm-3">
                                        <div class="stat">
                                            <div class="row">
                                                <div class="col-sm-3">
                                                    <span class="material-symbols-outlined staticon">
                                                        movie
                                                    </span>
                                                </div>
                                                <div class="col-sm-9">
                                                    <p>Films</p>
                                                    <h5>0</h5>
                                                </div>
                                                
                                            </div>
                                            
                                        </div>
                                        
                                    </div>
                                    <div class="col-sm-3">
                                        <div class="stat">
                                            <div class="row">
                                                <div class="col-sm-3">
                                                    <span class="material-symbols-outlined staticon">
                                                        network_node
                                                    </span>
                                                </div>
                                                <div class="col-sm-9">
                                                    <p>Audience</p>
                                                    <h5>0</h5>
                                                </div>
                                                
                                            </div>
                                        </div>
                                    </div>
                                    <div class="col-sm-3">
                                        <div class="stat">
                                            <div class="row">
                                                <div class="col-sm-3">
                                                    <span class="material-symbols-outlined staticon">
                                                        group
                                                    </span>
                                                </div>
                                                <div class="col-sm-9">
                                                    <p>Supporters</p>
                                                    <h5>0</h5>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                    <div class="col-sm-3">
                                        <div class="stat">
                                            <div class="row">
                                                <div class="col-sm-3">
                                                    <span class="material-symbols-outlined staticon">
                                                        contacts
                                                    </span>
                                                </div>
                                                <div class="col-sm-9">
                                                    <p>Connections</p>
                                                    <h5>0</h5>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                            </div>
                        </div>
                    </div>
                
                </div>
                <div class="descriptionBox">
                    <hr>
                    <p class="description">{{ user.description }}</p>
                </div>
                <br>
                <div class="container servicesContainer">
                    <div class="container">
                        <h3>My Accounts</h3>
                        <button class="serviceSelect">
                            <img class="serviceIcon" src="https://i.ibb.co/LRN7Y46/channels4-profile.jpg">
                            <h5>G Guided Productions</h5>
                        </button>
                    </div>
                </div>
                <br>
                <div class="container servicesContainer">
                    <div class="container">
                        <h3>My Posts</h3>
                        <div class="filmList">
                            <div class="col-sm-4">
                                <div class="film">
                                    <img src="https://i.ibb.co/5jJVLrS/2020.jpg">
                                    <h3>2020</h3>
                                    <h6>G Guided Productions</h6>
                                    <p>Director</p>
                                    <button class="filmButton">Watch</button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            
            <div class="col-sm-3">
                <h2 align="center">Related</h2>
            </div>
        </div>
        
    </div>
    
    
  </main>
</template>


<style>
.film{
    width:100%;
    background-color: var(--color-background-mute);
    border-radius:15px;
    padding:15px;
    text-align: center;
}
.filmButton{
    width:100%;
    padding:10px;
    margin-left:0px;
    background-color: var(--color-background-soft);
    color: var(--color-text);
    border-radius: 5px;
    cursor: pointer;
}
.filmButton:hover{
    background-color: var(--color-background);
}
.film img{
    width:100%;
    height:fit-content;
    border-radius:15px;
    object-fit: cover;
}
.serviceIcon{
    border-radius:50%;
    width:50px;
    height:50px;
}
.serviceSelect h5{
    margin:0px;
    font-size:14px;
 }
 .serviceSelect{
    padding:20px;
    width:150px;
    height:150px;
    border-radius:15px;
    background-color: var(--color-background-mute);
    color: var(--color-text);
 }
 .serviceSelect:hover{
    background-color: var(--color-background);
 }
.servicesContainer{
    background: var(--color-background-soft);
    border-radius: 15px;
    padding:25px;
}
.description{
    margin-top:30px;
}
    .descriptionBox{
        margin-top:185px;
    }
 .bannerImage{
    width:100%;
    height: 250px;
    background-color: var(--an-gold);
    border-radius: 14px 14px 0px 0px;
    padding-left:30px;
 }
 .headerProfileImage{
    width:150px;
    height:150px;
    margin-top:180px;
    border-radius:50%;
    object-fit: cover;
    border:5px solid var(--color-background);
 }
 .statistics{
    margin-top:210px;
    height: 70px;
 }
 .stat{
    background-color: var(--color-background-mute);
    border-radius: 15px;
    padding:15px;
    width:90%;
    border:3px solid var(--color-background);
 }
 .staticon{
    background-color: var(--color-border);
    padding:8px;
    border-radius:10px;
    font-size:24px;
 }
 .stat p{
    font-size:12px;
    margin: 0px 0px 3px 0px;
 }
 .stat h5{
    margin:0px;
    font-size:14px;
 }
</style>