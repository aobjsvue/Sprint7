<template>
    <div>
        <b-collapse id="collapse-1" class="">
            <b-card border-variant="dark" class="mt-2 mb-3 py-3">
                <div class="cardContent">
                    <b-card-text class="m-0">Nombre de pàgines</b-card-text>
                    <Buttons @changeQuantity="changeNumPages" />
                    <b-icon icon="info" v-b-modal.helpPages></b-icon>
                    <b-modal id="helpPages" centered hide-header hide-footer no-fade>
                        <p class="helpText">En aquest component ha d'indicar el nombre de pàgines que tindrà el seu lloc web.</p>
                    </b-modal>
                </div>
                <div class="cardContent">
                    <b-card-text class="m-0">Nombre de idiomes</b-card-text>
                    <Buttons @changeQuantity="changeNumLanguages"/>
                    <b-icon icon="info" v-b-modal.helpLanguages></b-icon>
                    <b-modal id="helpLanguages" centered hide-header hide-footer no-fade>
                        <p class="helpText">En aquest component ha d'indicar el nombre d'idiomes que tindrà el seu lloc web.</p>
                    </b-modal>
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
    .bi-info {
        cursor: pointer;
        color: white;
        background-color: #b0b0ae;
        border-radius: 1em;
    }
    .bi-info:focus {
        outline: none;
    }
    .modal-content {
        border-radius: 2em;
        border-width: 2px;
        border-color: black;
    }
    .modal-body {
        display: flex;
        justify-content: center;
        padding: 2em;
    }
    .modal-dialog {
        max-width: 660px;
    }
    .helpText {
        margin: 0;
    }
</style>