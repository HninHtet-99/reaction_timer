<template>

  <p>Result : {{score}} ms</p>

  <div v-if="score < 250">
    <h4>you are too fast! 0_0</h4>
  </div>
  <div v-else-if="score >= 250 && score < 600 ">
    <h4>you are normal! :)</h4>
  </div>
  <div v-else>
    <h4>you are too slow! try again :(</h4>
  </div>

</template>

<script>
export default {
    props: ["score"]
}
</script>

<style>

</style>