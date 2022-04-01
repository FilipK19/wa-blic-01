<template>
  <div class="bookdetails">
    <h1>This is an about page</h1>
    <ul>
    <li v-for="item in books" v-bind:key="item.url">
      {{booknumber}}
    </li>
    </ul>
  </div>
</template>

<script>
export default {
  components: {
    
  },
  name: "BookDetails",
  props: ["booknumber"],

  data: function () {
    return {
      books: [],
      bookdetails: [],
    }
  },
created: async function() {
    let rezultat = await fetch(
      'https://www.anapioficeandfire.com/api/books/' + 1)
    let podaci = await rezultat.json();
    this.books = podaci
},


created2: async function() {
    let rezultat2 = await fetch(
    )
    let podaci2 = await rezultat2.json();
    this.bookdetails = podaci2
}

}
</script>
