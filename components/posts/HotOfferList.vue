<template>
    <section class="post-list">
        <HotOfferPreview
                v-for="post in hotOffers.slice(0,3)"
                :key="post.id"
                :id="post.id"
                :is-admin="isAdmin"
                :offerImgLink="post.offerImgLink"
                :offerLocation="post.offerLocation"
                :offerDescription="post.offerDescription"
                :offerPrice="post.offerPrice"
                :offerDateDay="post.offerDateDay"
                :offerDateMonth="post.offerDateMonth"
                :offerDateYear="post.offerDateYear"
                :offerSpots="post.offerSpots"
                :offerDiscount="post.offerDiscount"
        />
    </section>
</template>

<script>
    import HotOfferPreview from '@/components/posts/HotOfferPreview'

    export default {
        components: {
            HotOfferPreview
        },
        props: {
            isAdmin: {
                type: Boolean,
                default: false
            },
            posts: {
                type: Array,
                required: true
            }
        },
        computed: {
            hotOffers: function() {
                return this.posts.filter((post) => {
                    if(post.offerDiscount > 0) {
                    return post
                    }
                })
            }
        }
    }
</script>


<style scoped>

    .post-list {
        display: flex;
        padding: 20px;
        box-sizing: border-box;
        flex-wrap: wrap;
        align-items: center;
        justify-content: center;
    }
</style>

