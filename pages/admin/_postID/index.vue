<template>
    <div class="admin-post-page">
        <section class="update-form">
            <add-offer :post="loadedPost" @submit="onSubmitted"/>
        </section>
    </div>
</template>

<script>
    import addOffer from "@/components/admin/addOffer";


    export default {
        layout: "admin",
        middleware: ['check-auth', 'auth'],
        components: {
            addOffer
        },

        asyncData(context) {
            return context.app.$axios
                .$get(
                    process.env.baseUrl + "/Offers/" +
                    context.params.postId +
                    ".json"
                )
                .then(data => {
                    return {
                        loadedPost: {...data, id: context.params.postId}
                    };
                })
                .catch(e => context.error());
        },
        methods: {
            onSubmitted(editedPost) {
                this.$store.dispatch("editPost", editedPost).then(() => {
                    this.$router.push("/admin");
                });
            }
        }
    };
</script>

<style scoped>
    .update-form {
        width: 90%;
        margin: 20px auto;
    }

    @media (min-width: 768px) {
        .update-form {
            width: 500px;
        }
    }
</style>
