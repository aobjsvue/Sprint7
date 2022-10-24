<template>
    <div id="budget">
        <b-card v-for="(list, index) in budgetList" :key="index">
            <p>Nom del projecte: {{ list.project }}</p>
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
    props: ["budgetList"]
}
</script>

<style scoped>
    .card {
        border-width: 1.5px;
        border-radius: 1em;
        border-color: black;
        margin-bottom: 0.3em;
    }.card-body {
        padding: 1em;
    }
    p {
        margin-bottom: 0.3em;
    }
    ul {
        margin-bottom: 0.3em;
    }
</style>