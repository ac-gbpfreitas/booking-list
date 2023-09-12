<template>
    <table class="book-table-list table table-striped">
      <thead>
        <th scope="col">
          #
        </th>
        <th scope="col">
          Book Title
        </th>
        <th scope="col">
          Book Author
        </th>
        <th scope="col">
          Book Genre
        </th>
        <th scope="col">
          Book ISBN
        </th>
        <th scope="col">
          Book Edition
        </th>
      </thead>
      <tbody>
        <tr v-for="book in importBookTable" :key="book.id">
          <td>
            {{ book.id }}
          </td>
          <td>
            {{ book.title }}
          </td>
          <td>
            {{ book.author }}
          </td>
          <td>
            {{ book.genre }}
          </td>
          <td>
            {{ book.isbn }}
          </td>
          <td>
            {{ book.edition }}th
          </td>
        </tr>
      </tbody>
    </table>
  </template>
  
  <script>
    export default {
      name: "BookTable",
      props: {
          importBookTable : [],
      },
      data() {
          return {
              localBookList : [],
          }
      },
      methods: {
          loadBooks() {
              this.localBookList = this.importBookTable;
          }
      },
      created() {
          this.loadBooks();
      }
    }
  </script>