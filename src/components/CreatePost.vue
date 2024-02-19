<template>
    <div class="container">
        <div class="row">
            <form @submit.prevent="createPost">
                <div class="my-3">
                    <label for="userId" class="form-label">Post User Id</label>
                    <input type="text" id="userId" v-model="formData.userId" class="form-control">
                </div>
                <div class="mb-3">
                    <label for="title" class="form-label">Post Title</label>
                    <input type="text" id="title" v-model="formData.title" class="form-control">
                </div>
                <div class="mb-3">
                    <label for="body" class="form-label">Post Body</label>
                    <input type="text" id="body" v-model="formData.body" class="form-control">
                </div>
                <button type="submit" class="btn btn-primary">Create Post</button>
            </form>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    name: 'CreatePost',
    data() {
        return {
            formData: {
                userId: '',
                title: '',
                body: '',
            }
        }
    },
    methods: {
        createPost() {
            axios.post('https://jsonplaceholder.typicode.com/posts', this.formData)
                .then((response) => {
                    console.log(response);
                })
                .catch((error) => {
                    console.log(error);
                })
        }
    }
}
</script>

<style scoped></style>