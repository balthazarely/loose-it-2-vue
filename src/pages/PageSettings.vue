<template>
  <q-page class="q-pa-md bg-grey-2">
    <h5
      class="subtitle text-weight-light"
    >Hi Dave, you have {{ goals.goalDate | createCountdown }} days left to reach your goal!</h5>
    <ProfileCard :goals="goals" :currentWeight="CurrentWeight" :startWeight="StartWeight" />
    <Macros />
  </q-page>
</template>

<script>
import { mapGetters } from "vuex";
import moment from "moment";

export default {
  components: {
    ProfileCard: require("components/Cards/ProfileCard.vue").default,
    Macros: require("components/Macros.vue").default,
  },
  computed: {
    ...mapGetters("weight", ["goals", "CurrentWeight", "StartWeight"]),
  },
  filters: {
    createCountdown(value) {
      let eventdate = moment(value);
      let todaysdate = moment();
      return eventdate.diff(todaysdate, "days");
    },
  },
};
</script>

<style>
</style>

