<template>
  <div id="app">
    <HomeComponent :stages="report" :blocks="blocks" @delete-task="deleteTask"/>
  </div>
</template>

<script>
import '../public/assets/style.scss'
import HomeComponent from "./components/HomeComponent.vue";
export default {
  name: "App",
  components: {
    HomeComponent,
  },
  data() {
		return {
			report: ['new-order', 'in-progress', 'waiting-for-buyer', 'completed'],
			blocks: [
				{
					id: 1,
					status: 'new-order',
					title: 'New order',
					productImage: '/assets/1.jpg',
					time: '5 days left',
					hour: '20 hrs',
					price: '$320',
				},
				{
					id: 2,
					status: 'new-order',
					title: 'New order',
					productImage: '/assets/1.jpg',
					time: '3 days left',
					hour: '4 hrs',
          			fprice: '$85'
				},
				{
					id: 3,
					status: 'in-progress',
					title: 'In Progress',
					productImage: '/assets/3.jpg',
					time: 'Due in 2 days, 5hrs',
					hour: '5 hrs',
          			price: '$155'
				},
				{
					id: 4,
					status: 'in-progress',
					title: 'In Progress',
					productImage: '/assets/4.jpg',
					time: 'Due in 3 days, 5hrs',
					hour: '8 hrs',
          			price: '$385'
				},
				{
					id: 5,
					status: 'waiting-for-buyer',
					title: 'Delivered',
					productImage: '/assets/2.jpg',
					time: '3 days left',
					hour: '3 hrs',
          			price: '$385'
				},
				{
					id: 6,
					status: 'completed',
					title: 'Completed',
					productImage: '/assets/4.jpg',
					time: 'Dec 12, 9:43pm',
          			hour: '8 hrs',
					price: '$346',
				},
				{
					id: 7,
					status: 'completed',
					title: 'Completed',
					productImage: '/assets/3.jpg',
					time: 'Dec 13, 8:21pm',
          			hour: '6 hrs',
					price: '$320',
				},
				{
					id: 8,
					status: 'completed',
					title: 'Cancelled',
					productImage: '/assets/3.jpg',
					time: 'Dec 12, 9:43pm',
          			hour: '20 hrs',
					price: '$385',
				},
			],
		}
	},
  methods: {
    deleteTask(id) {
      this.blocks = this.blocks.filter(item =>item.id !== id);
      alert('Task Removed Successfully')
    }
  }
};
</script>
