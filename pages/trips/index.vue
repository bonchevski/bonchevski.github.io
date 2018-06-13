<template>
    <div>
        <div class="container-fluid">
            <div class="trips-banner d-none d-md-block hidden-sm col-md-12">
                <h1 class="greeting align-items-center">Trips</h1>
            </div>

            <h1 class="greeting-mobile d-md-none hidden-md col-8 offset-2">Trips</h1>
        </div>

        <section>
            <TripsList isAdmin
                        :posts="loadedPosts"/>
        </section>
    </div>
</template>

<script>
    import TripsList from "@/components/posts/TripsList"

    export default {
        head() {
            return {
                title: 'Trip with StyleTravel',
                 meta: [{ hid: 'description', name: 'description', content: 'About our company Nuxt.js ' }]
            }
        },
        name: "Trips",
        components: {
            TripsList
        },
        computed: {
            loadedPosts() {
                return this.$store.getters.loadedPosts;
            }
        },
    }
</script>

<style scoped>

    .container-fluid {

        width: 100%;
        padding: 0;

    }

    .trips-banner {
        width: 100vw;
        height: 230px;
        padding: 0;
        /*background-repeat: no-repeat;*/
        background-image: url("~/static/images/tripsBanner.jpg");
    }

    .greeting {
        color: white;
        text-align: left !important;
        padding-left: 30px;
        padding-top: 9vh;
        border: none;
    }

    .greeting-mobile {
        margin-top: 5%;
        text-align: center;
    }


</style>