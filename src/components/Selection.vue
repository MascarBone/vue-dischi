<template>
  <select name="" id="">
      <option @click="$emit('selection', element)" v-for="(element, index) in list" :key="index" value="">{{element}}</option>
  </select>
</template>

<script>
export default {
    name: 'Selection',



    props: {
        list: Array,
    },

    methods: {
        change (el) {
            console.log('change it');
            console.log(el)
        }
    }
}
</script>

<style>

</style>