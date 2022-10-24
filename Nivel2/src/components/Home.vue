<template>
    <b-container fluid id="home">
        <b-row>
            <b-col cols="4">
            <form @submit.prevent="handleSubmit">
            <p class="questions">Què vol fer?</p>

            <div class="options">
                <input type="checkbox" :value="500" v-model="prices" @change="updateTotal" v-b-toggle.collapse-1 class="checkboxes" />
                <label class="labelText">Una pàgina web (500€)</label>
            </div>

            <Panel @changeNumPages="updateNumPages" @changeNumLanguages="updateNumLanguages" />

            <div class="options">
                <input type="checkbox" :value="300" v-model="prices" @change="updateTotal" class="checkboxes" />
                <label class="labelText">Una consultoria SEO (300€)</label>
            </div>

            <div class="options">
                <input type="checkbox" :value="200" v-model="prices" @change="updateTotal" class="checkboxes" />
                <label class="labelText">Una campanya de Google Ads (200€)</label>
            </div>

            <p class="questions">Preu: {{ totalPrice }}€</p>

            <p class="questions">Vol desar el pressupost per a futures consultes, fer-ne un de nou i poder comparar-los i compartir-los fàcilment? Ompli els següents camps!</p>

            <div class="budget-form">
                <label class="label-budget">Nom per al pressupost</label>
                <input type="text" v-model="budgetName" />
            </div>

            <div class="budget-form">
                <label class="label-budget">El seu nom</label>
                <input type="text" v-model="userName" />
            </div>

            <div>
                <b-button type="submit" variant="success">Enviar</b-button>
                <router-link to="/">
                    <b-button type="button" variant="warning">Tornar enrere</b-button>
                </router-link>
            </div>
        </form>
        </b-col>
        
        <b-col cols="6">
            <BudgetList v-if="budgetList.length" :budgetList="budgetList" />
        </b-col>
        </b-row>
    </b-container>
</template>

<script>
    import Panel from "./Panel.vue"
    import BudgetList from "./BudgetList.vue"
    
    export default {
        name: "Home",
        components: {
            Panel,
            BudgetList
        },
        data() {
            return {
                prices: [],
                totalPrice: 0,
                numPages: 1,
                numLanguages: 1,
                userName: "",
                budgetName: "",
                budgetList: []
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
            },
            handleSubmit() {
                this.budgetList.push({
                    budget: this.budgetName,
                    user: this.userName,
                    webpage: this.prices.includes(500),
                    numPages: this.numPages,
                    numLanguages: this.numLanguages,
                    seoconsulting: this.prices.includes(300),
                    adscampaign: this.prices.includes(200),
                    price: this.totalPrice,
                    date: Date.now()
                });
                this.userName = "";
                this.budgetName = "";
            }
        }
    }
</script>

<style>
    #home {
        margin: 2em 0;
    }
    .questions {
        margin-bottom: 1em;
        width: 31vw;
    }
    .labelText {
        margin-bottom: 0;
        margin-right: 0.3em;
    }
    .checkboxes {
        margin-right: 0.3em;
    }
    .options {
        display: flex;
        margin-bottom: 0.3em;
    }
    .budget-form {
        margin-bottom: 1em;
    }
    .label-budget{
        width: 142px;
    }
    .btn-success {
        margin-right: 1em;
    }
</style>