<template id="front">
  <b-container style="margin-top: 9rem">
    <b-row>
      <b-col>
        <filters
          @send-to-parent="updateParentFromChildren"
          :button-title="filterData[0].buttonTitle"
          :tab-column="filterData[0].tabColumn"
          :button-selections="filterData[0].buttonSelections"
        ></filters>
      </b-col>
    </b-row>
    <div>current selected options: {{ selectedOptionsInFiltersComponent }}</div>
  </b-container>
</template>

<script>
import Filters from "./Filters";

export default {
  name: "TM",
  components: {
    Filters,
  },
  data() {
    return {
      selectedOptionsInFiltersComponent: [],
      filterData: [
        {
          buttonTitle: "Status",
          tabColumn: "Employee_Status",
          buttonSelections:
            '[{"text":"Active","value":"Active"},{"text":"Terminated","value":"Terminated"}]',
        },
      ],
    };
  },
  methods: {
    updateParentFromChildren(selectedElements) {
      this.selectedOptionsInFiltersComponent = selectedElements;
    },
  },
};
</script>