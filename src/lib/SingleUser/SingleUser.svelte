<script>
	import { createEventDispatcher } from 'svelte';
	import { slide, fly } from 'svelte/transition';
	// defining the props
	export let user;
	export let i;
	// distructing props from user prop
	export let { userName, userEmail, image, id } = user;
	const dispatch = createEventDispatcher();
	// dispatching event to be custom function prop
	const remove = () => {
		dispatch('remove', id);
	};
</script>

<div
	transition:fly={{ duration: 500, x: 200 }}
	class="flex items-center m-5 bg-white border p-2 rounded-lg shadow-md hover:shadow-lg cursor-pointer relative"
>
	<button
		on:click={remove}
		class="absolute right-0 top-0 -mt-3 rounded-full w-5 h-5 bg-red-300 text-white text-sm text-center hover:bg-red-700"
		>x</button
	>
	<p class="w-10">{i + 1}</p>

	<img class="rounded-full w-16 h-16 mx-4" src={image} alt={userName} />
	<span class="mx-4 w-20"> {userName}</span>
	<span class="mx-4 w-20"> {userEmail}</span>
</div>
