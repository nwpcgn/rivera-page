## Usage

```html
<script>
	// import Fa from 'svelte-fa/src/fa.svelte'
	// import { faCaretLeft, faChevronLeft } from '@fortawesome/free-solid-svg-icons'
	import {
		TabPage,
		TabBar,
		MovieList,
		MovieDetails,
		BackBtn,
		SettingsBtn,
		_page,
		_loading,
		sleep
	} from './lib'

	const setPage = (index = 0, delay = 200) => {
		_loading.set(true)
		sleep(delay)
			.then(() => {
				_page.set(index)
			})
			.then(() => sleep(delay))
			.then(() => {
				_loading.set(false)
			})
	}
</script>

<TabPage {setPage}>
	<svelte:fragment slot="p1">
		<TabBar label="blackburn-archiv">
			<svelte:fragment slot="end">
				<SettingsBtn on:clicked={() => setPage(2, 100)} />
			</svelte:fragment>
		</TabBar>
		<div class="p-8 nwp">
			<h2 class="mb-3">Welcome Page</h2>
			<h4 class="mb-3">
				Create your package using @sveltejs/package and preview/showcase your
				work with SvelteKit
			</h4>
			<p>
				Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the
				documentation
			</p>
		</div>
	</svelte:fragment>
	<svelte:fragment slot="p2">
		<TabBar label="Movies">
			<svelte:fragment slot="start">
				<BackBtn on:clicked={() => setPage(0, 50)} />
			</svelte:fragment>
		</TabBar>

		<MovieList {setPage} />
	</svelte:fragment>
	<svelte:fragment slot="p3">
		<TabBar label="Settings">
			<svelte:fragment slot="start">
				<BackBtn on:clicked={() => setPage(0, 50)} />
			</svelte:fragment>
		</TabBar>
		<div class="p-8 nwp">
			<h2>Page 3</h2>
		</div>
	</svelte:fragment>
	<svelte:fragment slot="p4">
		<TabBar label="Details">
			<svelte:fragment slot="start">
				<BackBtn on:clicked={() => setPage(1, 50)} />
			</svelte:fragment>
		</TabBar>
		<MovieDetails {setPage} />
	</svelte:fragment>
</TabPage>
```
