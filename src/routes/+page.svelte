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
	import IconFile from 'virtual:icons/mdi/file'
	import IconComputers from 'virtual:icons/mdi/cellphone-link'
	import IconSharedWithMe from 'virtual:icons/mdi/account-supervisor'
	import IconRecent from 'virtual:icons/mdi/clock-time-four-outline'
	import IconStarred from 'virtual:icons/mdi/star-outline'
	import IconSpam from 'virtual:icons/mdi/alert-octagon-outline'
	import IconTrash from 'virtual:icons/mdi/trash-can-outline'
	import IconStorage from 'virtual:icons/mdi/cloud-outline'
	import { createClient } from '@supabase/supabase-js'
	import {
		PUBLIC_SUPABASE_URL,
		PUBLIC_SUPABASE_ANON_KEY
	} from '$env/static/public'

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

	let files: FileList

	const supabase = createClient(PUBLIC_SUPABASE_URL, PUBLIC_SUPABASE_ANON_KEY)

	async function handleLogin() {
		const { data, error } = await supabase.auth.signInWithOAuth({
			provider: 'github',
			options: { redirectTo: 'http://localhost:5173' }
		})

		console.log({ data, error })
	}

	async function handleUpload() {
		const { data, error } = await supabase.storage
			.from('files')
			.upload('public/avatars/me.jpg', files[0])

		console.log({ data, error })
	}
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

	<button on:click={handleLogin}>SIGN IN</button>

	<form on:submit={handleUpload}>
		<input type="file" bind:files />
		<button type="submit">enviasr</button>
	</form>

	{#if files && files[0]}
		<p>
			{files[0].name}
		</p>
	{/if}

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
							<IconComputers />
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
							<IconSharedWithMe />
						</div>
						<p class="text-slate-500 font-medium">Shared with me</p>
					</div>

					<div
						class="flex items-center justify-left gap-3 rounded-full py-1 px-2 container"
					>
						<div class="flex items-center justify-center">
							<IconMenuRight class="w-4 h-4" />
							<IconRecent />
						</div>
						<p class="text-slate-500 font-medium">Recent</p>
					</div>

					<div
						class="flex items-center justify-left gap-3 rounded-full py-1 px-2 container"
					>
						<div class="flex items-center justify-center">
							<IconMenuRight class="w-4 h-4" />
							<IconStarred />
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
							<IconSpam />
						</div>
						<p class="text-slate-500 font-medium">Spam</p>
					</div>

					<div
						class="flex items-center justify-left gap-3 rounded-full py-1 px-2 container"
					>
						<div class="flex items-center justify-center">
							<IconMenuRight class="w-4 h-4" />
							<IconTrash />
						</div>
						<p class="text-slate-500 font-medium">Trash</p>
					</div>

					<div
						class="flex items-center justify-left gap-3 rounded-full py-1 px-2 container"
					>
						<div class="flex items-center justify-center">
							<IconMenuRight class="w-4 h-4" />
							<IconStorage />
						</div>
						<p class="text-slate-500 font-medium">Storage</p>
					</div>
				</div>

				<div class="flex flex-col items-center gap-2">
					<div class="mx-auto w-10/12 bg-gray-200 rounded-full h-1">
						<div class="bg-blue-600 h-1 rounded-full w-1/3" />
					</div>
					<span class="font-light"> 3.93 GB of 15 GB used </span>
				</div>

				<div class="flex items-center justify-center">
					<button
						class="text-blue-600 text-sm border-gray-700 hover:bg-gray-100 border-[1px] rounded-full h-10 w-2/3"
					>
						Get more storage
					</button>
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
										{#if item.kind === 'file'}
											<IconFile />
										{:else}
											<IconFolder />
										{/if}

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
