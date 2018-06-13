<template>
    <div>
        <section class="filter-section">
            <div class="search-wrapper col-xs-10 offset-xs-1 col-lg-4 offset-lg-4 col-xl-4 offset-xl-4 align-content-center">
                <h1 class="search-title">Search:</h1>
                <input type="text" v-model="search" placeholder=" search for your next trip's location">
           <AdvancedSearchToggle @toggle="$emit('advancedSearchToggle')"/>
            </div>
        </section>

    <section class="post-list">
        <TripsPreview
                v-for="post in filteredPosts"
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
    </div>
</template>

<script>
    import TripsPreview from '@/components/posts/TripsPreview'
    import AdvancedSearchToggle from '@/components/AdvancedSearchToggle'
    export default {
        components: {
            TripsPreview,
            AdvancedSearchToggle
        },
        data() {
           return {
               search: ''
           }
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
            filteredPosts: function() {
                return this.posts.filter((post) => {
                    return post.offerLocation.toLowerCase().match(this.search)
                })
            }
        }
    }
</script>


<style scoped>
    input {
        border-radius: 2px;
        border: 1px solid;
        align-content: center;
        width: 100%;

    }

    .search-title {
        text-align: center;
        font-size: 1.8rem;
        border-bottom: 1px solid #ccc
    }


    .filter-section {
        margin-top: 50px;
    }


    .post-list {
        display: flex;
        padding: 20px;
        box-sizing: border-box;
        flex-wrap: wrap;
        align-items: center;
        justify-content: center;
    }
</style>

