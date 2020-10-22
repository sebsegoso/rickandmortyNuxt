<template>
<div class="loading-wrapper">
    <div class="loader"></div>
</div>
</template>

<script>
name: 'Loading'
export default {

}
</script>

<style>
.loading-wrapper {
    width: 100vw;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
}

.loader {
    border: 5px solid #f3f3f3;
    /* Light grey */
    border-top: 5px solid #495057;
    /* Blue */
    border-radius: 50%;
    width: 60px;
    height: 60px;
    animation: spin 2s linear infinite;
}

@keyframes spin {
    0% {
        transform: rotate(0deg);
    }

    100% {
        transform: rotate(360deg);
    }
}
</style>
