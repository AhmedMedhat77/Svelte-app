<script>
	import { createEventDispatcher } from 'svelte';
	// not recomended to pass function as prop
    // export let filterUsers;

	//  recomended way to dispatch event
	const dispatch = createEventDispatcher();
	const filterFunction = (e) => {
		const { value } = e.target;
		// dispatch event
		dispatch('filter', value);
	};
</script>

<div class="ml-4 mt-4">
	<label for="user-filter">Filter Users</label>
	<select
		name="user-filter"
		id="user-filter"
		class="border rounded-lg px-4 py-2 ml-4"
		on:change={filterFunction}
	>
		<option default value={'null'}>ALL</option>
		<option value={'true'}>Active</option>
		<option value={'false'}>In-active</option>
	</select>
</div>
