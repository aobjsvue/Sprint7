<template>
    <div id="welcome">
        <h3 class="salute">Benvingut/da!</h3>
        <h6 class="description">En aquesta pàgina web podreu calcular i rebre al moment un pressupost per a la creació de la vostra pròpia pàgina web, una consultoria SEO, una campanya de Google Ads, entre altres serveis. Endavant, feu clic al botó per començar!</h6>
        <router-link to="/home">
            <b-button type="button" variant="success">A la calculadora!</b-button>
        </router-link>
    </div>
</template>

<style>
    #welcome {
        display: flex;
        flex-direction: column;
        align-items: center;
        text-align: center;
        margin: 2em 0;
    }
    .salute {
        margin: 0;
    }
    .description {
        width: 70vw;
        margin: 2em 0;
    }
    @media (min-width: 1025px) {
        .description {
            width: 40vw;
        }
    }
</style>