<script setup>
    import { RouterLink } from 'vue-router'
</script>

<template>
    <div class="heading">
            <RouterLink to="/">
                <img class="heading__logo" src="../assets/logo.png" alt="Math quiz app logo">
            </RouterLink>    
            <RouterLink to="/" class="heading__link">Math quiz</RouterLink> 
    </div>
    
</template>

<style>
    .heading {
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: center;
        column-gap: 2em;
    }
    .heading__link {
        color: #032704;
        font-size: 2em;
        font-weight: 800;
        text-decoration: none;
    }
</style>