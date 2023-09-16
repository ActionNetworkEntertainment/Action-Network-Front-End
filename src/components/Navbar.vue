
<script setup>
defineProps({
  user: {
    type: Object,
    required: true
  }
})

$(document).ready(function () {
  // Check if the viewport width is less than or equal to a specific value (e.g., 768px for typical mobile devices)
  if ($(window).width() <= 768) {
    $(".menu-toggle").click(function () {
      $(".menu").slideToggle();
    });
  }
});
</script>

<template>
  <header class="flex-container responsive-margin responsive padding">
  <div class="left-side">
    <a href="#" class="logo"><img src="../assets/images/ANLogoCircleFlatGradient.png" ></a>
    <a href="#" class="button">Films</a>
    <a href="#" class="button">Discover</a>
    <a href="#" class="button">My Library</a>
  </div>
  <div class="center-side">
    <input type="text" class="searchBox" id="search" placeholder="Search">
  </div>
  <div class="right-side">
    <button class="smallButton"><i class="fa-solid fa-bell"></i></button>
    <button class="smallButton"><i class="fa-solid fa-message"></i></button>
    <button class="largeButton">
      <div class="row">
        <div class="col-2">
          <img :src="user.profileImageURL" alt="User Profile">
        </div>
        <div class="col-10">
          <h5>{{user.fullName}}</h5>
        </div>
      </div>
    </button>
  </div>
  <button class="menu-toggle mobile-only"><i class="fa-solid fa-bars"></i></button>
</header>
</template>

<style>
/* mini.css utility classes */
.flex-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
}

.left-side {
  display: flex;
  align-items: center;
  gap: 10px;
}

.menu {
  display: none;
  flex-direction: column;
  gap: 10px;
}

.center-side {
  flex: 1;
  text-align: center;
}

.right-side {
  display: flex;
  gap: 10px;
  align-items: center;
}

/* Header styling */
header {
  display: flex;
  align-items: center;
  padding: 10px 20px; /* Add padding to the header */
}

/* Logo and buttons styling */
.logo img {
  width: 50px; /* Adjust the image size as needed */
  height: auto;
}
.largeButton{
    width: fit-content;
    height:40px;
    background-color: var(--color-background-mute);
  border: 1px solid var(--color-background-soft);
  border-radius: 50px;
  display: flex;
  justify-content: center;
  align-items: center; /* Center align vertically */
  padding: 10px 40px 10px 10px; /* Add padding for spacing */
  text-transform: capitalize;
  margin-left: auto;
}
.largeButton h5{
    font-weight: 400;
    color: var(--color-heading);
    border-radius:50%;
}
.largeButton img{
    margin-top: 6px;
    border-radius: 50%;
    height: 30px;
    object-fit: cover;
    width: 30px;
    padding:1px;
    border:1px solid var(--an-gold)
}

.button {
  text-decoration: none;
  color: #333; /* Adjust the color as needed */
  margin-right: 15px; /* Add some spacing between buttons */
}

.searchBox {
  padding: 5px 20px; /* Add padding to the search box */
  width:300px;
  border: 1px solid var(--color-background-mute);
  background-color: var(--color-background-soft);
  border-radius: 50px;
  color:var(--color-text);
  margin: 0px 150px; /* Add spacing between search box and button */
}

.smallButton {
  background-color: var(--color-background-mute);
  border: 1px solid var(--color-background-soft);
  height:40px;
  width:40px;
  padding: 0px;
  color: var(--color-text);
  border-radius: 50%;
  cursor: pointer;
  margin: 0 10px;
}
.smallButton:hover, .largeButton:hover{
    background-color: var(--color-background-soft);
}
/* Display the toggle button only on mobile screens */
.mobile-only {
  display: none;
}

/* Media query for mobile devices */
@media screen and (max-width: 1250px) {
  .mobile-only {
    display: block; /* Display the toggle button on mobile screens */
  }
  .flex-container {
    padding: 5px; /* Adjust the padding for smaller screens */
  }

  .left-side,
  .right-side {
    gap: 5px; /* Adjust the gap between elements for smaller screens */
  }

  .menu,
  .searchBox,
  .smallButton,
  .largeButton {
    margin: 5px; /* Adjust margins for smaller screens */
  }
}
@media screen and (max-width: 950px) {

  .right-side{
    display: none;
  }
}

@media screen and (max-width: 768px) {
  .center-side{
    display: none;
  }
}
@media screen and (max-width: 450px) {
  
}
</style>