<template>
    <div>
        <div class="container-fluid">
            <div class="about-banner d-none d-md-block hidden-sm col-md-12">
                <h1 class="greeting align-items-center">About us</h1>
            </div>

            <h1 class="greeting-mobile d-md-none hidden-md col-8 offset-2">About us</h1>
        </div>
            <section class="about-info row">
                <div class="col-xs-10 offset-1 col-lg-5 col-xl-4 justify-content-center about-img">
                    <img src="../../static/images/about-family.jpg" alt="">
                </div>
                <div class="col-xs-10 offset-1 col-lg-5 offset-lg-1 col-xl-6 offset-xl-0 align-self-center">
                    <h1>Who we are</h1>
                    <p>We are StyleTravel, we were found in 2001 by Bob and Albena Tonchevi. We’re a family business and
                        we value the importance of having a good time together as families and friends. We organize all
                        kinds of trips, some of our specialties are family and group vacations in our wonderful balkan
                        region where we share the magical experience of embracing our culture and getting in touch with
                        the nature that surrounds us.</p>
                </div>
            </section>
            <section class="about-info row">
                <div class="col-xs-10 offset-1 col-lg-5 offset-lg-1 col-xl-4 about-img">
                    <img src="../../static/images/about-sofia.jpg" alt="">
                </div>
                <div class="col-xs-10 offset-1 col-lg-5 offset-lg-1 col-xl-6 offset-xl-0 align-self-center">
                    <h1>What we do</h1>
                    <p>Every season and holiday we have themed special trips to locations that are usually tied to the
                        theme either in a historical way or a traditional way. We also organize photography trips with
                        some of our friendly clients that do it professionally where we would have the group activity of
                        taking pictures of the landscapes or landmarks and most importantly have fun together. We’re
                        determined to not be just a travel agency but also educators! We travel with students from
                        schools all around the capital organized in partnership with the institutions. We value our
                        youth and believe they should be familiar with their beautiful and rich in traditions
                        country.</p>
                </div>
            </section>
            <section class="about-info row">
                <div class="col-xs-10 offset-1 col-lg-5 col-xl-4 about-img">
                    <img src="../../static/images/pulev.jpg" alt="">
                </div>
                <div class="col-xs-10 offset-1 col-lg-5 offset-lg-1 col-xl-6 offset-xl-0 align-self-center">
                    <h1>Join us!</h1>
                    <p>Last but not least we’re huge fans of our athletes, so we organize groups for events around the
                        world where our stars will have matches! We’re proud to say and to see the interest and passion
                        of our people who join us on these adventures to cheer for their success!</p>
                </div>
            </section>
        </div>
    </div>
</template>

<script>
    import 'bootstrap/dist/css/bootstrap.css'
    import 'bootstrap-vue/dist/bootstrap-vue.css'
    import TheBanner from '@/components/UI/banner'

    export default {
        head() {
            return {
                title: "About StyleTravel Bulgaria",
                meta: [{ hid: "description", name: 'description', content: 'Here you can find a short history of StyleTravel, from foundation until now and why we do what we do.'}]
            }
        },
        name: "index",
        components: {
            TheBanner
        },

    }
</script>

<style scoped>


    .container-fluid {

        width: 100%;
        padding: 0;

    }

    .about-banner {
        width: 100vw;
        height: 230px;
        padding: 0;
        /*background-repeat: no-repeat;*/
        background-image: url("~/static/images/aboutUs.jpg");
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


    .about-info {
       max-width: 100%;
        margin-top: 20px !important;
        margin-bottom: 20px !important;
    }

    .about-img img {
        max-width: 100%;
    }

    h1 {
        border-bottom: 1px solid #ccc;
        text-align: center !important;
    }

</style>