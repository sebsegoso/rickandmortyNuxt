<template>
<el-container>
    <Loading v-if="loading" />
    <el-row v-else align="middle">
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
import Loading from "../components/Loading";
export default {
    components: {
        Card,
        Loading
    },
    data() {
        return {
            personajes: [],
            pagina: 1,
            loading: true,
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
                .then((data) => (this.personajes = data.results))
                .then(() => this.loading = false);
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
