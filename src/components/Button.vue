<template>
    <button class="text-white" :class="{ primary: theme === 'primary' }"> {{ text }} </button>
</template>

<script>
export default {
    props: [ 'text', 'theme']
}
</script>

<style>
    button {
        background-color:  hsl(180, 66%, 49%);
        color: #fff;
        padding: 10px 30px;
    }

    button :focus {
        outline: 2px solid transparent;
    }

    button.primary {
        border-radius: 20px;
    }

</style>