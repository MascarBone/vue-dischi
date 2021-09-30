<template>
  <select name="" id="">
      <option v-for="(element, index) in list" :key="index" value="">{{element}}</option>
  </select>
</template>

<script>
export default {
    name: 'Selection',

    props: {
        list: Array,
    },
}
</script>

<style>

</style>