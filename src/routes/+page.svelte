<script>
  import Splash from '../components/Splash/Splash.svelte';
	import Gallery from '../components/Gallery/Gallery.svelte';
	import { images } from '../utils/mock-data';
</script>

<svelte:head>
	<title>Gallery</title>
	<meta name="description" content="Photo gallery" />
</svelte:head>

<Splash image={images[0].image}/>
<Gallery images={images} />

