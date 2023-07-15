<script lang="ts">
	import IconCog from 'virtual:icons/mdi/cog'
	import IconHelpCircle from 'virtual:icons/mdi/help-circle'
	import IconDotsGrid from 'virtual:icons/mdi/dots-grid'
	import IconGoogleDrive from 'virtual:icons/mdi/google-drive'
</script>

<main class="p-4">
	<header class="flex items-center gap-2 justify-between">
		<div class="flex gap-2 items-center">
			<IconGoogleDrive />
			<p>Drive</p>
		</div>

		<div>
			<input
				type="text"
				name=""
				placeholder="Search Drive"
				class="bg-gray-100 text-black"
			/>
		</div>

		<div class="flex justify-between items-center">
			<div class="flex gap-4">
				<IconHelpCircle />
				<IconCog />
			</div>

			<div
				class="flex h-8 w-8 items-center justify-center rounded-full bg-neutral-100"
			>
				<IconDotsGrid />
				<img
					src="https://i.imgur.com/Ydd8U6P.jpg"
					alt="Avatar"
					class="h-full w-full rounded-[inherit]"
				/>
			</div>
		</div>
	</header>
</main>
