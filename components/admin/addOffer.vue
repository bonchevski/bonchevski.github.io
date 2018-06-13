<template>
    <form @submit.prevent="onSave">
        <app-control-input v-model="editedPost.offerLocation">Location</app-control-input>
        <app-control-input v-model="editedPost.offerPrice">Price</app-control-input>
        <app-control-input v-model="editedPost.offerSpots">Available places</app-control-input>
        <app-control-input v-model="editedPost.offerDateDay">Day</app-control-input>
        <app-control-input v-model="editedPost.offerDateMonth">Month</app-control-input>
        <app-control-input v-model="editedPost.offerDateYear">Year</app-control-input>
        <app-control-input v-model="editedPost.offerImgLink">Link to image</app-control-input>
        <app-control-input v-model="editedPost.offerDescription" control-type="textarea">Description</app-control-input>
        <app-control-input v-model="editedPost.offerDiscount">Discount</app-control-input>

        <app-button type="submit">Save</app-button>
        <app-button type="button" style="margin-left: 10px" btn-style="cancel" @click="onCancel">Cancel</app-button>
    </form>
</template>

<script>
    import AppControlInput from "@/components/UI/AppControlInput"
    import AppButton from "@/components/UI/AppButton"

    export default {
        components: {
            AppButton,
            AppControlInput
        },
        props: {
            post: {
                type: Object,
                required: false
            }
        },
        data() {
            return {
                editedPost: this.post
                    ? {...this.post}
                    : {
                        offerLocation: "",
                        offerPrice: "",
                        offerSpots: "",
                        offerDateDay: "",
                        offerDateMonth: "",
                        offerDateYear: "",
                        offerImgLink: "",
                        offerDescription: "",
                        offerDiscount: "",
                    }
            };
        },
        methods: {
            onSave() {
                // Save the post
                this.$emit('submit', this.editedPost)
            },
            onCancel() {
                // Navigate back
                this.$router.push("/admin");
            }
        }
    }
</script>

<style scoped>

</style>