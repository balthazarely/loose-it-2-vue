<template>
  <q-card bg-variant="light" class="shadow-1" flat bordered>
    <q-item-label header>All Weight Loss</q-item-label>
    <div id="chart-1" style="height: 370px; background: white">
      <line-chart :data="sortedEntriesChart" :colors="['#f5881e', '#666']" class="q-pa-md" />
    </div>
  </q-card>
</template>

<script>
import { mapGetters } from "vuex";

export default {
  props: ["sortedEntriesChart"],
  data() {
    return {};
  },
  //   computed: {
  //     ...mapGetters(["sortedEntriesChart"]),
  //   },
};
</script>