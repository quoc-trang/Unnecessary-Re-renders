<script setup lang="ts">
import { faker } from "@faker-js/faker";
import PeopleTableRow from "@/components/PeopleTableRow.vue";
import { ref } from "vue";

const people = Array.from({ length: 20 }, () => ({
  id: crypto.randomUUID(),
  name: faker.person.fullName(),
  company: faker.company.name(),
  job: faker.person.jobTitle(),
  country: faker.location.country(),
  color: faker.internet.color(),
  image: faker.image.avatar(),
}));

const activePerson = ref("");

function toggleActivePerson(id: string) {
  activePerson.value = id;
}
</script>
<template>
  <div class="overflow-x-auto">
    <h2 class="text-xl font-bold">People Table</h2>
    <p class="text-sm text-gray-500">Click on a row to select a person</p>
    <table class="table">
      <!-- head -->
      <thead>
        <tr>
          <th>Name</th>
          <th class="text-center">Job</th>
          <th class="text-center">Favorite Color</th>
        </tr>
      </thead>
      <tbody>
        <!-- row 1 -->
        <PeopleTableRow
          v-for="person in people"
          @click="toggleActivePerson(person.id)"
          :key="person.id"
          :person="person"
          :active="activePerson === person.id"
          v-memo="[activePerson === person.id]"
        />
      </tbody>
    </table>

    <h2 class="mt-5 text-xl font-bold">Selected Person</h2>
    {{ people.find((p) => p.id === activePerson)?.name || "No one selected" }}
  </div>
</template>
