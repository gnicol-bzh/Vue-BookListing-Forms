<template>
    <form v-on:submit.prevent="bookSubmit(bookTitle, bookAuthor)" class action="#" method="post">
        <input v-model="bookTitle" type="text" name="title" value placeholder="Book Title" />
        <input v-model="bookAuthor" type="text" name="author" value placeholder="Book Author" />
        <div>
            <input id="finishedReading" v-model="bookData.finishedReading" type="checkbox" /><label for="finishedReading">Finished Reading</label>
            <input id="borrowed" v-model="bookData.ownership" type="radio" value="borrowed"><label for="borrowed">borrowed</label>
            <input id="bought" v-model="bookData.ownership" type="radio" value="bought"><label for="bought">bought</label>
        </div>
        <button type="submit" name="button">Add Book</button>
    </form>
</template>

<script>
export default {
    name: "BookForm",
    props: ["books"],
    data() {
        return {
            bookTitle: "",
            bookAuthor: "",
            bookData: {
                bookTitle: "",
                bookAuthor: "",
                finishedReading: false,
                ownership: []
            }
        };
    },
    methods: {
        bookSubmit(bookTitle, bookAuthor) {
            this.$emit("addBook", bookTitle, bookAuthor);
        }
    }
};
</script>

<style>
</style>
