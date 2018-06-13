<template>
    <footer class="container">
        <div class="the-footer">
            <div class="col-xs-7 col-md-6 col-lg-3 info">
            <h1 class="address">Where to find us: bul. "Vasil Levski" 8, Sofia</h1>
            <p class="copyright"> &#169; All rights reserved.</p>
            </div>

            <div class="some d-none d-md-block col-md-4 offset-md-2 col-lg-2 offset-lg-5">

                <a href="https://www.facebook.com/%D0%A1%D1%82%D0%B8%D0%BB-%D0%A2%D1%80%D0%B0%D0%B2%D0%B5%D0%BB-117497205586305/"><i class="fa fa-instagram fa-3x"></i></a>
                <a href="https://www.instagram.com/styletravelbg/"><i class="fa fa-facebook-f fa-3x"></i></a>

            </div>

        <div class="col-xs-2 offset-xs-1 col-md-2 offset-md-0 col-lg-1 offset-lg-0 arrow">
            <a href="#main"><i class="fa fa-angle-up fa-3x"></i></a>
        </div>
        </div>
    </footer>
</template>

<script>


    export default {
        name: "the-footer",

    }
</script>

<style scoped>
    .container {
        min-height: 0;
        max-width: 1920px;
        padding: 0;
        justify-content: center;
        align-items: center;
        text-align: center;
    }
    .the-footer {
        color: white;
        width: 100%;
        height: 150px;
        display: flex;
        justify-content: space-around;
        align-items: center;
        background-color: #47494e;
        z-index: 100;
        box-sizing: border-box;

    }

    a {
        color: white;
    }

    i {
        width: 64px;

    }

    i:hover {
        background-color: white;
        color: #47494e;
        border-radius: 5px;
    }

    .address {
        padding-top: 10px;
        margin-bottom: 5px !important;
        font-size: .8rem;
        width: 100%;
        text-align: left;
    }

    .copyright {
        font-size: .7rem;
        margin-bottom: 1px !important;
        text-align: left;
    }
</style>