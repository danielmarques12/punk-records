<script lang="ts">
	import IconCog from 'virtual:icons/mdi/cog'
	import IconHelpCircle from 'virtual:icons/mdi/help-circle'
	import IconDotsGrid from 'virtual:icons/mdi/dots-grid'
	import IconGoogleDrive from 'virtual:icons/mdi/google-drive'
	import IconMagnify from 'virtual:icons/mdi/magnify'
	import IconTune from 'virtual:icons/mdi/tune'
	import IconCheck from 'virtual:icons/mdi/check-underline-circle-outline'
	import IconPlus from 'virtual:icons/mdi/plus'
</script>

<main class="py-2 px-4 bg-slate-50">
	<header class=" flex items-center gap-2 justify-between">
		<div class="flex gap-2 items-center">
			<IconGoogleDrive class="w-10 h-10" />
			<p class="text-2xl font-medium text-slate-600">Drive</p>
		</div>

		<div>
			<label class="relative flex items-center justify-center">
				<span class="absolute inset-y-0 left-0 flex items-center px-5">
					<IconMagnify class="h-6 w-6 fill-slate-500" />
				</span>

				<input
					class="bg-slate-100 text-slate-600 placeholder-slate-600 h-12 w-[800px] rounded-full px-14 focus:outline-none"
					placeholder="Search in Drive"
					type="text"
				/>

				<span class="absolute inset-y-0 right-0 flex items-center px-5">
					<IconTune class="h-6 w-6 fill-slate-500" />
				</span>
			</label>
		</div>

		<div class="flex gap-5 justify-between items-center text-slate-600">
			<IconCheck class="h-6 w-6" />
			<IconHelpCircle class="h-6 w-6" />
			<IconCog class="h-6 w-6" />
			<IconDotsGrid class="h-6 w-6" />
			<img
				src="https://i.imgur.com/Ydd8U6P.jpg"
				alt="Avatar"
				class="h-8 w-8 rounded-full"
			/>
		</div>
	</header>

	<div class="flex">
		<div class="h-screen p-4 flex flex-col gap-4">
			<div>
				<button
					class="flex gap-2 bg-white rounded-xl shadow py-4 px-5 hover:bg-slate-200"
				>
					<IconPlus class="w-6 h-6" />
					New
				</button>
			</div>

			<div class="flex flex-col gap-4">
				<div>
					<div>
						<p class="text-slate-500 font-medium">My Drive</p>
					</div>
				</div>
			</div>
		</div>

		<div class="bg-white">Right Column</div>
	</div>
</main>
