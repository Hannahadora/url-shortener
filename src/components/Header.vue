<template>
    <div class="header px-24 py-7">
        <div class="grid grid-cols-5">
            <div class="">
                <img alt="logo" src="../assets/images/logo.svg" />
            </div>

            <div class="navbar col-span-4 flex items-center justify-between">
                <ul class="flex items-center gap-5">
                   <li><a href="">Features</a></li>
                   <li><a href="">Pricing</a></li>
                   <li><a href="">Resources</a></li>
                </ul>

                <ul class="flex items-center gap-5">
                    <li>Login</li>
                    <Button text="Sign Up" theme="primary"/>
                </ul>
            </div>
        </div>
    </div>
</template>



<script>
import Button from './Button.vue'

export default {
    components: {
       Button
    },

    data() {
        return {
            
        }
    }
}
</script>

<style scoped>

    li {
        color: hsl(257, 27%, 26%);
        font-weight: 500;
        cursor: pointer;
    }

</style>