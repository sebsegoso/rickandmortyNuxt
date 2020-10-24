<template>
<el-col :xs="24" :sm="12" :md="8" :lg="6" class="wrapper">
    <nuxt-link :to="'/' + id">
        <el-card shadow="hover" class="card">
            <img :src="imagen" class="image" width="100%" />

            <div class="card__body">
                <h3>{{ id }} - {{ nombre }}</h3>
            </div>
        </el-card>
    </nuxt-link>
</el-col>
</template>

<script>
export default {
    name: "Card",
    props: ["id", "nombre", "imagen"],
    data: () => ({
        show: false,
    }),
};
</script>

<style scoped>
.wrapper {
    padding: 1%;
}

.wrapper a {
    text-decoration: none;
}

.card {
    transition: all .3s;
    min-height: 350px;
}

.card__body {
    width: 100%;
}

.card:hover {
    cursor: pointer;
    box-shadow: 0 0 5px #000, 0 0 15px #ffd04b;
}
</style>
