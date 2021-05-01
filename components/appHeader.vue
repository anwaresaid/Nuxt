<template>
<!-- header component to be displayed on all pages it has the navigation bar  -->
    <div class="header">
        <h1 class="title"> Tickers Bar Chart</h1>
        <ul>
            <li>
                <nuxt-link to="/">
                    Home
                </nuxt-link>
            </li>
            <li>
                <nuxt-link to="/about">
                    about
                </nuxt-link>
            </li>
            <li>
                <nuxt-link to="/api">
                    api
                </nuxt-link>
            </li>
        </ul>
    </div>
  
</template>

<script>
export default {
    name: 'appHeader',

}
</script>

<style>
    .header {
        display: flex;
        justify-content:space-between;
        align-items:center;
        margin-bottom: 1rem;
        padding-bottom: 1rem;
        border-bottom: 1px dotted #ccc;
        }

    .header .title{
        font-size:3rem;
        color: #526488;
    }
    .header ul{
        display: flex;
    }
    .header a{
        display:inline-block;
        background-color: #333;
        color:#ccc;
        padding: 0.3rem 1rem;
        margin-right: 0.5rem;
    }
</style>