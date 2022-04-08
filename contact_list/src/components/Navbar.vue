<template>
    <div class="nav">
    <router-link class = "router" to="/">Home</router-link><br>
    <router-link class = "router" to="/register">Register Contact</router-link>
  </div>
</template>

<script>
export default {
    name: 'Navbar'
}
</script>

<style>
.nav {
    margin-left: 100px;
    background-color: #ffffff;
    height: 150px;
    width: 400px;
    border-radius: 6px;
    box-shadow: 1px 1px;
    padding: 22px;

}

.router {
    font-size: 50px
}

</style>