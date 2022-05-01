<template>
  <b-dropdown :text="buttonTitle">
    <b-form-group v-slot="{ ariaDescribedby }">
      <b-form-checkbox
        v-for="choice in buttonChoices"
        :key="choice.value"
        v-model="selected"
        :value="choice.value"
        :aria-describedby="ariaDescribedby"
        name="flavour-3a"
        @change="tryFilter"
      >
        {{ choice.text }}
      </b-form-checkbox>
    </b-form-group>
  </b-dropdown>
</template>

<script>
export default {
  name: "Filters",
  props: {
    buttonTitle: String,
    tabColumn: String,
    buttonSelections: String,
  },
  data() {
    return {
      buttonChoices: [
        {
          text: "Active",
          value: "Active",
        },
        {
          text: "Terminated",
          value: "Terminated",
        },
      ],
      selected: [],
    };
  },
  created() {
    this.buttonChoices = JSON.parse(this.buttonSelections);
  },
  mounted() {
    this.tryFilter();
  },
  methods: {
    tryFilter() {
      console.log(this.selected);
      this.$emit("send-to-parent", this.selected);
    },
  },
};
</script>
