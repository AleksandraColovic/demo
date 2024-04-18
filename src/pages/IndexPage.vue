<template>
  <q-page class="q-pa-lg">
    <q-table
      style="height: 400px"
      flat
      bordered
      title="Packaging Orders"
      :rows="rows"
      :columns="columns"
      row-key="index"
      virtual-scroll
    />
  </q-page>
</template>

<script setup>
import { onMounted, ref } from "vue";
import { api } from "boot/axios";

const columns = [
  {
    name: "id",
    label: "ID",
    field: "id",
  },
  {
    name: "externalReferenceId",
    required: true,
    label: "External Reference",
    align: "left",
    field: "externalReferenceId",
    format: (val) => `${val}`,
    sortable: true,
  },
  {
    name: "quantity",
    align: "center",
    label: "Quantity",
    field: "quantity",
    sortable: true,
  },
  { name: "location", label: "Location", field: "location", sortable: true },
];

const seed = [];
const rows = ref([]);

onMounted(() => {
  api
    .get("http://localhost:7575/api/packagingOrder")
    .then((response) => {
      console.log(response.data);
      rows.value = response.data;
    })
    .catch((error) => {
      console.log(error);
    });
});

// we generate lots of rows here
/* let rows = [];
for (let i = 0; i < 1000; i++) {
  rows = rows.concat(seed.slice(0).map((r) => ({ ...r })));
}
rows.forEach((row, index) => {
  row.index = index;
}); */

/* export default {
  setup() {
    return {
      columns,
      rows,

      pagination: ref({
        rowsPerPage: 1000,
      }),
    };
  },
  mounted: {
    loadData() {
      axios
        .get("/api/packagingOrder")
        .then((response) => {
          console.log(response.data);
          this.seed = response.data;
        })
        .catch(() => {
          this.$q.notify({
            color: "negative",
            position: "top",
            message: "Loading failed",
            icon: "report_problem",
          });
        });
    },
  },
}; */
</script>
