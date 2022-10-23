<template>
    <div class="buttonsInput">
        <b-button type="button" @click="increase"><b-icon icon="plus"></b-icon></b-button>
        <b-form-input type="text" v-model="quantity" size="sm" class="inputStyles" />
        <b-button type="button" @click="decrease"><b-icon icon="dash"></b-icon></b-button>
    </div>
</template>

<script>
    export default {
        name: "Buttons",
        emits: ["changeQuantity"],
        data() {
            return {
                quantity: 1
            };
        },
        methods: {
            increase() {
                this.quantity >= 1 ? this.quantity++ : this.quantity = 1;
                this.changeQuantity();
            },
            decrease() {
                this.quantity > 1 ? this.quantity-- : this.quantity = 1;
                this.changeQuantity();
            },
            changeQuantity() {
                this.$emit("changeQuantity", this.quantity);
            }
        }
    }
</script>

<style>
    .inputStyles {
        width: 3em;
        border-color: transparent;
        text-align: center;
    }
    .inputStyles:focus {
        border-color: black;
        border-width: 2px;
        box-shadow: none;
    }
    .btn-secondary, .btn-secondary:hover, .btn-secondary:focus {
        background-color:#f67754;
        border-color: transparent;
        box-shadow: none;
        padding: 0.2em 0.3em 0 0.3em;
        margin-top: 0;
        margin-right: 0.3em;
    }
    .buttonsInput {
        display: flex;
        align-items: center;
    }
</style>