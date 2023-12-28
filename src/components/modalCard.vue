<template>
  <div>
    <b-button id="show-btn" @click="showModal">Open Modal</b-button>

    <b-modal ref="my-modal">
      <div class="d-block text-center">
        <h3>Hello From My Modal!</h3>
      </div>
    </b-modal>
  </div>
</template>

<script>
  export default {
    methods: {
      showModal() {
        this.$refs['my-modal'].show()
      },
      hideModal() {
        this.$refs['my-modal'].hide()
      },
    }
  }
</script>