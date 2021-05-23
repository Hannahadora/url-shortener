<template>
    <div class="header lg:px-24 md:px-12 px-5 py-7">
        <div class="grid grid-cols-5">
            <div class="">
                <img alt="logo" src="../assets/images/logo.svg" />
            </div>

            <div class="navbar col-span-4 md:flex hidden items-center justify-between">
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

            <div  @click.prevent="toggleNav" class="md:hidden absolute right-7">
                <i v-if="!showNav" class="fas fa-bars"></i>
                <i v-if="showNav" class="fas fa-times"></i>
            </div>
        </div>


<!-- Mobile Screen -->
        <div v-if="showNav" class="sidenavbar md:hidden w-10/12 h-80 rounded-3xl absolute top-20 p-10 z-50" style="background-color: hsl(257, 27%, 26%);">
            <div class="flex flex-col items-center gap-5">
                <h6><a href="">Features</a></h6>
                <h6><a href="">Pricing</a></h6>
                <h6><a href="">Resources</a></h6>
            </div>

            <div class="my-5 py-5 border-t border-gray-500 flex flex-col items-center gap-5">
                <h6>Login</h6>
                <Button class="w-full" text="Sign Up" theme="primary"/>
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
     showNav: false       
        }
    },

    methods: {
        toggleNav() {
        this.showNav = !this.showNav
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

    h6 {
        color: white;
        font-size: 18px;
    }
</style>