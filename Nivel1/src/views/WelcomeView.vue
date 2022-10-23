<template>
    <div>
        <Welcome />
        <router-link to="/home">
            <button type="button">A la calculadora!</button>
        </router-link>
    </div>
</template>

<script>
import Welcome from "@/components/Welcome.vue"

export default {
    name: "WelcomeView",
    components: {
        Welcome
    }
}
</script>