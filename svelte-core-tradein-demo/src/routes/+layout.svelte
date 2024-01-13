<!--Layout Boilerplate-->
<script lang="ts">
	// Tailwind CSS
	import '../app.postcss';

	// Highlight JS
	import hljs from 'highlight.js/lib/core';
	import 'highlight.js/styles/github-dark.css';
	import { storeHighlightJs, type DrawerSettings, type DrawerStore } from '@skeletonlabs/skeleton';
	import xml from 'highlight.js/lib/languages/xml'; // for HTML
	import css from 'highlight.js/lib/languages/css';
	import javascript from 'highlight.js/lib/languages/javascript';
	import typescript from 'highlight.js/lib/languages/typescript';

	hljs.registerLanguage('xml', xml); // for HTML
	hljs.registerLanguage('css', css);
	hljs.registerLanguage('javascript', javascript);
	hljs.registerLanguage('typescript', typescript);
	storeHighlightJs.set(hljs);

	// Floating UI for Popups
	import { computePosition, autoUpdate, flip, shift, offset, arrow } from '@floating-ui/dom';
	import { storePopup } from '@skeletonlabs/skeleton';

	// FaIcon
	import Fa from 'svelte-fa';
	import {
		faAnglesRight,
		faCommentDollar,
		faCheckDouble,
		faFileLines
	} from '@fortawesome/pro-duotone-svg-icons';
	import { faStore } from '@fortawesome/pro-duotone-svg-icons';

	// Layout
	import { AppShell, AppBar, AppRailAnchor, AppRail, AppRailTile } from '@skeletonlabs/skeleton';
	storePopup.set({ computePosition, autoUpdate, flip, shift, offset, arrow });

	// Store
	import { initializeStores, getDrawerStore } from '@skeletonlabs/skeleton';

	//TreeView
	import {
		TreeView,
		TreeViewItem,
		RecursiveTreeView,
		type TreeViewNode
	} from '@skeletonlabs/skeleton';

	initializeStores();
	const drawerStore: DrawerStore = getDrawerStore();
	const drawerSettings: DrawerSettings = {
		id: 'main-drawer',
		bgDrawer: 'bg-gray-800',
		width: 'w-[300px] md:w-[15%]',
		padding: 'p-4',
		rounded: 'rounded-r-2xl',
		opacityTransition: false
	};

	function openDrawer() {
		drawerStore.open(drawerSettings);
	}

	let currentTile: number = 0;
	const branchMenu = [
		{
			id: 0,
			name: 'รายงาน Job Trade-in',
			icon: faCommentDollar,
			route: '/job-trade-in'
		},
		{
			id: 1,
			name: 'ยืนยันการ Trade-in',
			icon: faCheckDouble,
			route: '/trade'
		}
	];

	const reportMenu = [
		{
			id: 2,
			name: 'Report',
			icon: faFileLines,
			route: '/report'
		}
	];
</script>

<AppShell>
	<svelte:fragment slot="header">
		<AppBar>
			<svelte:fragment slot="lead">
				<Fa icon={faStore} />
				<span class="ml-4"><h2>Trade-in</h2></span>
			</svelte:fragment>
			<svelte:fragment slot="trail">(actions)</svelte:fragment>
		</AppBar>
	</svelte:fragment>
	<svelte:fragment slot="sidebarLeft">
		<AppRail width="w-24">
			{#each branchMenu as menu}
				<AppRailTile
					selected={true}
					name="tile{menu.id}"
					title="tile{menu.id}"
					value={menu.id}
					bind:group={currentTile}
					hover="bg-primary-hover-token"
					active="bg-primary-active-token"
					regionLead="flex justify-center items-center"
				>
					<svelte:fragment slot="lead">
						<Fa icon={menu.icon} size="lg" class="text-2xl grid justify-items-center" >
						</Fa>
						
					</svelte:fragment>
					<span class="text-center text-sm flex justify-center">{menu.name}</span>
					
				</AppRailTile>
			{/each}
		</AppRail>
	</svelte:fragment>
	<svelte:fragment slot="pageHeader"></svelte:fragment>
	<slot />
	<svelte:fragment slot="pageFooter"></svelte:fragment>
	<svelte:fragment slot="footer"></svelte:fragment>
</AppShell>
