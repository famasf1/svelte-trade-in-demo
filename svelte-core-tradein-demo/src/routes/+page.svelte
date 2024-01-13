
<script>
	let grid = 'grid';
	let gridCols = 'grid-cols-1';
	let gap = 'gap-4';
	let minWidth = 'min-w-full';
	let minWidthMd = 'md:min-w-[750px]';

	$: loginBoxStyleSettings = `${grid} ${gridCols} ${gap} ${minWidth} ${minWidthMd}`;

</script>

<div class="flex justify-center">
	<!-- <div class="grid grid-cols-1 gap-4 min-w-full md:min-w-[750px]">
		<h3 class="text-center py-6">Create A Code Snippet!</h3>
		<div class="card p-4 w-full text-token space-y-4">
			<label class="label">
				<span>Snippet Title</span>
				<input class="input" type="text" placeholder="Snippet Title" />
			</label>
			<label class="label">
				<span>Programming Language</span>
				<select class="select">
					<option value="html">HTML</option>
					<option value="css">CSS</option>
					<option value="typescript">Typescript</option>
					<option value="javascript">Javascript</option>
				</select>
				<input class="input" type="text" placeholder="Programming Language" />
			</label>
			<label class="label">
				<span>Snippet</span>
				<textarea class="textarea" rows="4" placeholder="Snippet Content goes here..." />
			</label>
		</div>
		<div class="text-center py-6">
			<h2>My Code Snippet</h2>
		</div>
	</div> -->

	<div class="{loginBoxStyleSettings} items-center h-screen">
		<div class="card w-full text-token space-y-4">
			<label class="label" for="inputField">
				<span></span>
			</label>
			<input class="input" type="text" id="inputField" placeholder="Input Field" />
			<label class="label" for="inputField">
				<span></span>
			</label>
			<input class="input" type="text" id="inputField" placeholder="Input Field" />
		</div>
	</div>
	
</div>

<style>

</style>