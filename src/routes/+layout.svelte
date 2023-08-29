<main class="flex flex-col justify-between min-h-[100vh]">
	<nav class="bg-blue-500 px-2 py-1 flex items-center justify-between">
		<h1 class="text-white text-2xl">Svelte</h1>
		<ul class="flex">
			<li class="px-2 py-2 text-white hover:text-green-400"><a href="/"> Home </a></li>
			<li class="px-2 py-2 text-white hover:text-green-400"><a href="/about"> About </a></li>
			<li class="px-2 py-2 text-white hover:text-green-400"><a href="/blog"> Blog </a></li>
		</ul>
	</nav>
	<slot />
	<footer class="text-ceneter bg-blue-800 text-white text-2xl text-bold">
		<p>Svelte Traning 2023 &copy;</p>
	</footer>
</main>
