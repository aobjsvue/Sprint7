<template>
    <div>
        <label>Nombre de pàgines </label>
        <Buttons @changeQuantity="changeNumPages" />
    </div>
    <div>
        <label>Nombre d'idiomes </label>
        <Buttons @changeQuantity="changeNumLanguages"/>
    </div>
</template>

<script>
    import Buttons from "./Buttons.vue";

    export default {
        name: "Panel",
        emits: ["changeNumPages", "changeNumLanguages"],
        components: { Buttons },
        methods: {
            changeNumPages(updateQuantity) {
                this.$emit("changeNumPages", updateQuantity);
            },
            changeNumLanguages(updateQuantity) {
                this.$emit("changeNumLanguages", updateQuantity);
            }
        }
    }
</script>