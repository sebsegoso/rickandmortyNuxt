<template>
<el-menu default-active="2" class="el-menu-vertical-demo" :collapse="isCollapse" background-color="#545c64" text-color="#fff" active-text-color="#ffd04b" style="border: 1px solid #000">
    <el-menu-item index="1" @click="toggleMenu">
        <i class="el-icon-menu"></i>
        <span slot="title">Menú</span>
    </el-menu-item>
    <hr />
    <nuxt-link to="/">
        <el-menu-item index="2">
            <i class="el-icon-house"></i>
            <span slot="title">Inicio</span>
        </el-menu-item>
    </nuxt-link>

    <el-menu-item index="3" disabled>
        <i class="el-icon-setting"></i>
        <span slot="title">Configuración</span>
    </el-menu-item>
</el-menu>
</template>

<style>
.el-menu-vertical-demo {
    min-height: 100%;
}

.el-menu-vertical-demo:not(.el-menu--collapse) {
    width: 200px;
}
</style>

<script>
export default {
    name: "Navbar",
    data() {
        return {
            isCollapse: true,
            hola: "hola",
        };
    },
    methods: {
        toggleMenu() {
            this.isCollapse ? (this.isCollapse = false) : (this.isCollapse = true);
        },
    },
};
</script>
