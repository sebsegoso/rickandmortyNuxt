<template>
<div class="error-wrapper">
    <div class="error-info">
        <h1>La página que buscas no existe :(</h1>
        <nuxt-link to="/">Visita la página de inicio</nuxt-link>
    </div>
</div>
</template>

<script>
export default {
    props: ["error"],
    layout: "blog", // you can set a custom layout for the error page
};
</script>

<style>
a,
a:active,
a:focus {
    text-decoration: none;
}

.error-wrapper {
    min-height: 100vh;
    padding: 3rem;
}

.error-info {
    border: 2px solid whitesmoke;
    width: 100%;
    padding: 1rem;
}
</style>
