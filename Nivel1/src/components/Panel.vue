<template>
    <div>
        <b-collapse id="collapse-1" class="">
            <b-card border-variant="dark" class="mt-2 mb-3 py-3">
                <div class="cardContent">
                    <b-card-text class="m-0">Nombre de pàgines</b-card-text>
                    <Buttons @changeQuantity="changeNumPages" />
                </div>
                <div class="cardContent">
                    <b-card-text class="m-0">Nombre de idiomes</b-card-text>
                    <Buttons @changeQuantity="changeNumLanguages"/>
                </div>
            </b-card>
        </b-collapse>
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

<style>
    .card {
        border-width: 2px;
        border-radius: 1em;
    }
    .cardContent {
        display: flex;
        align-items: center;
        justify-content: center;
    }
    .card-text {
        padding-right: 0.5em;
        width: 150px;
    }
</style>