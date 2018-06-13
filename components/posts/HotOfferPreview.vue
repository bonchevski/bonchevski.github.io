<template>
    <div>
        <div class="post-preview">
            <article>
                <div
                        class="post-thumbnail"
                        :style="{backgroundImage: 'url(' + offerImgLink + ')'}"></div>
                <div class="post-content">
                    <h1>{{offerLocation}}</h1>
                    <p>{{offerDescription | snippet}}...</p>
                    <p>{{ offerPrice }}</p>
                </div>

                <b-btn class="more-details-btn" v-b-modal="id">See more details</b-btn>
            </article>


            <!-- Modal Component -->
            <b-modal :id="id" :title="offerLocation" ok-title="Continue" cancel-title="Go back"
                     @ok.prevent="displayCheckout = !displayCheckout">
                <b-container fluid>
                    <div v-if="displayCheckout">
                        <div
                                class="post-thumbnail"
                                :style="{backgroundImage: 'url(' + offerImgLink + ')'}"></div>
                        <h1>{{offerLocation}}</h1>
                        <p>{{ offerDescription }}</p>

                        <div class="informations">
                            <p>Date: {{offerDateDay}} {{offerDateMonth}} {{offerDateYear}}</p>
                            <p>Price: {{ offerPrice }}</p>
                            <p class="spots">Available spots: {{ offerSpots }}</p>
                            <p>Discount: {{ offerDiscount }}%</p>
                        </div>
                    </div>


                     <div class="checkout" v-else>
                        <form id="form" method="post" v-on:submit="validateForm">

                           <div class="form-group">
          <label class="form-control-label" for="name">Name</label>
          <input id="fullName" fullName="fullName" class="form-control" type="text" 
                 v-model="fullName" v-bind:class="{ 'is-invalid': attemptSubmit && missingName }">
          <div class="invalid-feedback">This field is required.</div>
        </div><!-- /form-group -->
                            <div class="form-group">
          <label class="form-control-label" for="number">Please enter the 16 digits on the front of your card.</label>
          <input id="cardNumber" name="cardNumber" class="form-control" type="text" v-model="cardNumber" v-bind:class="{ 'is-invalid': attemptSubmit && wrongNumber }">
          <div class="invalid-feedback">Oops something went wrong! Please check that the numbers you entered are 16 in total.</div>
        </div><!-- /form-group -->
                            <div class="full-wrapper form-group" id="fixLines">
                                <div class="half-wrapper">
                                    <h1 class="checkout-title">CVR</h1>
                                    <input type="tel" id="cvrNumber" name="cvrNumber" 
                                    class="form-control" 
                                    v-model="cvrNumber" 
                                    v-bind:class="{ 'is-invalid': attemptSubmit && wrongCVR }">
          <div class="invalid-feedback">Make sure you have entered all 3 digits of your CVR on the back of your card!</div>
        </div><!-- /form-group -->
                                <div class="half-wrapper">
                                    <h1 class="checkout-title"> Expiry date</h1>
                                    <input type="date">
                                </div>
                            </div>


                            <div class="form-group">
                             <input type="text" id="address" name="address" 
                                    placeholder=" Address: Street, bldg., apt., zip code"
                                    class="form-control" 
                                    v-model="address" 
                                    v-bind:class="{ 'is-invalid': attemptSubmit && missingAddress }">
                            <div class="invalid-feedback">Oops!This field is required! Pleae fill in your address details.</div>
                            </div>
                           <div class="form-group" >
                             <input type="text" id="city" name="city" 
                                    placeholder="Enter your City here..."
                                    class="form-control" 
                                    v-model="city" 
                                    v-bind:class="{ 'is-invalid': attemptSubmit && missingCity }">
                            <div class="invalid-feedback">Oops!This field is required! Pleae fill in your current city of residency.</div>
                            </div>
                             <div class="form-group">
                             <input type="text" id="country" name="country" 
                             placeholder="Country"
                                    class="form-control" 
                                    v-model="country" 
                                    v-bind:class="{ 'is-invalid': attemptSubmit && missingCountry }">
                            <div class="invalid-feedback">Oops!This field is required! Pleae fill in your current country of residency.</div>
                            </div>
                            <div class="form-group">
                             <input type="email" id="email" name="email" placeholder="Youremail@example.com"
                                    class="form-control" 
                                    v-model="email" 
                                    v-bind:class="{ 'is-invalid': attemptSubmit && missingEmail }">
                            <div class="invalid-feedback">Oops!This field is required! Pleae enter your valid e-mail so we can contact you if needed!</div>
                            </div>
