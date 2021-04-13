<script>
    import Nav from "@components/Nav.svelte"
</script>

  
<svelte:head>
  <head>
    <link
      rel="stylesheet"
      href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css"
    />
  </head>
</svelte:head>

<main>
    <Nav />
    <slot/>
</main>

<style>
    	 main {
		text-align: center;
		padding: 0em;
		max-width: 240px;
		margin: 0 auto;
    box-sizing: border-box;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}

    @font-face {
    font-family: 'Galano';
    src: url('../assets/fonts/GalanoGrotesqueAlt-SemiBold.eot');
    src: url('../assets/fonts/GalanoGrotesqueAlt-SemiBold.eot?#iefix') format('embedded-opentype'),
      url('../assets/fonts/GalanoGrotesqueAlt-SemiBold.woff2') format('woff2'),
      url('../assets/fonts/GalanoGrotesqueAlt-SemiBold.woff') format('woff'),
      url('../assets/fonts/GalanoGrotesqueAlt-SemiBold.ttf') format('truetype');
    font-weight: 600;
    font-style: normal;
    font-display: swap;
  }
  
  @font-face {
    font-family: 'Galano';
    src: url('../assets/fonts/GalanoGrotesqueAlt-Medium.eot');
    src: url('../assets/fonts/GalanoGrotesqueAlt-Medium.eot?#iefix') format('embedded-opentype'),
      url('../assets/fonts/GalanoGrotesqueAlt-Medium.woff2') format('woff2'),
      url('../assets/fonts/GalanoGrotesqueAlt-Medium.woff') format('woff'),
      url('../assets/fonts/GalanoGrotesqueAlt-Medium.ttf') format('truetype');
    font-weight: 500;
    font-style: normal;
    font-display: swap;
  }
  
  @font-face {
    font-family: 'Canela';
    src: url('../assets/fonts/Canela-MediumItalic.eot');
    src: url('../assets/fonts/Canela-MediumItalic.eot?#iefix') format('embedded-opentype'),
      url('../assets/fonts/Canela-MediumItalic.woff2') format('woff2'),
      url('../assets/fonts/Canela-MediumItalic.woff') format('woff'),
      url('../assets/fonts/Canela-MediumItalic.ttf') format('truetype');
    font-weight: 500;
    font-style: italic;
    font-display: swap;
  }
  
  @font-face {
    font-family: 'Galano';
    src: url('../assets/fonts/GalanoGrotesqueAlt-Regular.eot');
    src: url('../assets/fonts/GalanoGrotesqueAlt-Regular.eot?#iefix') format('embedded-opentype'),
      url('../assets/fonts/GalanoGrotesqueAlt-Regular.woff2') format('woff2'),
      url('../assets/fonts/GalanoGrotesqueAlt-Regular.woff') format('woff'),
      url('../assets/fonts/GalanoGrotesqueAlt-Regular.ttf') format('truetype');
    font-weight: normal;
    font-style: normal;
    font-display: swap;
  }
  

</style>

 