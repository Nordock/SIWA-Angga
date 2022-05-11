<template>
  <div class="q-pa-md">
    <q-table
      grid
      title="Movies"
      :rows="movies"
      :columns="columns"
      row-key="name"
      :filter="filter"
      hide-header
    >
      <template v-slot:top-right>
        <q-input
          borderless
          dense
          debounce="300"
          v-model="filter"
          placeholder="Search"
        >
          <template v-slot:append>
            <q-icon name="search" />
          </template>
        </q-input>
      </template>
    </q-table>
    <div class="row">
      <q-space />
      <q-btn round icon="add" label="" color="secondary" to="movieinput" />
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
import { useQuasar, LocalStorage } from "quasar";

const $q = useQuasar();
const columns = [
  {
    name: "title",
    label: "",
    align: "left",
    field: "movTitle",
  },
  {
    name: "director",
    label: "",
    align: "left",
    field: "movDir",
  },
  { name: "genre", label: "", align: "right", field: "movGen" },
];

const movies = [
  // $q.localStorage.getItem("newMov"),
  // {
  //   id: 1,
  //   title: "Power Ranger",
  //   director: "Dean Esraelite",
  //   summary: "bla bla",
  //   genre: "Action/Sci-fi",
  // },
  // {
  //   id: 2,
  //   title: "Frozen",
  //   director: "Chris Buck",
  //   summary: "bla bla",
  //   genre: "Animation",
  // },
  // {
  //   id: 3,
  //   title: "The Godfather",
  //   director: "Francis Ford Coppola",
  //   summary: "bla bla",
  //   genre: "Drama",
  // },
];

export default {
  name: "IndexPage",

  setup() {
    return {
      filter: ref(""),
      columns,
      movies: ref([LocalStorage.getItem("newMov")]),
    };
  },
};
</script>
