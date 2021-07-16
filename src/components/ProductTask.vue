<template>
  <div>
      <div class="card">
        <div class="inner_card">
            <div class="icon_delete">
              <a href="javascript:void(0)" @click="removeTask(task.id)">
                <img src="/assets/menu.png" alt="" title="">
              </a>
            </div>
            <div class="product_div">
              <div class="product_img">
                <img :src="task.productImage" alt="" title="">
              </div>
              <div class="product_detail">
                  <label :class="fetchClass(task.status)">{{ task.title }}</label>
                  <p v-if="task.status !== 'completed'"><img src="/assets/clock.png" alt="" title=""> {{ task.time }}</p>
                  <p v-else>{{ task.time }}</p>
                  <p>{{ task.hour}} | <span class="price"><b>{{ task.price}}</b></span></p>
              </div>
            </div>
        </div>
        <hr/>
        <div class="inner_card pt-0">
            <h2><a href="javascript:void(0)">View Order</a></h2>
            <div class="float-right">
              <div class="user_img">
                <a href="javascript:void(0)"><img src="/assets/user1.jpg" alt="" title=""></a>
              </div>
              <a href="javascript:void(0)"><img src="/assets/chat.png" alt="" title="" style="width:30px"></a>
            </div>
        </div>
      </div>
  </div>
</template>

<script>
export default {
  props: {
    task: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      productBackgroundcolor: [
        { 
          name:'new-order',
          class: 'bg_yellow' 
        },
        { 
          name:'in-progress', 
          class: 'bg_blue' 
        },
        { 
          name:'waiting-for-buyer', 
          class: 'bg_pink' 
        },
        { 
          name:'completed',
          class: 'bg_green' 
        },
      ]
    }
  },
  methods: {
    fetchClass(status) {
      const className = this.productBackgroundcolor.filter(colorClass => colorClass.name === status);
      return className[0].class;
    },
    removeTask(id) {
      if(confirm("Are you sure you want to remove task ?")){
        this.$emit('remove-task', id); // Emit to parent element.
      }
    }
  }
}
</script>