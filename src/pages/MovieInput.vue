<template>
  <q-page padding class="items-center-justify-center bg-grey-3">
    <q-card flat class="bg-white q-pa-md">
      <span class="text-h5 text-weight-light q-pa-md">
        <span class="text-blue-grey-14">Movie Input</span>
      </span>

      <div class="q-pa-md">
        <q-form class="q-gutter-md">
          <div class="row">
            <q-space />
            <q-btn round label="D" color="negative" @click="delMovie" />
            <q-btn round label="S" color="secondary" @click="addMovie" />
          </div>
          <q-input
            label="Title"
            lazy-rules
            color="secondary"
            v-model="movTitle"
            :rules="[
              (val) => (val !== null && val !== '') || 'Title Required!',
            ]"
          >
            <template v-slot:append>
              <q-icon name="title" />
            </template>
          </q-input>

          <q-input
            label="Director"
            lazy-rules
            color="secondary"
            v-model="movDir"
            :rules="[
              (val) => (val !== null && val !== '') || 'Director Required!',
            ]"
          >
            <template v-slot:append>
              <q-icon name="person" />
            </template>
          </q-input>

          <q-input
            label="Summary"
            lazy-rules
            color="secondary"
            v-model="movSum"
          >
            <template v-slot:append>
              <q-icon name="summarize" />
            </template>
          </q-input>

          <q-input label="Genre" lazy-rules color="secondary" v-model="movGen">
            <template v-slot:append>
              <q-icon name="summarize" />
            </template>
          </q-input>
        </q-form>
      </div>
    </q-card>
  </q-page>
</template>

<script>
import { ref } from "vue";
import { useQuasar } from "quasar";

export default {
  name: "MovieInput",

  setup() {
    const movTitle = ref(null);
    const movDir = ref(null);
    const movSum = ref(null);
    const movGen = ref(null);
    const edit = ref(false);
    const $q = useQuasar();

    return {
      movTitle,
      movDir,
      movSum,
      movGen,
      edit,

      addMovie() {
        // console.log(this.movTitle);
        if (edit.value === false) {
          // add new movie
          // const movies = []
          const newMovie = {
            movTitle: movTitle.value,
            movDir: movDir.value,
            movSum: movSum.value,
            movGen: movGen.value,
            id: Math.floor(Math.random() * 100),
          };

          // const oldMovie = $q.localStorage.getItem("newMov");
          // const movies = [newMovie, oldMovie];
          //console.log(movies);

          $q.localStorage.set("newMov", newMovie);
        } else {
          //edit movie
        }
      },
    };
  },
};
</script>

<style scoped></style>
