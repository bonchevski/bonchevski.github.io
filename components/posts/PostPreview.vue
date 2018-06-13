<template>
    <div class="post-preview">
        <nuxt-link :to="postLink" class="post-preview">
            <article>
                <div
                        class="post-thumbnail"
                        :style="{backgroundImage: 'url(' + offerImgLink + ')'}"></div>
                <div class="post-content">
                    <h1>{{offerLocation}}</h1>
                    <p>{{offerDescription | snippet}}...</p>
                    <p>{{ offerPrice }}</p>
                </div>
            </article>
        </nuxt-link>
    </div>
</template>

<script>
    import 'bootstrap/dist/css/bootstrap.css'
    import 'bootstrap-vue/dist/bootstrap-vue.css'

    export default {
        name: 'PostPreview',
        data() {
            return {
                displayModal: false
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
        },
        computed: {
            postLink() {
                return this.isAdmin ? '/admin/' + this.id : '/posts/' + this.id
            }
        },
        filters: {
            snippet: function (value) {
                return value.slice(0, 70)
            }
        }
    }
</script>


<style scoped>
    .post-preview {
        /*border: 1px solid #ccc;*/
        box-shadow: 0 2px 2px #ccc;
        background-color: white;
        width: 80%;
        height: 400px;
    }

    a {
        text-decoration: none;
        color: black;
    }

    @media (min-width: 850px) {
        .post-preview {
            width: 330px;
            margin: 10px;
        }
    }

    h1 {
        font-size: 1.5rem
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
    }
</style>
