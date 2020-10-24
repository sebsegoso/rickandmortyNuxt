<template>
<el-container v-loading="loading" element-loading-text="Cargando..." element-loading-spinner="el-icon-loading" element-loading-background="#495057">
    <transition name="el-fade-in">
        <el-row align="middle">
            <el-pagination class="pag" :hide-on-single-page="true" layout="prev, pager, next" :total="totalPaginas" @prev-click="prevPage" @next-click="nextPage" :current-page="pagina" @current-change="clickPagina">
            </el-pagination>
            <Card class="card__character" v-for="personaje in personajes" :key="personaje.id" :id="personaje.id" :nombre="personaje.name" :imagen="personaje.image" />
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
            totalPaginas: 0,
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
                    this.personajes = data.results;
                    this.totalPaginas = data.info.pages * 10;
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
            this.pagina = pag;
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
