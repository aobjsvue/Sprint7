<template>
    <div>
        <p>Què vols fer?</p>
        <form>
            <div>
                <input type="checkbox" :value="500" v-model="prices" @change="updateTotal" />
                <label>Una pàgina web (500€)</label>
            </div>
            <div>
                <input type="checkbox" :value="300" v-model="prices" @change="updateTotal" />
                <label>Una consultoria SEO (300€)</label>
            </div>
            <div>
                <input type="checkbox" :value="200" v-model="prices" @change="updateTotal" />
                <label>Una campanya de Google Ads (200€)</label>
            </div>
        </form>
        <p>Preu: {{ totalInitial }}€</p>
    </div>
</template>

<script>
    export default {
        name: 'Home',
        data() {
            return {
                prices: [],
                totalInitial: 0
            }
        },
        methods: {
            updateTotal() {
                this.totalInitial = 0;
                this.prices.forEach((price) => {
                    this.totalInitial += price;
                });
                console.log(this.prices)
            }
        }
    }
</script>