<template>
  <svg ref="container" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512" />
</template>

<script>
import iconsList from "@/assets/svg/icons.json";

export default {
  name: "Icons",
  props: {
    name: {
      type: String,
      required: true,
    },
  },
  mounted: function () {
    //take the reference to the SVG tag and use the return of filter function to build the html inside it
    this.$refs.container.innerHTML = this.filterIcon(this.name);
  },
  methods: {
    filterIcon: (name) => {
      //filter the icons JSON, the JSON contains the code to use inside the SVG tag
      const icon = iconsList.filter((item) => item.name === name);
      return icon[0].code;
    },
  },
};
</script>

<style>
</style>