<template>
    <div>
        <p class="question">Què vols fer?</p>
        <b-form>
            <div class="options">
                <input type="checkbox" :value="500" v-model="prices" @change="updateTotal" v-b-toggle.collapse-1 />
                <label class="labelText">Una pàgina web (500€)</label>
            </div>
            <Panel @changeNumPages="updateNumPages" @changeNumLanguages="updateNumLanguages" />
            <div class="options">
                <input type="checkbox" :value="300" v-model="prices" @change="updateTotal" />
                <label class="labelText">Una consultoria SEO (300€)</label>
            </div>
            <div class="options">
                <input type="checkbox" :value="200" v-model="prices" @change="updateTotal" />
                <label class="labelText">Una campanya de Google Ads (200€)</label>
            </div>
            <p class="options">Preu: {{ totalPrice }}€</p>
        </b-form>
    </div>
</template>

<script>
    import Panel from "./Panel.vue";
    
    export default {
        name: "Home",
        components: {
            Panel
        },
        data() {
            return {
                prices: [],
                totalPrice: 0,
                numPages: 1,
                numLanguages: 1
            }
        },
        methods: {
            updateTotal() {
                this.totalPrice = 0;
                this.prices.forEach((price) => {
                    this.totalPrice += price;
                });
                if (this.prices.includes(500)) {
                    this.totalPrice += this.numPages * this.numLanguages * 30;
                }
            },
            updateNumPages(updatedNumPages) {
                this.numPages = updatedNumPages;
                this.updateTotal();
            },
            updateNumLanguages(updatedNumLanguages) {
                this.numLanguages = updatedNumLanguages;
                this.updateTotal();
            }
        }
    }
</script>

<style>
    .labelText {
        padding-left: 0.5em;
        margin: 0;
    }
    .options {
        display: flex;
        width: 289px;
        margin: 0.3em 0;
    }
    form {
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    .question {
        margin-top: 2em;
    }
</style>