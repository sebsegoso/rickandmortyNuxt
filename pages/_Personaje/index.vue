<template>
<div class="personaje-wrapper" v-loading="loading" element-loading-text="Cargando..." element-loading-spinner="el-icon-loading" element-loading-background="#495057">
    <transition name="el-fade-in">
        <div class="personaje__data">
            <img :src="data.image" alt="character image" class="personaje__data__img" />
            <div class="personaje__data__info">
                <h1>{{ data.id }} - {{ data.name }}</h1>
                <hr />
                <p>Species: {{ data.species }}</p>
                <p>Gender: {{ data.gender }}</p>
                <p>Origin: {{ data.origin.name }}</p>
                <p>Status: {{ data.status}}</p>
            </div>
        </div>
    </transition>
</div>
</template>

<script>
export default {
    name: "Card",
    data() {
        return {
            loading: true,
            data: {
                id: "",
                name: "",
                species: "",
                gender: "",
                origin: {
                    name: "",
                },
            },
        };
    },
    created() {
        this.llamadoApi();
    },
    methods: {
        llamadoApi() {
            this.loading = true;
            fetch(this.urlPersonaje)
                .then((res) => res.json())
                .then((data) => (this.data = data))
                .then(() => (this.loading = false));
        },
    },
    computed: {
        urlPersonaje() {
            return `https://rickandmortyapi.com/api/character/${this.$route.params.Personaje}`;
        },
    },
    head() {
        return {
            title: `${this.data.name} | Rick & Morty personajes`,
        };
    },
};
</script>

<style>
.personaje-wrapper {
    width: 100%;
    min-height: 100vh;
    padding: 3rem;
}

.personaje__data {
    border: 2px solid whitesmoke;
    width: 100%;
    padding: 1rem;
    display: flex;
}

.personaje__data__info {
    padding: 0 3rem;
    font-size: 1.5rem;
}
</style>
