<template>
    <section class="main-content-book-page">
        <NavigationBar @sendBookPage="getUserInput"/>
        <BookTable v-if="filterBook.length==0" :importBookTable="this.bookListPage"/>
        <BookTable :importBookTable="this.filterBook"/>
    </section>
</template>

<script>
    import NavigationBar from './../NavigationBar.vue';
    import BookTable from './../BookTable.vue';
    
    export default {
        name: "BookPage",
        props: {
            bookListPage : [],
        },
        components: {
            NavigationBar,
            BookTable
        },
        data() {
            return {
                filterBook : [],
            }
        },
        methods: {
            getUserInput(e) {
                let byTitleList = [];
                let byAuthorList = [];
                let byGenreList = [];
                
                byTitleList = this.bookListPage.filter( (book) => book.title.toLowerCase().includes(e.toLowerCase()) );
                byAuthorList = this.bookListPage.filter( (book) => book.author.toLowerCase().includes(e.toLowerCase()) );
                byGenreList = this.bookListPage.filter( (book) => book.genre.toLowerCase().includes(e.toLowerCase()) );
                
                this.filterBook = this.array_unique(
                    [].concat(byTitleList,byAuthorList,byGenreList)
                ).sort();
                
                //Original
                // this.filterBook = this.bookListPage.filter( (book) => book.title.toLowerCase().includes(e.toLowerCase()) );
            },
            array_unique(newArray) {
                return [...new Set(newArray)];
            }
        },
        created() {
            // console.log(this.bookListPage);
        }
    }
</script>

<style>
.main-content-book-page {
    display: flex;
    flex-direction: column;
}
</style>