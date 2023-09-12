<template>
    <form class="d-flex" role="search">
        <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search" @keyup="searchEvent($event)" v-model="searchInput">
        <button class="btn btn-outline-success" type="submit">Search</button>
    </form>
</template>

<script>
    
    export default {
        name: "SearchBookBar",
        data() {
            return {
                localSearchBook : "",
            }
        },
        methods: {
            searchEvent(e) {
                this.localSearchBook = e.target.value;
                this.$emit("searchBarInput",this.localSearchBook);
            }
        }
    }
</script>