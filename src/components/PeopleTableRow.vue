<script setup lang="ts">
interface Props {
  person: {
    id: string;
    name: string;
    company: string;
    job: string;
    country: string;
    color: string;
    image: string;
  };
  active: boolean;
}
const props = defineProps<Props>();

function consoleReRender() {
  console.log("PeopleTableRow re-rendered:" + props.person.name);
}
</script>
<template>
  <tr
    class="cursor-pointer"
    :class="{
      'bg-primary text-white': active,
    }"
  >
    <td>
      <div class="flex items-center gap-3">
        <div class="avatar">
          <div class="w-12 h-12 mask mask-squircle">
            <img :src="person.image" alt="Avatar Tailwind CSS Component" />
          </div>
        </div>
        <div>
          <div class="font-bold">{{ person.name }}</div>
          <div class="text-sm opacity-50">{{ person.country }}</div>
        </div>
      </div>
    </td>
    <td class="text-center">
      {{ person.company }}
      <br />
      <span class="badge badge-ghost badge-sm">{{ person.job }}</span>
    </td>
    <td class="w-5 text-center">
      <span
        class="rounded-full badge badge-sm"
        :style="{ backgroundColor: person.color }"
      ></span>
      {{ consoleReRender() }}
    </td>
  </tr>
</template>
