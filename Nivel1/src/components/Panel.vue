<template>
    <div>
        <label>Nombre de pàgines </label>
        <input type="text" v-model="numPages" @input="changeNumPages()" required/>
    </div>
    <div>
        <label>Nombre d'idiomes </label>
        <input type="text" v-model="numLanguages" @input="changeNumLanguages()" required/>
    </div>
    <p>{{ numPages }} {{ numLanguages}}</p>
</template>

<script>
export default {
    name: 'Panel',
    emits: ['changeNumPages', 'changeNumLanguages'],
    data() {
        return {
            numPages: '1',
            numLanguages: '1'
        }
    },
    methods: {
        changeNumPages() {
            this.$emit('changeNumPages', this.numPages);
        },
        changeNumLanguages() {
            this.$emit('changeNumLanguages', this.numLanguages);
        }
    }
}
</script>