<button class="btn btn-primary" >Reserve Spots</button>

                        
                        </form>
                    </div>
                </b-container>

            </b-modal>


            <!--<div class="modal" id="exampleModa2" role="dialog"-->
            <!--v-if="displayModal">-->
            <!--<div class="modal-dialog" role="document">-->
            <!--<div class="modal-content">-->
            <!--<div class="modal-header">-->
            <!--<h5 class="modal-title" id="exampleModalLabel">{{ offerLocation }}</h5>-->
            <!--<button type="button" class="close" data-dismiss="modal" aria-label="Close">-->
            <!--<span aria-hidden="true">&times;</span>-->
            <!--</button>-->
            <!--</div>-->
            <!--<div class="modal-body">-->
            <!--<div-->
            <!--class="post-thumbnail"-->
            <!--:style="{backgroundImage: 'url(' + offerImgLink + ')'}"></div>-->
            <!--<h1>{{offerLocation}}</h1>-->
            <!--<p>{{ offerDescription }}</p>-->

            <!--<div class="informations">-->
            <!--<p>Date: {{offerDateDay}} {{offerDateMonth}} {{offerDateYear}}</p>-->
            <!--<p>Price: {{ offerPrice }}</p>-->
            <!--<p class="spots">Available spots: {{ offerSpots }}</p>-->
            <!--<p>Discount: {{ offerDiscount }}%</p>-->
            <!--</div>-->
            <!--</div>-->
            <!--<div class="modal-footer">-->
            <!--<button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>-->
            <!--<nuxt-link :to="postLink" type="button" class="btn btn-primary">Save changes</nuxt-link>-->
            <!--</div>-->
            <!--</div>-->
            <!--</div>-->
            <!--</div>-->
        </div>

    </div>
</template>

<script>
    import 'bootstrap/dist/css/bootstrap.css'
    import 'bootstrap-vue/dist/bootstrap-vue.css'

    export default {
        name: 'HotOfferPreview',
        data() {
            return {
                fullName: '',
                cardNumber:'',
                cvrNumber: '',
                address: '',
                city: '',
                country: '',
                email: '',
                displayModal: false,
                displayCheckout: true
            }
        },
        props: {
            id: {
                type: String,
                required: true
            },
            isAdmin: {
                type: Boolean,
                required: true
            },
            offerLocation: {
                type: String,
                required: true
            },
            offerPrice: {
                type: String,
                required: true
            },
            offerDescription: {
                type: String,
                required: true
            },
            offerImgLink: {
                type: String,
                required: true
            },
            offerDateDay: {
                type: String,
                required: true
            },
            offerDateMonth: {
                type: String,
                required: true
            },
            offerDateYear: {
                type: String,
                required: true
            },
            offerSpots: {
                type: String,
                required: true
            },
            offerDiscount: {
                type: String,
                required: true
            }
        },
        computed: {
            postLink() {
                return this.isAdmin ? '/admin/' + this.id : '/Offers/' + this.id
            },
                     missingName: function () { return this.fullName === ''; },
                missingAddress: function() {return this.address === '';},
                missingCity: function () {return this.city ==='' ;},
                missingCountry: function () {return this.country ==='' ;},
                missingEmail: function () {return this.email ==='' ;},
                wrongNumber: function () {
      return (
        this.cardnNumber === '' ||
        this.cardNumber.length < 16 
      )
    },
              wrongCVR: function () {
      return (
        this.cvrNumber === ''
      )},
        },
        filters: {
            snippet: function (value) {
                return value.slice(0, 70)
            }
        },
        methods: {
            validateForm: function (event) {
    
      this.attemptSubmit = true;
      if (this.missingName)
      if (this.cardNumber)
      if (this.cvrNumber)
      if (this.address)
      if (this.city)
      if (this.country)
      if (this.email)
      //if (this.cardnNumber.length < 16)
       event.preventDefault();
    },

        },

    }
</script>


<style scoped>
    #fixLines{
        margin-left:0%;

}
    .buy-booking {
        float: left;
        margin-left: 5%;
    }

    .full-wrapper {
        margin-left: 5%;
        margin-right: 5%;
        width: 90%;
        font-size: 1rem;
        margin-bottom: 5%;
    }

    .half-wrapper {
        width: 45%;
        margin-right: 5%;
        float: left;
        margin-bottom: 5%;
    }

    .half-wrapper input {
        width: 80%;
    }

    input::-webkit-outer-spin-button,
    input::-webkit-inner-spin-button {
        /* display: none; <- Crashes Chrome on hover */
        -webkit-appearance: none;
        margin: 0; /* <-- Apparently some margin are still there even though it's hidden */
    }

    .full-width {
        width: 90%;
    }

    .checkout-title {
        font-size: 1.2rem;
    }

    input {
        border-radius: 3px;
        border: 1px solid #ccc
    }

    .informations {
        text-align: right;
        border-top: 1px solid #ccc
    }

    .more-details-btn {
        margin-bottom: 10px;
        margin-left: 10px;

    }

    .post-preview {
        border: 1px solid #ccc;
        box-shadow: 0 2px 2px #ccc;
        background-color: white;
        width: 90%;
    }

    a {
        text-decoration: none;
        color: black;
    }

    .post-preview {
        width: 350px;
        margin: 10px;
    }

    @media (min-width: 576px) {
        .post-preview {
            width: 350px;
            margin: 10px;
        }
    }

    /*// Medium devices (tablets, 768px and up)*/
    @media (min-width: 768px) {

    }

    /*// Large devices (desktops, 992px and up)*/
    @media (min-width: 992px) {
        .post-preview {
            width: 350px;
            margin: 10px;
        }
    }

    h1 {
        font-size: 1.2rem
    }

    .post-thumbnail {
        width: 100%;
        height: 200px;
        background-position: center;
        background-size: cover;
    }

    .post-content {
        padding: 10px;
        text-align: left;
    }

    a:hover .post-content,
    a:active .post-content {
        background-color: #ccc;
    }
</style>
