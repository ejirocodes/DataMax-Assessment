<template>
  <v-app>
    <v-main>
      <Dashboard />
    </v-main>
  </v-app>
</template>

<script>
import Dashboard from "./pages/dashboard";

export default {
  name: "App",

  components: {
    Dashboard,
  },

};
</script>
<style>
@import url("https://fonts.googleapis.com/css2?family=Lato:wght@400;700&display=swap");
.v-application {
  font-family: "Lato", sans-serif !important;
}
.v-sheet.v-card:not(.v-sheet--outlined) {
  box-shadow: none !important;
}
.v-data-table {
  border: 1px solid #dddddd;
  box-shadow: none !important;
  transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
}
.card-table {
  margin: 4rem 0 5rem !important;
}
.v-btn__content {
  text-transform: none;
  font-size: 11px;
}
.v-btn {
  padding: 15px 25px !important;
}
.text-start {
  padding: 20px 17px !important;
}
.v-data-table > .v-data-table__wrapper > table > tbody > tr > th,
.v-data-table > .v-data-table__wrapper > table > thead > tr > th,
.v-data-table > .v-data-table__wrapper > table > tfoot > tr > th {
  font-size: .9rem !important;
}
th {
  border-top: 1px solid #dddddd;
}

.theme--light.v-data-table
  > .v-data-table__wrapper
  > table
  > tbody
  > tr:hover:not(.v-data-table__expanded__content):not(.v-data-table__empty-wrapper) {
  background: #dbdbdb !important;
}
.loader {
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  z-index: 122;
}
tbody tr:nth-of-type(odd) {
  background-color: rgba(0, 0, 0, 0.05) !important;
}
</style>