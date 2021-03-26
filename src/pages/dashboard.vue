<template >
  <v-container class="dashboard">
    <PreLoader v-if="isLoading" />

    <v-card class="card-table">
      <v-row class="px-4 pt-4 pb-2">
        <v-spacer></v-spacer>
        <v-col cols="12" md="4">
          <v-text-field
            v-model="search"
            outlined
            single-line
            dense
            hide-details
            append-icon="mdi-magnify"
            label="Search for Books..."
            class="ma-2"
          ></v-text-field>
        </v-col>
      </v-row>
      <v-data-table
        :headers="headers"
        :items="books"
        :items-per-page="10"
        :search="search"
      >
      </v-data-table>
    </v-card>
  </v-container>
</template>
<script>
import PreLoader from "../components/PreLoader";

export default {
  data() {
    return {
      search: "",
      headers: [
        { text: "Name", value: "name" },
        {
          text: "ISBN",
          align: "start",
          sortable: true,
          value: "isbn",
        },
        { text: "Authors", value: "authors" },
        { text: "Pages", value: "email" },
        { text: "Country", value: "country" },
        { text: "Released", value: "released" },
      ],
      books: [],
      isLoading: true,
    };
  },
  components: {
    PreLoader,
  },
  methods: {
    async getBooks() {
      try {
        const res = await fetch(
          `https://www.anapioficeandfire.com/api/books?pageSize=12`
        );
        const data = await res.json();
        console.log({ data });
        this.books = data;
        this.isLoading = false;
      } catch (error) {
        console.log(error);
      }
    },
  },
  mounted() {
    this.getBooks();
  },
};
</script>
<style>
</style>