<template>
  <div>
    <q-card>
      <q-card-section>
        <div class="text-h6">My Goals</div>
      </q-card-section>

      <q-card-section class="q-pt-none">
        <q-input
          v-model="goalWeightEntry.goalWeight"
          type="number"
          style="max-width: 200px"
          label="Enter Goal Weight"
          :value="goalWeightEntry.goalWeight"
        />
      </q-card-section>
      <q-card-section class="q-pt-none">
        <q-input
          v-model="goalWeightEntry.goalDate"
          :value="goalWeightEntry.goalWeight"
          mask="date"
          :rules="['date']"
          label="Enter Goal Date"
        >
          <template v-slot:append>
            <q-icon name="event" class="cursor-pointer">
              <q-popup-proxy ref="qDateProxy" transition-show="scale" transition-hide="scale">
                <q-date v-model="goalWeightEntry.goalDate" :value="goalWeightEntry.goalWeight">
                  <div class="row items-center justify-end">
                    <q-btn v-close-popup label="Close" color="primary" flat />
                  </div>
                </q-date>
              </q-popup-proxy>
            </q-icon>
          </template>
        </q-input>
      </q-card-section>
      <q-card-actions align="right">
        <q-btn @click="submitEntry" label="Enter" color="primary" v-close-popup />
      </q-card-actions>
    </q-card>
  </div>
</template>


<script>
import moment from "moment";
import { mapActions } from "vuex";

export default {
  data() {
    return {
      goalWeightEntry: {
        goalWeight: this.goals.goalWeight,
        goalDate: this.goals.goalDate,
      },
    };
  },
  props: ["goals"],
  methods: {
    ...mapActions("weight", ["updateGoals"]),

    submitEntry() {
      this.updateGoals(this.goalWeightEntry);
      //   console.log(this.goalWeightEntry.goalWeight, "< weight");
      //   console.log(this.goalWeightEntry.goalDate, "< Date");
      //   console.log(this.goalWeightEntry);
    },
  },
};
</script>

