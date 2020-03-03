<template>
  <div>
    <h2>HTML Table</h2>

    <table class="container">
      <th>Species</th>
      <th>Name</th>
      <th>Date of Birth</th>
      <tr v-for="animal in animals" :key="animal.name">
        <td>{{ animal.species }}</td>
        <td>{{ animal.name }}</td>
        <td>{{isTheyHaveBirdht( animal.date_of_birth )}}</td>
        <button @click="remove(animal)">Remove</button>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      animals: [
        { species: "dog", name: "Pera", date_of_birth: null },
        { species: "dog", name: "Gojko", date_of_birth: null },
        { species: "cat", name: "Milunka", date_of_birth: new Date() },
        { species: "cat", name: "Zile", date_of_birth: new Date() },
        { species: "cat", name: "Mile", date_of_birth: new Date() },
        { species: "bird", name: "Joca", date_of_birth: new Date() }
      ]
    };
  },
  methods: {
    isTheyHaveBirdht(date) {
      if (!date) {
        return "nepoznat";
      }
      return date;
    },
    remove(animal) {
      let index = this.animals.indexOf(animal);
      this.animals.splice(index, 1);
    }
  }
};
</script>