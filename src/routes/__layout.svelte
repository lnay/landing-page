<script>
	import "./layout.scss";
	import Logo from "./components/Logo.svelte";
	import Nav from "./navbar.svelte";
	export let pagepath;
	$: containerClass = pagepath==='/'?"cover-container":"container";
</script>

<script context="module">
	export function load({url}){
		return {props : {pagepath : url.pathname}};
	}
</script>

<!--<meta name="theme-color" content="#7952b3">-->
<svelte:head>
	<title>Lukidean Geometry</title>
</svelte:head>

<div class="outer">
	<div class="{containerClass} inner">
		<header>
			<Logo extraClass="flat"/>
			<Nav pagepath={pagepath}/>
		</header>

		<main>
			<h1>Cover your page.</h1>
			<p>
				Cover is a one-page template for building simple and beautiful home
				pages. Download, edit the text, and add your own fullscreen background
				photo to make it your own.
			</p>
			<p>
				The current page is <em>{pagepath}</em>
			</p>
			<slot></slot>
		</main>

		<footer>
		<p>
			Cover template for
			<a href="https://getbootstrap.com/" class="text-white">Bootstrap</a>
			, by <a href="https://twitter.com/mdo" class="text-white">@mdo</a>.
		</p>
		</footer>
	</div>
</div>

<style lang="scss">
	@use "../../node_modules/bootstrap/scss/bootstrap.scss";
	:global {
		div.outer {
			@extend .d-flex;
			@extend .h-100;
			@extend .text-center;
			@extend .text-white;
			@extend .bg-dark;
		}
		div.inner {
			@extend .d-flex;
			@extend .w-100;
			@extend .h-100;
			@extend .p-3;
			@extend .mx-auto;
			@extend .flex-column;
			transition: max-width 0.5s ease-out;
		}
		header {
			@extend .mb-auto;
		}
		main {
			@extend .px-3;
		}
		footer {
			@extend .mt-auto;
			@extend .text-white-50;
		}
		header > div:first-child {
			@extend .float-md-start;
			@extend .mb-0;
		}
		body {
			text-shadow: 0 .05rem .1rem rgba(0, 0, 0, .5);
			box-shadow: inset 0 0 5rem rgba(0, 0, 0, .5);
		}
	}

	.cover-container {
		max-width: 42em;
	}
</style>
