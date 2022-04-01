<template>
  <div class="home">
    <ul>
    <li v-for="item in books" v-bind:key="item.url">
      Ime: <router-link :to=" '/bookDetails/' + item.name"> {{ item.name }}</router-link> <br>
      Autor: {{item.authors}} <br>
      Izdano: {{item.released}} <br> <br>
    </li>
  </ul>
    {{books}}
    
  </div>
</template>

<script>


export default {
  name: 'HomeView',
  data: function () {
    return {
      books: [],
    };
  },
  async mounted() {
    let rezultat = await fetch(
      'http://ntankovic.unipu.hr:8000/books.json'
    );
    let podaci = await rezultat.json();

    this.books = podaci;
  },
}
</script>
