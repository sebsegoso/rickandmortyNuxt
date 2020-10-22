<template>
<el-container>
    <transition name="el-fade-in">
        <Loading v-if="loading" />
        <el-row v-else align="middle">

            <el-pagination class="pag" layout="prev, pager, next" :total="totalPaginas" @prev-click="prevPage" @next-click="nextPage" :current-page="pagina" @current-change="clickPagina">
            </el-pagination>

            <Card v-for="personaje in personajes" :key="personaje.id" :id="personaje.id" :nombre="personaje.name" :imagen="personaje.image" />
        </el-row>
    </transition>
</el-container>
</template>

<script>
export default {
    data() {
        return {
            personajes: [],
            pagina: 1,
            loading: true,
            totalPaginas: ''
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
                .then((data) => {
                    this.personajes = data.results
                    this.totalPaginas = (data.info.pages) * 10
                })
                .then(() => (this.loading = false));
        },
        nextPage() {
            this.pagina++;
            this.llamadoApi();
        },
        prevPage() {
            this.pagina--;
            this.llamadoApi();
        },
        clickPagina(pag) {
            this.pagina = pag
            this.llamadoApi()
        }
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
