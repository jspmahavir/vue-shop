<template>
    <div id="app">
        <navbar/>
        <div class="container">
            <router-view></router-view>
        </div>
    </div>
</template>

<script>
import Navbar from '@/components/Navbar'
export default {
    name: 'app',
    components: {
        Navbar
    }
}
</script>

<style>
  * {
    font-family: 'Poppins';

  }
body {
    background-color: #F5F3ef;
}

</style>