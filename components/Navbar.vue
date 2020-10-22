<template>
<el-menu default-active="2" class="el-menu-vertical-demo" :collapse="isCollapse" background-color="#545c64" text-color="#fff" active-text-color="#ffd04b" style="border: 1px solid #000">
    <el-menu-item index="1" @click="toggleMenu">
        <i v-if="isCollapse" class="el-icon-caret-right"></i>
        <i v-else class="el-icon-caret-left"></i>
        <span slot="title">{{menuTitle}}</span>
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
        };
    },
    methods: {
        toggleMenu() {
            this.isCollapse ? (this.isCollapse = false) : (this.isCollapse = true);
        }
    },
    computed: {
        menuTitle() {
            if (this.isCollapse) {
                return "Abrir menú"
            } else {
                return "Cerrar menú"
            }
        }
    }
};
</script>
