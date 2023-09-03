<script setup>
import { RouterLink, RouterView } from 'vue-router'

</script>

<template>
  <header>
    <h1>ShopFruit</h1>
    <div class="wrapper">
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/product">Products</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header>

  <br>

  <RouterView />
</template>

<style>
  @import './assets/main.css'
</style>
