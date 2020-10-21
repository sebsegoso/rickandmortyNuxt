<template>
<el-container v-loading="loading">
    <el-row align="middle">
        <el-col :span="12">
            <button @click="prevPage" :disabled="pagina == 1">Anterior</button>
        </el-col>

        <el-col :span="12">
            <button @click="nextPage" :disabled="pagina == 34">Siguiente</button>
        </el-col>

        <Card v-for="personaje in personajes" :key="personaje.id" :id="personaje.id" :nombre="personaje.name" :imagen="personaje.image" />
    </el-row>
</el-container>
</template>

<script>
import Card from "../components/Card";
export default {
    components: {
        Card,
    },
    data() {
        return {
            personajes: [],
            pagina: 1,
            loading: false,
        };
    },
    created() {
        this.llamadoApi();
    },
    methods: {
        llamadoApi() {
            this.loading = true;
            fetch(this.url)
                .then((res) => res.json())
                .then((data) => (this.personajes = data.results));

            this.loading = false;
        },
        nextPage() {
            this.pagina++;
            this.llamadoApi();
        },
        prevPage() {
            this.pagina--;
            this.llamadoApi();
        },
    },
    computed: {
        url() {
            return `https://rickandmortyapi.com/api/character?page=${this.pagina}`;
        },
    },
};
</script>

<style>
</style>
