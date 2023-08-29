<script>
	import { users, remove, addNewUser } from '../../Store';
	import FilterUser from '../FilterUser/FilterUser.svelte';
	import NewUser from '../NewUser/NewUser.svelte';
	import SingleUser from '../SingleUser/SingleUser.svelte';

	$: filterdUsers = $users;

	const filterUsers = (e) => {
		const value = e.detail;
		if (value === 'null') {
			filterdUsers = $users;
			return;
		}

		filterdUsers = $users.filter((user) => user.active === value);
	};
</script>

<section>
	<h1 class="text-2xl text-center mt-10">Users List</h1>
	<!-- Filter Component -->
	<div class="flex justify-between items-center">
		<FilterUser on:filter={filterUsers} />
		<NewUser on:newUser={addNewUser} />
	</div>
	<div>
		{#each filterdUsers as user, i (user.id)}
			<SingleUser on:remove={remove} {i} {user} />
		{:else}
			<p>No Users To Be Shown</p>
		{/each}
	</div>
	<div />
</section>

<style>
</style>
