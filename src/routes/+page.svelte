<script lang="ts">
	import { enhance } from "$app/forms";
	import type { PageData } from "./$types";

	export let data: PageData;
	console.log(data.user);
	async function getUserDetails() {
		const response = await fetch(`https://api.github.com/users/${data.user.username}`);
		const details = await response.json();
		console.log(details);
	}
	getUserDetails();
</script>

<h1>Hi, {data.user.username}!</h1>
<p>Your user ID is {data.user.id}.</p>
<form method="post" use:enhance>
	<button>Sign out</button>
</form>
