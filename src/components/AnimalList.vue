<template>
  <div>
    <h2>HTML Table</h2>
    <form @submit.prevent="addAnimal">
      <div>
        <h3>Add new animal</h3>
        <label for>Species</label>
        <input type="text" name="species" v-model="newAnimal.species" /> &nbsp;
        <label for>Name</label>
        <input type="text" name="name" v-model="newAnimal.name" /> &nbsp;
        <label for>Date of Birth</label>
        <input type="text" name="date_of_birth" v-model="newAnimal.date_of_birth" />
        <br />
        <button type="submit">Add new animal</button>
      </div>
    </form>
    <br />

    <table class="container">
      <th>Species</th>
      <th>Name</th>
      <th>Date of Birth</th>
      <tr v-for="animal in animals" :key="animal.name">
        <td>{{ animal.species }}</td>
        <td>{{ animal.name }}</td>
        <td>{{isTheyHaveBirdht( animal.date_of_birth )}}</td>
        <button @click="remove(animal)">Remove</button>
        <button @click="moveToTop(animal)">Move To Top</button>
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
      ],
      newAnimal: {}
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
    },
    moveToTop(animal) {
      this.remove(animal);
      this.animals.unshift(animal);
    },
    addAnimal() {
      this.animals.push(this.newAnimal);
      this.newAnimal = {};
    }
  }
};
</script>