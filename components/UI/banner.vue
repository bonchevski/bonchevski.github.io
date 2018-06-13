<template>
    <div class="container-fluid">
        <div class="wrapper d-none d-md-block hidden-sm col-md-12"  :style="{ backgroundImage: `url(${backgroundUrl})` }">
            <h1 class="greeting align-items-center">{{ postTitle }}</h1>
        </div>

        <h1 class="greeting-mobile d-md-none hidden-md col-8 offset-2">{{ postTitle }}</h1>
    </div>
</template>

<script>
    import backgroundUrl from "@/static/images/dubai.png"

    export default {
        name: "banner",
        data() {
            return { backgroundUrl };
        },
        props: {
            postTitle: {
                type: String,
                default: "Welcome"
            }
        }
    }
</script>

<style scoped>
    .container-fluid {

        width: 100%;
        padding: 0;

    }

   .wrapper {
       width: 100vw;
       height: 230px;
       padding: 0;
       background-repeat: no-repeat;
   }

    .greeting {
        color: white;
        text-align: left;
        padding-left: 30px;
        padding-top: 10vh;
    }

    .greeting-mobile {
        margin-top: 5%;
        text-align: center;
    }
</style>