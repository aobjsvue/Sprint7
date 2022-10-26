<template>
    <b-container fluid id="home">
        <b-row>
            <b-col cols="12" md="5">
                <form ref="form" @submit.prevent="handleSubmit">
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
                        <b-form-input type="text" size="sm" v-model="budgetName" />
                    </div>

                    <div class="budget-form">
                        <label class="label-budget">El seu nom</label>
                        <b-form-input type="text" size="sm" v-model="userName" />
                    </div>

                    <div>
                        <b-button type="submit" variant="success" size="sm">Enviar</b-button>
                        <router-link to="/">
                            <b-button type="button" variant="warning" size="sm">Tornar enrere</b-button>
                        </router-link>
                    </div>
                </form>
            </b-col>
            
            <b-col cols="12" md="7" lg="6">
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
        display: flex;
        align-items: center;
        margin-bottom: 1em;
    }
    .form-control {
        margin-left: 0.3em;
        width: auto;
        
        border-color: black;
    }
    .form-control:focus {
        border-color: black;
        border-width: 2px;
        box-shadow: none;
    }
    .label-budget{
        width: 142px;
        margin-bottom: 0;
    }
    .btn-success {
        margin-right: 1em;
    }
    @media (min-width: 390px) and (max-width: 786px) {
        .row {
            flex-direction: column;
        }
        .questions {
            width: 325px;
        }
    }
    @media (min-width: 280px) and (max-width: 389px) {
        .row {
            flex-direction: column;
        }
        .questions {
            width: 100%;
        }
    }
</style>