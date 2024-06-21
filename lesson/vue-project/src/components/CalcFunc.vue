<template>
  <div>
      <input type="text" v-model="operant.value" v-for="operant in operants" :key="operant.id">
    {{ result }}
    <div>
      <button @click="calcAllResult(item)" v-for="item in operations" :key="item.id">
        {{ item }}
      </button>
    </div>
    <div>
      <template v-if="error">
        {{ error }}
      </template>
    </div>
    <div>
      <template v-if="result < 0"> Получилось отрицательное число</template>
      <template v-if="result >= 0 && result <= 100"> Получилось число от 0 до 100</template>
      <template v-if="result > 100"> Получилось число больше 100</template>
    </div>
    <div>
      Число Фиббоначи для первого поля ввода {{ fib1 }}
      Число Фиббоначи для воторого поля ввода {{ fib2 }}
    </div>
    <div>
      <h3>История операций</h3>
      <div v-for="log in logs" :key="log.id">
        {{ log }}
      </div>
    </div>
  </div>
</template>

<script>
import Vue from 'vue'
export default {
  name: 'CalcFunc',

  data () {
    return {
      operants: [
        { id: 1, value: '' },
        { id: 2, value: '' }
      ],
      result: 0,
      operations: ['+', '-', '*', '/'],
      error: '',
      logs: {}
    }
  },

  methods: {
    add () {
      this.result = Number(this.operants[0].value) + Number(this.operants[1].value)
    },
    minus () {
      this.result = Number(this.operants[0].value) - Number(this.operants[1].value)
    },
    mult () {
      this.result = Number(this.operants[0].value) * Number(this.operants[1].value)
    },
    div () {
      // this.result = Number(this.operant1) / Number(this.operant2)
      // const { operants } = this.operants
      // if (operants === 0) {
      //   this.error = 'На ноль делить нельзя'
      // } else {
      //   this.result = this.operant1 / this.operant2
      // }
      if (Number(this.operants[1].value) === 0) {
        this.error = 'На ноль делить нельзя'
        this.result = 0
      } else {
        this.result = ''
        this.result = Number(this.operants[0].value) / Number(this.operants[1].value)
      }
    },
    fib (n) {
      return n <= 1 ? n : this.fib(n - 1) + this.fib(n - 2)
    },
    calcAllResult (operation = '+') {
      this.error = ''
      switch (operation) {
        case '+':
          this.add()
          break
        case '-':
          this.minus()
          break
        case '*':
          this.mult()
          break
        case '/':
          this.div()
          break
      }
      // this.logs[Date.now()] = `${this.operants[0].value}${operation}${this.operants[1].value} = ${this.result}`
      const key = Date.now()
      const value = `${this.operants[0].value}${operation}${this.operants[1].value} = ${this.result}`
      Vue.set(this.logs, key, value)
    }
  },
  computed: {
    fib1 () {
      return this.fib(this.operants[0].value)
    },
    fib2 () {
      return this.fib(this.operants[1].value)
    }
  }
}
</script>

<style lang="scss" scoped></style>
