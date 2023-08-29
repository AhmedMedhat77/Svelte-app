<script>
	import { createEventDispatcher } from 'svelte';
	import Modal from '../Modal/Modal.svelte';
	let showModal = false;
	let newUser = {};
	const dispatch = createEventDispatcher();
	// Handle Submit
	const handleForm = (e) => {
		dispatch('newUser', newUser);
		showModal = false;
	};

	$: disableBtn = !newUser.name || !newUser.userEmail;
</script>

<div class="mt-4">
	<button
		on:click={() => (showModal = true)}
		class="bg-blue-800 py-2 px-2 rounded text-white hover:bg-blue-500 cursor-pointer"
	>
		New user
	</button>

	<Modal show={showModal} on:submit={handleForm} on:close={() => (showModal = false)}>
		<!-- this is the slot we cant add slot inside slot content -->
		<h1 class="text-2xl text-center">Create New User</h1>

		<div class="py-1 px-2 my-4">
			<label for="userName"> Name </label>
			<input
				class="px-2 py-1 rounded border w-full"
				bind:value={newUser.userName}
				type="text"
				name="userName"
				id="userName"
			/>
		</div>

		<div class="py-1 px-2 my-4">
			<label for="userEmail"> Email </label>
			<input
				class="px-2 py-1 rounded border w-full"
				type="userEmail"
				name="userEmail"
				id="userEmail"
				bind:value={newUser.userEmail}
			/>
		</div>
		<div class="py-1 px-2 my-4 flex justify-between">
			<label for="true"> Active: </label>
			<div class="flex">
				<label for="true"> yes </label>
				<input
					class="px-2 py-1 w-full rounded border mx-5"
					type="radio"
					value="true"
					name="active"
					id="true"
					bind:group={newUser.active}
				/>
				<label for="false"> no </label>
				<input
					class="px-2 py-1 w-full rounded border mx-5"
					type="radio"
					value="false"
					name="active"
					id="false"
					bind:group={newUser.active}
				/>
			</div>
		</div>

		<button
			disabled={false}
			id="submitBtn"
			type="submit"
			slot="right-button"
			class="px-2 py-1 bg-blue-400 text-white rounded hover:bg-blue-700">Create</button
		>
	</Modal>
</div>
