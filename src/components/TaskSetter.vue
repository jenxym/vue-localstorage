<template>
	<v-container>
		<h2 class=".title mt-3">Add a new task</h2>
		<v-card flat class="pa-4 grey lighten-4">
			<v-form v-model="valid" ref="form">
				<v-text-field outlined required v-model="taskData.taskName" :rules="nameRules" label="Add a title"></v-text-field>
				<v-text-field outlined required v-model="taskData.taskInfo" :rules="infoRules" label="Add a short description"></v-text-field>
				<v-btn depressed tile large color="success" @click="addTask"><v-icon>mdi-plus</v-icon>Add task</v-btn>
			</v-form>
		</v-card>
	</v-container>
</template>

<script>
import { EventBus } from '@/events/event-bus.js';
export default {
	data() {
		return {
			valid: false,
			nameRules: [(v) => !!v || 'A task name is required', (v) => /^[a-zA-Z0-9 ]+$/.test(v) || 'Only alphanumerics characters'],
			infoRules: [(v) => !!v || 'A task description is required', (v) => /^[a-zA-Z0-9 ]+$/.test(v) || 'Only alphanumerics characters'],
			taskData: {
				taskName: '',
				taskInfo: '',
			},
		};
	},
	methods: {
		addTask() {
			if (!this.$refs.form.validate()) return;
			EventBus.$emit('addtask', this.taskData);
			this.taskData = {};
			this.$refs.form.reset();
		},
	},
};
</script>

<style></style>
