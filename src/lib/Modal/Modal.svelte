<script>
	import { createEventDispatcher } from 'svelte';
	const dispatch = createEventDispatcher();
	const close = () => {
		dispatch('close');
	};
	const onSubmit = () => {
		dispatch('submit');
	};
	export let show;
</script>

{#if show}
	<div class="relative z-10" aria-labelledby="modal-tite" role="dialog" aria-modal="true">
		<div class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity" />
		<div class="fixed z-10 inset-0 overflow-y-auto">
			<div
				class="flex items-center sm:items-center justify-center min-h-full p-4 text-center sm:p-0"
			>
				<div
					class="relative bg-white rounded-lg px-4 pb-4 text-left overflow-hidden shadow-xl transform transition-all sm:my-8 sm:max-w-sm sm:w-full"
				>
					<div class="mt-5 sm:mt-6">
						<!-- Some HTML like props.children  -->
						<form on:submit={onSubmit} preventDefault={onSubmit}>
							<slot />

							<div class="flex justify-between">
								<button
									type="button"
									class="px-2 py-1 bg-white border rounded hover:bg-gray-200"
									on:click={close}
								>
									Close
								</button>
								<slot name="right-button" />
							</div>
						</form>
					</div>
				</div>
			</div>
		</div>
	</div>
{/if}
