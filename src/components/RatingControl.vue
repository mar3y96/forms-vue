<template>
  <ul>
    <li :class="{ active: activeOption == 'poor' }"><button name="rating" type="button" value="poor"
        @click="activate('poor')">Poor</button></li>
    <li :class="{ active: activeOption == 'average' }"><button name="rating" type="button" value="average"
        @click="activate('average')">Average</button></li>
    <li :class="{ active: activeOption == 'great' }"><button name="rating" type="button" value="great"
        @click="activate('great')">Great</button></li>
  </ul>
</template>

<script>
export default {
  props:['modelValue'],
  emits:['update:modelValue'],
  data() {
    return {
      // activeOption: this.modelVaue
    };
  },
  computed:{
    activeOption(){
      return this.modelValue;
    }
  },
  methods: {
    activate(option) {
      this.activeOption = option;
      this.$emit('update:modelValue',option)
    }
  },
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0.5rem 0;
  padding: 0;
  display: flex;
}

li {
  margin: 0 1rem;
  border: 1px solid #ccc;
  padding: 1rem;
  display: flex;
  justify-content: center;
  align-items: center;
}

button {
  font: inherit;
  border: none;
  background-color: transparent;
  cursor: pointer;

}

.active {
  border-color: #a00078;
  background-color: rgb(219, 246, 83);
}

.active button {
  color: #a00078;
}
</style>