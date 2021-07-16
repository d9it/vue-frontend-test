<template>
  <div>
    <div class="container">
      <div class="box_1" v-for="(stage , index) in stages" :key="index">
        <slot :name="stage">
          <h2>{{ stage }}</h2>
        </slot>
        <ProductTask  v-for="block in fetchBlocks(stage)" :key="block[idProp]" :task="block" @remove-task="updateBlock"></ProductTask>
      </div>
    </div>
  </div>
</template>

<script>
import ProductTask from './ProductTask.vue'
export default {
  name: "HomeComponent",
  props: {
    stages: {
      type: Array,
      required: true,
    },
    blocks: {
      type: Array,
      required: true,
    },
    statusProp: {
      type: String,
      default: 'status',
    },
    idProp: {
      type: String,
      default: 'id',
    },
  },
  components: {
    'ProductTask': ProductTask
  },
  computed: {
    currentBlocks() {
      return this.blocks;
    },
  },
  methods: {
    fetchBlocks(status) {
      return this.currentBlocks.filter(block => block[this.statusProp] === status);
    },
    updateBlock(id) {
      console.log('212121', id);
      this.$emit('delete-task', id);
    }
  }
};
</script>
