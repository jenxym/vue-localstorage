<template>
	<div class="list">
		<v-container>
			<h2 class=".title mt-3 mb-2">All your taks</h2>
			<v-card v-for="(item, index) in tasks" :key="item.taskName" tile class="mb-2 d-flex justify-space-between">
				<div>
					<v-card-title>{{ item.taskName }}</v-card-title>
					<v-card-text>{{ item.taskInfo }}</v-card-text>
				</div>
				<v-card-actions>
					<v-btn text color="error" @click="deleteTask(index)"><v-icon>mdi-delete</v-icon>Delete</v-btn>
				</v-card-actions>
			</v-card>
		</v-container>
	</div>
</template>

<script>
import { EventBus } from '@/events/event-bus.js';

export default {
	data() {
		return {
			tasks: [],
		};
	},
	mounted() {
		EventBus.$on('addtask', (data) => {
			this.tasks.push(data);
			this.updateLocalData();
		});
	},
	methods: {
		deleteTask(index) {
			this.tasks.splice(index, 1);
			this.updateLocalData();
		},
		updateLocalData() {
			localStorage.setItem('local-tasks', JSON.stringify(this.tasks));
		},
	},
	created() {
		let localTasks = JSON.parse(localStorage.getItem('local-tasks'));
		if (localTasks) this.tasks = localTasks;
	},
};
</script>

<style></style>
