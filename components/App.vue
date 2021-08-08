<template>
    <div id="app">
        <AppHeader/>
        <div id="app-body">
            <AppSidebar/>
            <div id="app-content">
            </div>
        </div>
    </div>
</template>

<script>
import AppHeader from '@/components/AppHeader.vue'
import AppSidebar from '@/components/AppSidebar.vue'

export default {
    name: "App",
    components: {
        AppHeader,
        AppSidebar
    }
}
</script>


<style src='@/assets/app_theme.css'></style>
<style scoped>
#app {
    min-width: 100vw;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
}

#app-body {
    flex-grow: 1;
    display: flex;
    flex-direction: row;
}

#app-content {
    flex-grow: 1;
    background-color: black;
}
</style>