<template>
    <div>
        <p>Què vols fer?</p>
        <form>
            <div>
                <input type="checkbox" :value="500" v-model="prices" @change="updateTotal" />
                <label>Una pàgina web (500€)</label>
            </div>
            <Panel @changeNumPages="updateNumPages" @changeNumLanguages="updateNumLanguages" />
            <div>
                <input type="checkbox" :value="300" v-model="prices" @change="updateTotal" />
                <label>Una consultoria SEO (300€)</label>
            </div>
            <div>
                <input type="checkbox" :value="200" v-model="prices" @change="updateTotal" />
                <label>Una campanya de Google Ads (200€)</label>
            </div>
        </form>
        <p>Preu: {{ totalPrice }}€</p>
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