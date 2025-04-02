<script lang="ts">
    export default {
      name:'Person',
    }
</script>

<template>
  <Button type="primary">123</Button>
</template>

<script setup lang="ts">
import {Button} from 'ant-design-vue'

</script>

<style>
 .person {
    background-color: skyblue;
    box-shadow: 0 0 10px;
    border-radius: 10px;
    padding: 20px;
  }
  button {
    margin: 0 5px;
  }
</style>