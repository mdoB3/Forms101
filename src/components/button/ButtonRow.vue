<template>
    <div>
        <button @click="onButtonClick" name="Hoodie" value="12" class="ui button">Hoodie</button>
        <button @click="onButtonClick" name="Hat" value="44" class="ui button">Hat</button>
        <button @click="onButtonClick" name="Jacket" value="21" class="ui button">Jacket</button>
        <button @click="onButtonClick" name="Cap" value="40" class="ui button">Cap</button>
    </div>
</template>
<script>
export default {
    name: 'ButtonRow',
    methods: {
        onButtonClick(evt) {
            const button = evt.target;
            console.log(`The user clicked ${button.name}: ${button.value}.`);
        }
    }
}

</script>
<style scoped>

</style>
