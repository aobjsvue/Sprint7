<template>
    <div id="budget">
        <div>
            <b-button type="button" variant="primary" @click="sortAlphabetically">Ordenar alfabèticament</b-button>
            <b-button type="button" variant="info" @click="sortByDate">Ordenar per data</b-button>
            <b-button type="button" variant="warning" @click="resetOrder">Reiniciar ordre</b-button>
        </div>

        <div id="search-bar">
            <b-icon icon="search"></b-icon>
            <b-form-input type="search" size="sm" placeholder="Nom del pressupost" v-model="search"></b-form-input>
        </div>

        <div v-if="searchBudget.length">
            <b-card v-for="(list, index) in searchBudget" :key="index">
                <p>Nom del pressupost: {{ list.budget }}</p>
                <p>El seu nom: {{ list.user }}</p>
                <p>Serveis seleccionats:</p>
                    <ul>
                        <li v-if="list.webpage">Una pàgina web amb {{ list.numPages }} nombre(s) de pàgines i {{ list.numLanguages }} nombre(s) de idiomes</li>
                        <li v-if="list.seoconsulting">Una consultoria SEO</li>
                        <li v-if="list.adscampaign">Una campanya de Google Ads</li>
                    </ul>
                <p>Preu total: {{ list.price }}€</p>
            </b-card>
        </div>
        <div v-else>No s'han trobat pressupostos amb aquest nom: {{ search }}</div>
    </div>
</template>

<script>
export default {
    name: "BudgetList",
    props: ["budgetList"],
    data() {
        return {
            search: ""
        }
    },
    methods: {
        sortAlphabetically() {
            this.budgetList.sort((a, b) => {
                if (a.budget < b.budget) {
                    return -1;
                }
                if (a.budget > b.budget) {
                    return 1;
                }
                return 0;
            });
        },
        sortByDate() {
            this.budgetList.sort((a, b) => {
                if (a.date < b.date) {
                    return -1;
                }
                if (a.date > b.date) {
                    return 1;
                }
                return 0;
            });
        },
        resetOrder() {
            this.sortByDate();
        }
    },
    computed: {
        searchBudget() {
            if (this.search.length >0) {
                return this.budgetList.filter((list) => list.budget.toLowerCase().includes(this.search.toLowerCase()));
            }
            return this.budgetList;
        }
    }
}
</script>

<style scoped>
    .card {
        border-width: 1.5px;
        border-radius: 1em;
        border-color: black;
        margin: 0.3em 0;
    }.card-body {
        padding: 1em;
    }
    p {
        margin-bottom: 0.3em;
    }
    ul {
        margin-bottom: 0.3em;
    }
    .btn-info {
        margin: 0 0.3em;
    }
    #search-bar {
        display: flex;
        align-items: center;
        margin-top: 0.3em;
    }
</style>