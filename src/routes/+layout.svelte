<script>
	import '../app.scss';	
	import Header from "./Header.svelte";
	
</script>




<div id="wrapper">
	<Header />

	<main>
	  <slot />
	</main>
    
	<a href="/portfolio">Developed by Fabiana De Rosa - click for more</a>
	
</div>
  


<style lang="scss">

	#wrapper {
		display: grid;
		grid-template-columns: auto 1fr;
		height: 100vh;
		padding: 0;
		width: 100%; 
		max-width: 1300px; 
		margin: 0 auto;

		a{	
			
			grid-column: 1 / 3;
			color: gray;
			justify-self: center;
			font-weight: 100;
			padding-top: 1.2rem;
			padding-bottom: .4rem;
			font-size: .7rem;
			text-decoration: none;
		}
		
	
	}

	@media screen and (max-width: 600px) {

		#wrapper {
			grid-template-columns: 1fr; 
			

		  a{	
			text-align: center;
			grid-column: 1;
		}
	}
}
</style>