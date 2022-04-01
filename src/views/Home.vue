<template>
  <div class="home">
    <ul>
    <li v-for="item in books" v-bind:key="item.url">
      {{booknumber = Number(item.url.split("/").slice(-1)[0])}}
      Ime: <router-link :to=" '/bookDetails/' + booknumber"> {{ item.name }}</router-link> <br>
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
  props: ["booknumber"],
  data: function () {
    return {
      books: [],
    };
  },
  async mounted() {
    let rezultat = await fetch(
      'https://www.anapioficeandfire.com/api/books'
    );
    let podaci = await rezultat.json();

    this.books = podaci;
  },
}
</script>
