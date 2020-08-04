<template>
  <button
    class="button is-large is-fullwidth mb-3"
    v-on:click="$emit('click')"
    v-bind:disabled="disabled"
  >
    <slot />
  </button>
</template>

<script>
export default {
  name: 'CountButton',
  props: ['disabled']
}
</script>
