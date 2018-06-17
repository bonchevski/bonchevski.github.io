<template>
    <div>
        <section class="filter-section">
            <div class="search-wrapper col-xs-10 offset-xs-1 col-lg-4 offset-lg-4 col-xl-4 offset-xl-4 align-content-center">
                <h1 class="search-title">Search:</h1>
                <input type="text" v-model="search" placeholder=" search for your next trip's location">
                <!--<AdvancedSearchToggle @toggle="$emit('advancedSearchToggle')"/>-->


                <div class="row">
                    <div class="col-md-3">
                        <h3>Locations</h3>
                        <ul>
                            <li v-for="location in locations">
                                <input type="checkbox" v-model="checkedLocations" v-bind:value="location"/> {{ location }}
                            </li>
                        </ul>
                        <span>Checked locations: {{ checkedLocations }}</span>
                    </div>

                </div>

            </div>
        </section>

        <section class="post-list">
            <TripsPreview
                    v-for="post in filteredCountries"
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
                    :offerCountry="post.offerCountry"
            />
        </section>
    </div>
</template>

<script>
    import TripsPreview from '@/components/posts/TripsPreview'
    // import AdvancedSearchToggle from '@/components/AdvancedSearchToggle'

    export default {
        components: {
            TripsPreview,
            // AdvancedSearchToggle
        },
        data() {
            return {
                search: '',
                locations: ["Bulgaria" , 'England', 'Italy', 'Greece'],
                checkedLocations: []
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
            filteredPosts: function () {
                return this.posts


               if (!this.checkedLocations.length || !this.search.length ) {

                   return this.posts
                       .filter((post) => {
                           return post.offerLocation.toLowerCase().match(this.search)
                       })
                       .filter(j => this.checkedLocations.includes(j.offerCountry))
               }



               // let self = this;
                //
                // return self.posts
                //     .filter((post) => {
                //         return post.offerLocation.toLowerCase().match(self.search)
                //     })
                //     .filter((post) => {
                //         if (!self.checkedLocations.length) {
                //             // return post.offerCountry.includes(self.checkedLocations)
                //
                //             return self.posts;
                //             return self.posts.filter(j => self.checkedLocations.includes(j.offerCountry))
                //         }
                //     })
            },
            filteredCountries: function () {

                // if ( !this.checkedLocations.length ) {
                //     return this.posts
                // } else if ( this.search.length > 0 ) {
                //     return this.posts.filter((post) => { return post.offerLocation.toLowerCase().match(this.search)})
                // } else {
                //     return this.posts
                //         .filter((post) => {return post.offerLocation.toLowerCase().match(this.search)})
                //         .filter(j => this.checkedLocations.includes(j.offerCountry))
                // }



                if (!this.checkedLocations.length || this.search.length)
                    return this.posts


                // return this.jobs.reduce((a, j)=> {
                //   if (this.checkedLocations.includes(j.location))
                //     a.push(j)
                //   return a
                //  },[])
                return this.posts
                    .filter((post) => {return post.offerLocation.toLowerCase().match(this.search)})
                    .filter(j => this.checkedLocations.includes(j.offerCountry))

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

