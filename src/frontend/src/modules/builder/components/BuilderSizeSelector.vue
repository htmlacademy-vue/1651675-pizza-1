<template>
  <div class="content__diameter">
    <div class="sheet">
      <h2 class="title title--small sheet__title">Выберите размер</h2>

      <RadioButton
        :arrayData="diameter"
        nameInput="diameter"
        classesNameComponent="sheet__content diameter"
        classesNameLabel="diameter__input diameter__input--"
        @updateData="
          (newValue) => {
            updateData(newValue, 'diameter', 'foundation');
          }
        "
      />
    </div>
  </div>
</template>

<script>
import RadioButton from "@/common/components/RadioButton.vue";

export default {
  name: "BuilderSizeSelector",

  components: {
    RadioButton,
  },

  computed: {
    diameter() {
      return this.$store.getters["Builder/diameter"];
    },
  },

  methods: {
    updateData(argValue, argName, argType) {
      this.$store.dispatch("Builder/updatePizzaBuilder", {
        type: argType,
        name: argName,
        value: argValue,
      });
    },
  },
};
</script>

<style></style>
