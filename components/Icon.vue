<!-- Icons from https://heroicons.com/ -->
<template>
  <svg xmlns="http://www.w3.org/2000/svg" fill="currentColor" viewBox="0 0 19 19" v-html="getSVG(name)"></svg>
</template>
<script>
import { defineComponent, ref } from "vue";
import OutlineIcons from "../outline";
import SolidIcons from "../solid";
export default defineComponent({
  name: "Icon",
  props: {
    name: { type: String, default: "annotation", required: true },
    solid: { type: Boolean, default: false },
  },
  methods: {
    getSVG(name) {
      let path='';
      let fill='';
      if (!(name in SolidIcons || name in OutlineIcons)){
        path = SolidIcons['OneTwoThree'];
        fill = 'fill="currentColor" viewBox="0 0 19 19"';
      }else{
        if (this.solid) {
          path = SolidIcons[name];
          fill = 'fill="currentColor" viewBox="0 0 19 19"';
        }else{
          path = OutlineIcons[name];
          fill = 'fill="none" stroke="currentColor" viewBox="0 0 19 19"';
        }
      }
      const svg = `<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="${path}" />`;
      return svg;
    },
  },
});
</script>

<style></style>
