<template>
    <div>
        <button type="button" @click="increase">+</button>
        <input type="text" v-model="quantity" />
        <button type="button" @click="decrease">-</button>
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