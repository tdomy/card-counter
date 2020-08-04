<template>
  <div class="has-background-grey-darker has-text-white has-text-right px-2 py-2 mt-4 mb-5">
    <p class="is-size-4">Remaining Cards: {{ remaining }}</p>
    <p class="is-size-1 has-text-weight-bold">{{ count }}</p>
  </div>
</template>

<script>
export default {
  name: 'DispCount',
  props: ['remaining', 'count']
}
</script>
