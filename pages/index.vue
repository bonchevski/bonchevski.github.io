<template>
    <main>
        <banner  :background-url="require('~/static/images/dubai.png')" post-title="Welcome to StyleTravel" />
        <div class="locations">
            <h1 class="section-title"> Top locations </h1>
            <top-posts-list isAdmin
                            :posts="loadedPosts" />
        </div>


        <div class="container-fluid">
            <div class="offers-banner d-none d-md-block hidden-sm col-md-12">
                <h1 class="greeting align-items-center"></h1>
            </div>

            <h1 class="greeting-mobile d-md-none hidden-md col-8 offset-2">Hot offers</h1>
        </div>


        <section class="offers">
            <h1 class="section-title">Hot offers</h1>
            <HotOfferList
                    isAdmin
                    :posts="loadedPosts" />
        </section>


    </main>

</template>


<script>

    import 'bootstrap/dist/css/bootstrap.css'
    import 'bootstrap-vue/dist/bootstrap-vue.css'
    import Banner from "@/components/UI/banner"
    import HotOfferList from "@/components/posts/HotOfferList"
    import TopPostsList from '@/components/posts/TopPostsList'


    export default {
        head() {
            return {
                title: 'StyleTravel Bulgaria',
                meta: [
                    { hid: 'description', name: 'description', content: 'Holiday trips, quick vacations, school trips - we have them all.' }
                ]
            }
        },
        components: {
            Banner,
            HotOfferList,
            TopPostsList
        },
        // data() {
        //     return {
        //         displayModal: false,
        //
        //     }
        // },
        computed: {
            loadedPosts() {
                return this.$store.getters.loadedPosts;
            }
        },

    }

</script>

<style>
    /* offers banner */
    .container-fluid {

        width: 100%;
        padding: 0;

    }

    .offers-banner {
        width: 100vw;
        height: 230px;
        padding: 0;
        /*background-repeat: no-repeat;*/
        background-image: url("~/static/images/offersBanner.jpg");
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
    
    
    
    
    .row {
        margin: 0 !important;
    }

    .offers {
        padding-top: 20px;
        padding-bottom: 20px;
    }

    .locations {
        padding-top: 20px;
        padding-bottom: 20px;
    }

    .section-title {
        text-align: center;
        margin-bottom: 20px;
        border-bottom: 2px solid #ccc;
        font-size: 1.7rem;
        padding-bottom: 10px;
    }

    .container {
        /*margin: 0 !important;*/
        display: flex;
        /*min-height: 100vh;*/
        /*justify-content: center;*/
        /*align-items: center;*/
        /*text-align: center;*/
    }

    .title {
        font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif; /* 1 */
        display: block;
        font-weight: 300;
        font-size: 100px;
        color: #35495e;
        letter-spacing: 1px;
    }

    .subtitle {
        font-weight: 300;
        font-size: 42px;
        color: #526488;
        word-spacing: 5px;
        padding-bottom: 15px;
    }

    .links {
        padding-top: 15px;
    }
</style>
