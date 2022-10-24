<template>
    <div id="budget">
        <div>
            <b-button type="button" variant="primary" @click="sortAlphabetically">Ordenar alfabèticament</b-button>
            <b-button type="button" variant="info" @click="sortByDate">Ordenar per data</b-button>
            <b-button type="button" variant="warning" @click="resetOrder">Reiniciar ordre</b-button>
        </div>
    
        <b-card v-for="(list, index) in budgetList" :key="index">
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
</template>

<script>
export default {
    name: "BudgetList",
    props: ["budgetList"],
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
</style>