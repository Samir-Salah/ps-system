<template>
    <div id="app">
        <Header />
        <SideBar />
        <router-view />
    </div>
</template>

<script>
import Header from "@/components/Header.vue";
import SideBar from "@/components/SideBar.vue";

export default {
    name: "App",
    components: {
        Header,
        SideBar
    }
};
</script>
