<template>
  <div class="list">
    <li class="list-item" v-for="(item, index) in list" :key="index">
      {{ item.name }}
    </li>
  </div>
</template>

<script>
export default {
  name: 'list',

  props: ['list']
}
</script>
