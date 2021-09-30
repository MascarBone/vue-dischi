<template>
  <select name="" id="">
      <option @click="$emit('author-selection',element)" v-for="(element, index) in list" :key="index" value="">{{element}}</option>
  </select>
</template>

<script>
export default {
    name: 'SelectionAuthor',

    props: {
        list: Array,
    }
}
</script>

<style lang="scss" scoped>

    select {
        margin: 50px 0;
    }

</style>