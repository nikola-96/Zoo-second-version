<template>
  <div>
    <h2>HTML Table</h2>
    <table>
      <tr v-for="animal in animals" :key="animal.name">
        <td>{{ animal.species }}</td>
        <td>{{ animal.name }}</td>
        <td>{{ animal.date_of_birth }}</td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      animals: [
        { species: "dog", name: "Pera", date_of_birth: new Date() },
        { species: "dog", name: "Gojko", date_of_birth: new Date() },
        { species: "cat", name: "Milunka", date_of_birth: new Date() },
        { species: "cat", name: "Zile", date_of_birth: new Date() },
        { species: "cat", name: "Mile", date_of_birth: new Date() },
        { species: "bird", name: "Joca", date_of_birth: new Date() }
      ]
    };
  }
};
</script>