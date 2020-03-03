<template>
  <div>
    <h2>Animal list</h2>
    <form @submit.prevent="addAnimal">
      <div>
        <p>Add new animal</p>
        <label for>Species:</label>
        <input type="text" name="species" v-model="newAnimal.species" /> &nbsp;
        <label for>Name:</label>
        <input type="text" name="name" v-model="newAnimal.name" /> &nbsp;
        <label for>Date of Birth:</label>
        <input type="text" name="date_of_birth" v-model="newAnimal.date_of_birth" />
        <label for="cars">Select species:</label> &nbsp;
        <select v-model="newAnimal.evolution_species">
          <option value="Invertebrates">Invertebrates</option>
          <option value="Amphibians">Amphibians</option>
          <option value="Reptiles">Reptiles</option>
          <option value="Birds">Birds</option>
          <option value="Mammals">Mammals</option>
        </select>
        <br />
        <button type="submit">Add new animal</button>
      </div>
    </form>
    <br />

    <table class="container">
      <th>Evolution Species</th>
      <th>Species</th>
      <th>Name</th>
      <th>Date of Birth</th>
      <tr v-for="animal in animals" :key="animal.name">
        <td>{{ animal.evolution_species }}</td>
        <td>{{ animal.species }}</td>
        <td>{{ animal.name }}</td>
        <td>{{isTheyHaveBirdht( animal.date_of_birth )}}</td>
        <button @click="remove(animal)">Remove</button>
        <button @click="moveToTop(animal)">Move To Top</button>
      </tr>
    </table>
    <br />
    <table>
      <th>Evolution Species</th>
      <tr v-for="species in list_evolution_species" :key="species">
        <td>{{ species }}</td>
        <button @click="showSpecies(species)">Show all</button>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      animals: [
        {
          evolution_species: "Mammals",
          species: "Dog",
          name: "Stella",
          date_of_birth: null
        },
        {
          evolution_species: "Mammals",
          species: "Dog",
          name: "Gojko",
          date_of_birth: null
        },
        {
          evolution_species: "Mammals",
          species: "Cat",
          name: "Mila",
          date_of_birth: new Date()
        },
        {
          evolution_species: "Mammals",
          species: "Cat",
          name: "Zile",
          date_of_birth: new Date()
        },
        {
          evolution_species: "Mammals",
          species: "Cat",
          name: "Mile",
          date_of_birth: new Date()
        },
        {
          evolution_species: "Mammals",
          species: "Bird",
          name: "Joca",
          date_of_birth: new Date()
        }
      ],
      newAnimal: {},
      list_evolution_species: [
        "Invertebrates",
        "Amphibians",
        "Reptiles",
        "Birds",
        "Mammals"
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
    },
    moveToTop(animal) {
      this.remove(animal);
      this.animals.unshift(animal);
    },
    addAnimal() {
      this.animals.push(this.newAnimal);
      this.newAnimal = {};
    },
    showSpecies(species) {
      let animalSpecies = [];
      this.animals.forEach(animal => {
        if (animal.evolution_species == species) {
          animalSpecies.push(animal.name);
        }
      });
      alert(animalSpecies);
    }
  }
};
</script>