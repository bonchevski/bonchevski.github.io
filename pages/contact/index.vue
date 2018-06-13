<template>
    <div>
        <div class="container-fluid">
            <div class="contact-banner d-none d-md-block hidden-sm col-md-12">
                <h1 class="greeting align-items-center">Contact us</h1>
            </div>

            <h1 class="greeting-mobile d-md-none hidden-md col-8 offset-2">Contact us</h1>
        </div>

        <div class="col-10 offset-1">
            <h1>Here is where you can get in touch face-to-face or through an e-mail.</h1>
        </div>
        <div class="half-page-vertical col-xs-10 offset-0 col-lg-6 offset-lg-0">
            <form class="needs-validation" novalidate>
                <div class="form-row">
                    <div class="col-xs-10 offset-xs-1 col-md-6 offset-md-3 col-lg-6 offset-lg-2">
                        <label for="validationTooltip01">First name</label>
                        <input type="text" class="form-control" id="validationTooltip01" placeholder="First name"
                               value="Mark" required>
                        <div class="valid-tooltip">
                            Looks good!
                        </div>
                    </div>
                    <div class="from-row"></div>
                    <div class="col-xs-10 offset-xs-1 col-md-6 offset-md-3 col-lg-6 offset-lg-2">
                        <label for="validationTooltip02">Last name</label>
                        <input type="text" class="form-control" id="validationTooltip02" placeholder="Last name"
                               value="Otto" required>
                        <div class="valid-tooltip">
                            Looks good!
                        </div>
                    </div>
                </div>
                <div class="form-row">
                    <div class="col-xs-10 offset-xs-0 col-md-6 offset-md-3 col-lg-6 offset-lg-2">
                        <label for="validationTooltip03">City</label>
                        <input type="text" class="form-control" id="validationTooltip03" placeholder="City" required>
                        <div class="invalid-tooltip">
                            Please provide a valid city.
                        </div>
                    </div>
                    <div class="col-xs-10 offset-xs-1 col-md-6 offset-md-3 col-lg-6 offset-lg-2">
                        <label for="validationTooltip01">Subject</label>
                        <input type="text" class="form-control" id="validationTooltip01" placeholder="Subject" required>
                        <div class="invalid-tooltip">
                            Please mention the subject of your message.
                        </div>
                    </div>
                    <div class="col-xs-10 offset-xs-1 col-md-6 offset-md-3 col-lg-6 offset-lg-2">
                        <div class="form-group">
                            <label for="FormControlTextarea1">Message</label>
                            <textarea class="form-control" id="FormControlTextarea1" rows="5" placeholder="Your message"></textarea>
                        </div>
                    </div>
                </div>
                <div class="offset-xs-4 offset-md-4 button">
                    <button class="btn btn-primary" type="submit">Submit form</button>
                </div>
            </form>
        </div>

        <div class="half-page-vertical col-xs-11 offset-0 col-lg-6 offset-lg-0">
            <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d2932.840451780501!2d23.31989331546662!3d42.68592187916632!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x40aa850e8e6a8dad%3A0xac65765473d35b2e!2sbul.+%22Vasil+Levski%22+8%2C+1142+Sofia+Center%2C+Sofia%2C+Bulgaria!5e0!3m2!1sen!2sdk!4v1527699480998" width="600" height="450" frameborder="0" style="border:0; margin-top: 30px; margin-bottom: 30px;" allowfullscreen></iframe>
        </div>
    </div>

</template>

<script>
    import theBanner from "@/components/UI/banner"

    export default {
        head() {
            return {
                title: "Contact StyleTravel Bulgaria",
                meta: [{ hid: "description", name: 'description', content: 'Here is the place where you can send StyleTravel your questions'}]
            }
        },
        layout: "default",
        name: "index",
        components: {
            theBanner
        },

    }
</script>

<style scoped>
    .container-fluid {

        width: 100%;
        padding: 0;

    }

    .contact-banner {
        width: 100vw;
        height: 230px;
        padding: 0;
        /*background-repeat: no-repeat;*/
        background-image: url("~/static/images/contactUsBanner.jpg");
    }

    .greeting {
        color: white;
        text-align: left;
        padding-left: 30px;
        padding-top: 10vh;
        border: none;
    }

    .greeting-mobile {
        margin-top: 5%;
        text-align: center;
    }


    .button {
        padding-bottom: 10px;
    }


    .half-page-vertical {
        position: relative;
        float: left;
        margin-top: 20px;
        margin-bottom: 20px;
    }

    .form-row {
        margin-top: 10px;
    }

    h1 {
        padding-top: 20px;
        padding-bottom: 10px;
        font-size: 1.7rem;
        border-bottom: 2px solid #ccc;
    }


    @media (max-width: 575.98px) {
        iframe {
            width: 350px;
            height: 300px;
        }
    }

    @media (min-width: 768px) {
        iframe {
            width: 450px;
        }
    }

    @media (min-width: 992px) {
        iframe {
            width: 500px;
        }
    }
</style>