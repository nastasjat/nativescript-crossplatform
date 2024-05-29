<template>
  <Page>
    <TabView>
      <TabViewItem title="Завдання 1">
        <StackLayout class="task-container">
          <Label
            text="Завдання 1: Знайдіть кількість парних чисел, які при діленні на 3 дають в остачі 2 на заданому проміжку чисел [a, b]."
            class="task-text"
            textWrap="true"
          />
          <StackLayout>
            <TextField v-model="a" hint="Початкове число" class="input-field" />
            <TextField v-model="b" hint="Кінцеве число" class="input-field" />
            <Button
              text="Знайти парні числа"
              @tap="findEvenNumbers"
              class="action-button"
            />
            <Label
              v-if="result1 !== null"
              :text="`Кількість парних чисел: ${result1}`"
              class="result-label"
            />
          </StackLayout>
        </StackLayout>
      </TabViewItem>

      <TabViewItem title="Завдання 2">
        <StackLayout class="task-container">
          <Label
            text="Завдання 2: Задано три числа. Знайдіть кількість тих з них, які кратні 27."
            class="task-text"
            textWrap="true"
          />
          <StackLayout>
            <TextField v-model="num1" hint="Перше число" class="input-field" />
            <TextField v-model="num2" hint="Друге число" class="input-field" />
            <TextField v-model="num3" hint="Третє число" class="input-field" />
            <Button
              text="Знайти кількість чисел кратних 27"
              @tap="findMultiplesOf27"
              class="action-button"
            />
            <Label
              v-if="result2 !== null"
              :text="`Кількість чисел кратних 27: ${result2}`"
              class="result-label"
            />
          </StackLayout>
        </StackLayout>
      </TabViewItem>
    </TabView>
  </Page>
</template>

<script>
export default {
  data() {
    return {
      a: '',
      b: '',
      num1: '',
      num2: '',
      num3: '',
      result1: null,
      result2: null,
    };
  },
  methods: {
    findEvenNumbers() {
      const a = parseInt(this.a);
      const b = parseInt(this.b);
      let count = 0;
      for (let i = a; i <= b; i++) {
        if (i % 2 === 0 && i % 3 === 2) {
          count++;
        }
      }
      this.result1 = count;
    },
    findMultiplesOf27() {
      const num1 = parseFloat(this.num1);
      const num2 = parseFloat(this.num2);
      const num3 = parseFloat(this.num3);
      let count = 0;
      if (num1 % 27 === 0) count++;
      if (num2 % 27 === 0) count++;
      if (num3 % 27 === 0) count++;
      this.result2 = count;
    },
  },
};
</script>

<style scoped>
.task-container {
  padding: 20px;
  margin-top: 50px;
}
.task-text {
  margin-bottom: 30px;
  font-weight: bold;
  white-space: normal;
}
.input-field {
  margin-bottom: 10px;
  padding: 40px;
  border: 1px solid #ccc;
  border-radius: 5px;
}
.action-button {
  margin-bottom: 10px;
  padding: 20px;
  background-color: purple;
  color: #fff;
  border: none;
  border-radius: 5px;
}
.result-label {
  padding: 10px;
  font-weight: bold;
}
</style>
