<template>
<el-col :xs="12" :sm="8" :lg="6" class="wrapper">
    <nuxt-link :to="'/' + id">
        <el-card shadow="hover" class="card">
            <img :src="imagen" class="image" width="100%" />
            <div style="padding: 14px">
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

<style>
.wrapper {
    padding: 20px;
}

.wrapper a {
    text-decoration: none;
}

.card {
    min-height: 315px;
}

.card:hover {
    cursor: pointer;
}
</style>
