<template>
	<form @submit.prevent="onSubmit">
		<div class="form-group my-2">
			<label for="username">Username</label>
			<input
				v-model="form.username"
				class="form-control"
				placeholder="Username"
				required
			/>
		</div>
		<div class="form-group my-2">
			<label for="password">Password</label>
			<input
				v-model="form.username"
				class="form-control"
				type="password"
				placeholder="Password"
				required
			/>
		</div>
		<div class="text-danger my-2">{{ userStore.state.error }}</div>
		<button class="btn btn-success btn-block my-2" type="submit">login</button>
	</form>
</template>

<script lang="ts">
import { reactive, defineComponent } from "vue";
import userStore from "../stores/user";

export default defineComponent({
	setup() {
		const form = reactive({ username: "", password: "" });

		const onSubmit = () => {
			userStore.login(form.username, form.password);
			form.username = "";
			form.password = "";
		};

		return { form, onSubmit, userStore };
	},
});
</script>
