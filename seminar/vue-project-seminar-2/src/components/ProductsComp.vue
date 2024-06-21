<template>
  <div>
    <div v-for="product in products" :key="product.id">
      <input type="number" v-model="product.quantity">
      <p>{{ product.name }}</p>
      <p>{{ product.price }}</p>
      <p>{{ product.quantity * product.price }}</p>
    </div>
    <p>Итого: {{ total }}</p>
  </div>
</template>

<script>
export default {
  name: 'ProductsComp',

  data () {
    return {
      products: [
        {
          id: 1,
          name: 'Товар 1',
          quantity: 5,
          price: 100,
          desc: 'lorem ver dolor sit amet, consectetur'
        },
        {
          id: 2,
          name: 'Товар 2',
          quantity: 8,
          price: 200,
          desc: 'lorem ver dolor sit amet, consectetur'
        },
        {
          id: 3,
          name: 'Товар 3',
          quantity: 10,
          price: 300,
          desc: 'lorem ver dolor sit amet, consectetur'
        }
      ]
    }
  },
  computed: {
    total () {
      return this.products.reduce((total, product) => {
        return total + product.quantity * product.price
      }, 0)
    }
  },

  methods: {

  }
}
</script>

<style lang="scss" scoped>
</style>

<!-- Разработать интерфейс корзины товаров, в котором пользователь
может изменять количество товаров в корзине и видеть общую сумму
покупки. Каждый товар представлен в виде блока, содержащего поле
ввода для изменения количества товара и отображение его цены. При
изменении количества товаров в поле ввода, необходимо
автоматически пересчитывать стоимость каждого товара и обновлять
общую сумму покупки.  -->
