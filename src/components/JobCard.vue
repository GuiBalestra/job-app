<template>
  <div>
    <b-col>
      <b-card
        :title="name"
        img-src="https://picsum.photos/600/300/?image=25"
        img-alt="Job-info"
        img-top
        tag="article"
        style="max-width: 20rem"
        class="mb-2"
        footer="Card Footer"
      >
        <b-card-text>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Atque, minus.
        </b-card-text>
        <b-button
          v-b-modal="modalId"
          variant="primary"
          v-b-tooltip.hover
          title="Apply Here"
          >Apply</b-button
        >
        <b-modal :id="modalId" title="Apply here info">
          <p class="my-4">Hello from modal</p>
        </b-modal>
      </b-card>
    </b-col>
  </div>
</template>

<script>
export default {
  props: {
    name: String,
    id: Number
  },
  computed: {
    modalId() {
      return `modal-${this.id}`;
    }
  }
};
</script>

<style></style>
