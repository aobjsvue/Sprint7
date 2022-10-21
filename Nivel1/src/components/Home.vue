<template>
    <div>
        <p>Què vols fer?</p>
        <form>
            <div>
                <input type="checkbox" :value="500" v-model="prices" @change="updateTotal" />
                <label>Una pàgina web (500€)</label>
            </div>
            <Panel @changeNumPages="updateNumPages($event)" @changeNumLanguages="updateNumLanguages($event)" />
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
    import Panel from './Panel.vue';
    
    export default {
        name: 'Home',
        components: {
            Panel
        },
        data() {
            return {
                prices: [],
                totalPrice: 0,
                numPages: '',
                numLanguages: ''
            }
        },
        methods: {
            updateTotal() {
                this.totalPrice = 0;
                this.prices.forEach((price) => {
                    this.totalPrice += price;
                });
                console.log(this.numPages);
            },
            updateNumPages(updatedNumPages) {
                this.numPages = updatedNumPages;
            },
            updateNumLanguages(updatedNumLanguages) {
                this.numLanguages = updatedNumLanguages;
            }
        }
    }
</script>