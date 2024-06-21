<template>
  <div>
    <div v-for="book in books" :key="book.id">
      <p>{{ book.name }}</p>
      <button @click="toggleDesk(book.id)">Show Description</button>
      <p v-if="showDescription.includes(book.id)">{{ book.desc }} {{ book.publication }}</p>
    </div>

  </div>
</template>

<script>
export default {
  name: 'BookComp',

  data () {
    return {
      books: [
        {
          id: 1,
          name: 'Книга 1',
          desc: 'lorem ver dolor sit amet, consectetur',
          publication: 2012
          // showDescription: false
        },
        {
          id: 2,
          name: 'Книга 2',
          desc: 'lorem ver dolor sit amet, consectetur',
          publication: 1997
          // showDescription: false
        },
        {
          id: 3,
          name: 'Книга 3',
          desc: 'lorem ver dolor sit amet, consectetur',
          publication: 2000
          // showDescription: false
        }
      ],
      showDescription: []
    }
  },
  computed: {

  },

  methods: {
    toggleDesk (id) {
      const findIndex = this.showDescription.indexOf(id)
      if (findIndex === -1) {
        this.showDescription.push(id)
      } else {
        this.showDescription.splice(findIndex, 1)
      }
    }
  }
}
</script>

<style lang="scss" scoped>
</style>
