<template>
    <div id="footer" class="w-full py-20 px-24">
        <div class="flex items-start justify-between">
            <div class="">
                <img alt="logo" src="../assets/images/logo.svg" />
            </div>

            <div class="flex items-start gap-20">
                <div class="flex flex-col gap-5">
                    <h1>Features</h1>
                    <ul>
                        <li><a href="">Link Shortening</a></li>
                        <li><a href="">Branded Links</a></li>
                        <li><a href="">Analytics</a></li>
                    </ul>
                </div>    
                <div class="flex flex-col gap-5">
                    <h1>Resources</h1>
                    <ul>
                        <li><a href="">Blog</a></li>
                        <li><a href="">Developers</a></li>
                        <li><a href="">Support</a></li>
                    </ul>
                </div>    
                <div class="flex flex-col gap-5">
                    <h1>Company</h1>
                    <ul>
                        <li><a href="">About</a></li>
                        <li><a href="">Our Team</a></li>
                        <li><a href="">Careers</a></li>
                        <li><a href="">Support</a></li>
                    </ul>
                </div>    
            </div>

            <div class="icons flex  items-start gap-10">
                <img src="src\assets\images\icon-facebook.svg" alt="" />
                <img src="src\assets\images\icon-twitter.svg" alt="" />
                <img src="src\assets\images\icon-pinterest.svg" alt="" />
                <img src="src\assets\images\icon-instagram.svg" alt="" />
            </div>
        </div>
    </div>
</template>

<style scoped>
    #footer {
        background-color: hsl(260, 8%, 14%);
    }

    h1 {
        color: #fff;
    }

    li {
        color: hsl(0, 0%, 75%);
        margin-bottom: 10px;
    }
</style>