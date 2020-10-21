<template>
<div class="personaje-wrapper">
    <div class="personaje-data">
        <img :src="data.image" alt="" />
        <h1>{{ data.id }} - {{ data.name }}</h1>
        <hr />
        <p>Species: {{ data.species }}</p>
        <p>Gender: {{ data.gender }}</p>
        <p>Origin: {{data.origin.name}}</p>
    </div>
</div>
</template>

<script>
export default {
    name: "Card",
    data() {
        return {
            data: {
                id: '',
                name: '',
                species: '',
                gender: '',
                origin: {
                    name: ''
                }
            },
        };
    },
    created() {
        this.llamadoApi();
    },
    methods: {
        llamadoApi() {
            fetch(this.urlPersonaje)
                .then((res) => res.json())
                .then((data) => (this.data = data));
        },
    },
    computed: {
        urlPersonaje() {
            return `https://rickandmortyapi.com/api/character/${this.$route.params.Personaje}`;
        },
    },
    head() {
        return {
            title: `${this.data.name} | Rick & Morty personajes`
        }
    }
};
</script>

<style>
.personaje-wrapper {
    min-height: 100vh;
    padding: 3rem;
}

.personaje-data {
    border: 2px solid whitesmoke;
    width: 100%;
    padding: 1rem;
}
</style>
