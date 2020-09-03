<template>
  <div class="q-pa-md row items-start q-gutter-md">
    <q-card class="my-card" flat bordered>
      <q-item>
        <q-item-section avatar>
          <q-avatar>
            <img src="https://cdn.quasar.dev/img/boy-avatar.png" />
          </q-avatar>
        </q-item-section>

        <q-item-section>
          <q-item-label>Dave Powers</q-item-label>
          <q-item-label caption>dave@gmail.com</q-item-label>
        </q-item-section>

        <q-item-section class="absolute-right q-mr-md">
          <q-btn round color="primary" icon="edit" size=".7rem" @click="showAddTask = true" />
        </q-item-section>
      </q-item>
      <q-dialog v-model="showAddTask">
        <AddProfileModal :goals="goals" />
      </q-dialog>

      <q-separator />
      <div class="row">
        <div class="col-4 q-pa-sm">
          <q-item-label caption>Start Weight:</q-item-label>
          <q-card-section>
            <div class="text-h5 ellipsis text-primary text-weight-bolder">
              {{startWeight[1]}}
              <span
                class="text-h6 ellipsis text-grey-5 text-weight-medium 1-ml-0"
              >lbs.</span>
            </div>
          </q-card-section>
        </div>
        <div class="col-4 q-pa-sm">
          <q-item-label caption>Start Date:</q-item-label>
          <q-card-section>
            <div
              class="text-h6 ellipsis text-primary text-weight-bolder"
            >{{startWeight[0] | formatDate}}</div>
          </q-card-section>
        </div>
        <div class="col-4 q-pa-sm">
          <q-item-label caption>Current Weight:</q-item-label>
          <q-card-section>
            <div class="text-h5 ellipsis text-primary text-weight-bolder">
              {{currentWeight}}
              <span
                class="text-h6 ellipsis text-grey-5 text-weight-medium 1-ml-0"
              >lbs.</span>
            </div>
          </q-card-section>
        </div>
        <q-separator />
        <div class="col-6 q-pa-sm">
          <q-item-label caption>Goal Weight:</q-item-label>
          <q-card-section>
            <div class="text-h5 ellipsis text-primary text-weight-bolder">
              {{goals.goalWeight}}
              <span
                class="text-h6 ellipsis text-grey-5 text-weight-medium 1-ml-0"
              >lbs.</span>
            </div>
          </q-card-section>
        </div>
        <div class="col-6 q-pa-sm">
          <q-item-label caption>Goal Date:</q-item-label>
          <q-card-section>
            <div
              class="text-h6 ellipsis text-primary text-weight-bolder"
            >{{goals.goalDate | formatDate}}</div>
          </q-card-section>
        </div>
      </div>
    </q-card>
  </div>
</template>

<script>
import moment from "moment";

export default {
  data() {
    return {
      showAddTask: false,
    };
  },
  components: {
    AddProfileModal: require("components/Modals/AddProfileModal.vue").default,
  },
  props: ["goals", "currentWeight", "startWeight"],
  filters: {
    formatDate: function (value) {
      if (value) {
        let data = moment(value).format("MMM Do");
        return data;
      }
    },
  },
};
</script>


<style scoped lang="sass">
.my-card
  width: 600px
</style>

