<script lang="ts">
	import IconCog from 'virtual:icons/mdi/cog'
	import IconHelpCircle from 'virtual:icons/mdi/help-circle'
	import IconDotsGrid from 'virtual:icons/mdi/dots-grid'
	import IconGoogleDrive from 'virtual:icons/mdi/google-drive'
	import IconFolderGoogleDrive from 'virtual:icons/mdi/folder-google-drive'
	import IconMagnify from 'virtual:icons/mdi/magnify'
	import IconTune from 'virtual:icons/mdi/tune'
	import IconCheck from 'virtual:icons/mdi/check-underline-circle-outline'
	import IconPlus from 'virtual:icons/mdi/plus'
	import IconMenuRight from 'virtual:icons/mdi/menu-right'
	import IconMenuDown from 'virtual:icons/mdi/menu-down'
	import IconFilter from 'virtual:icons/mdi/filter-variant'
	import IconGridLarge from 'virtual:icons/mdi/grid-large'
	import IconInfo from 'virtual:icons/mdi/information-outline'
	import IconArrowDown from 'virtual:icons/mdi/arrow-down'
	import IconFolder from 'virtual:icons/mdi/folder'

	type DriveItem = {
		kind: 'file' | 'folder'
		name: string
		size?: number
		owner: {
			avatar_url: string
			name: string
		}
		lastModified: {
			date: Date
			author: string
		}
	}

	const itens: DriveItem[] = [
		{
			kind: 'folder',
			name: 'coding',
			owner: {
				name: 'me',
				avatar_url: 'https://i.imgur.com/Ydd8U6P.jpg'
			},
			lastModified: {
				author: 'me',
				date: new Date('01-29-2021')
			}
		},
		{
			kind: 'folder',
			name: 'My Stuff',
			owner: {
				name: 'me',
				avatar_url: 'https://i.imgur.com/Ydd8U6P.jpg'
			},
			lastModified: {
				author: 'me',
				date: new Date('02-26-2021')
			}
		},
		{
			kind: 'file',
			name: 'mods.zip',
			owner: {
				name: 'me',
				avatar_url: 'https://i.imgur.com/Ydd8U6P.jpg'
			},
			lastModified: {
				author: 'me',
				date: new Date('07-02-2023')
			},
			size: 69.9
		}
	]
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
					class="focus:bg-white bg-slate-100 text-slate-600 placeholder-slate-600 h-12 w-[800px] rounded-full px-14 focus:outline-none"
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
		<div class="min-w-[250px] h-screen py-4 mr-4 flex flex-col gap-4">
			<div>
				<button
					class="flex gap-2 bg-white rounded-xl drop-shadow-lg py-4 px-5 hover:bg-slate-200"
				>
					<IconPlus class="w-6 h-6" />
					New
				</button>
			</div>

			<div class="flex flex-col gap-4">
				<div class="flex flex-col">
					<div
						class="flex items-center justify-left gap-3 rounded-full py-1 px-2 container bg-sky-200"
					>
						<div class="flex items-center justify-center">
							<IconMenuRight class="w-4 h-4" />
							<IconFolderGoogleDrive />
						</div>
						<p class="text-slate-500 font-medium">My Drive</p>
					</div>

					<div
						class="flex items-center justify-left gap-3 rounded-full py-1 px-2 container"
					>
						<div class="flex items-center justify-center">
							<IconMenuRight class="w-4 h-4" />
							<IconFolderGoogleDrive />
						</div>
						<p class="text-slate-500 font-medium">Computers</p>
					</div>
				</div>

				<div class="flex flex-col">
					<div
						class="flex items-center justify-left gap-3 rounded-full py-1 px-2 container"
					>
						<div class="flex items-center justify-center">
							<IconMenuRight class="w-4 h-4" />
							<IconFolderGoogleDrive />
						</div>
						<p class="text-slate-500 font-medium">Shared with me</p>
					</div>

					<div
						class="flex items-center justify-left gap-3 rounded-full py-1 px-2 container"
					>
						<div class="flex items-center justify-center">
							<IconMenuRight class="w-4 h-4" />
							<IconFolderGoogleDrive />
						</div>
						<p class="text-slate-500 font-medium">Recent</p>
					</div>

					<div
						class="flex items-center justify-left gap-3 rounded-full py-1 px-2 container"
					>
						<div class="flex items-center justify-center">
							<IconMenuRight class="w-4 h-4" />
							<IconFolderGoogleDrive />
						</div>
						<p class="text-slate-500 font-medium">Starred</p>
					</div>
				</div>

				<div class="flex flex-col">
					<div
						class="flex items-center justify-left gap-3 rounded-full py-1 px-2 container"
					>
						<div class="flex items-center justify-center">
							<IconMenuRight class="w-4 h-4" />
							<IconFolderGoogleDrive />
						</div>
						<p class="text-slate-500 font-medium">Spam</p>
					</div>

					<div
						class="flex items-center justify-left gap-3 rounded-full py-1 px-2 container"
					>
						<div class="flex items-center justify-center">
							<IconMenuRight class="w-4 h-4" />
							<IconFolderGoogleDrive />
						</div>
						<p class="text-slate-500 font-medium">Trash</p>
					</div>

					<div
						class="flex items-center justify-left gap-3 rounded-full py-1 px-2 container"
					>
						<div class="flex items-center justify-center">
							<IconMenuRight class="w-4 h-4" />
							<IconFolderGoogleDrive />
						</div>
						<p class="text-slate-500 font-medium">Storage</p>
					</div>
				</div>
			</div>
		</div>

		<div class="container bg-white m-2 p-4 rounded-2xl">
			<div class="flex flex-col gap-4">
				<div class="flex items-center justify-between">
					<div>
						<button class="flex gap-1 items-center">
							<span class="text-2xl">My Drive</span>
							<IconMenuDown />
						</button>
					</div>

					<div class="flex items-center gap-4">
						<IconFilter />
						<IconGridLarge />
						<IconInfo />
					</div>
				</div>

				<div class="flex items-center gap-3 text-sm">
					<button
						class="border-[1px] border-slate-500 rounded-md px-3 py-1 flex items-center justify-center gap-3"
					>
						<span> File type </span>
						<IconMenuDown />
					</button>

					<button
						class="border-[1px] border-slate-500 rounded-md px-3 py-1 flex items-center justify-center gap-3"
					>
						<span> People </span>
						<IconMenuDown />
					</button>

					<button
						class="border-[1px] border-slate-500 rounded-md px-3 py-1 flex items-center justify-center gap-3"
					>
						<span> Last modified </span>
						<IconMenuDown />
					</button>
				</div>

				<div>
					<table class="container text-slate-600 font-light">
						<thead class="border-b-2 container">
							<tr class="flex items-center justify-between py-3">
								<th class="flex items-center gap-4">
									<span>Name</span>
									<IconArrowDown />
								</th>

								<th>Owner</th>

								<th class="flex items-center"
									><span>Last modified</span>
									<IconMenuDown />
								</th>

								<th>File size</th>
							</tr>
						</thead>

						<tbody class=" container">
							{#each itens as item}
								<tr
									class="border-b-2 flex items-center p-3 hover:bg-gray-100 justify-between"
								>
									<td class="flex items-center gap-4">
										<IconFolder />
										<span>{item.name}</span>
									</td>

									<td class="flex items-center gap-2">
										<img
											src={item.owner.avatar_url}
											alt="Avatar"
											class="h-5 w-5 rounded-full"
										/>
										<span class="text-sm"> {item.owner.name} </span>
									</td>

									<td
										><span class="text-sm"
											>{item.lastModified.date.toDateString()}
											{item.lastModified.author}</span
										>
									</td>

									<td> {item.size ? item.size : '-'} </td>
								</tr>
							{/each}
						</tbody>
					</table>
				</div>
			</div>
		</div>
	</div>
</main>
