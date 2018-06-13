<template>
    <section class="post-list">
        <OfferPreview
                v-for="post in postsReversed.slice(0, 3)"
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

        />
    </section>
</template>

<script>
    import OfferPreview from '@/components/posts/OfferPreview'

    export default {
        components: {
            OfferPreview
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
            postsReversed() {
                return [...this.posts].reverse()
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

