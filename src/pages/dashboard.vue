<template >
  <v-container class="dashboard">
    <PreLoader v-if="isLoading" />
    <v-card class="card-table">
      <v-row class="px-4 pt-4 pb-2">
        <v-spacer></v-spacer>
        <v-col cols="12" md="3">
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
        <template v-slot:[`item.released`]="{ item }">
          <span>{{
            new Date(item.released).getDate() +
            " " +
            new Date(item.released).toLocaleString("default", {
              month: "short",
            }) +
            ", " +
            new Date(item.released).getFullYear()
          }}</span>
        </template>
      </v-data-table>
      <v-snackbar v-model="isError" :timeout="2000" top right color="red" elevation="0">
        {{ message }}

        <template v-slot:action="{ attrs }">
          <v-btn color="black" text v-bind="attrs" @click="isError = false" >
            Close
          </v-btn>
        </template>
      </v-snackbar>
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
        { text: "Name", value: "name", divider: true },
        {
          text: "ISBN",
          align: "start",
          sortable: true,
          value: "isbn",
          divider: true,
        },
        { text: "Authors", value: "authors", divider: true },
        { text: "Country", value: "country", divider: true },
        { text: "Released", value: "released", divider: true },
      ],
      books: [],
      isLoading: true,
      isError: false,
      message: "",
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
        this.books = data;
        this.isLoading = false;
      } catch (error) {
        this.isError = true;
        this.message = error
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