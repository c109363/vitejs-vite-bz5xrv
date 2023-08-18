<h1>Visual Complexity Measures</h1>

<script>
  import { onMount } from 'svelte';

  let image1 = getRandomImage();
  let image2 = getRandomImage();
  let showImages = true;
  let selectedImage = null;

  function getRandomImage() {
    return `./${Math.floor(Math.random() * 100) + 1}.jpg`;
  }

  function showNextImages() {
    image1 = getRandomImage();
    image2 = getRandomImage();
    selectedImage = null;
    showImages = true;
  }

  function handleChoice(choice) {
    selectedImage = choice;
  }

  onMount(() => {
    showNextImages();
  });
</script>



<div class="container">
<h3 style = "color:black;">Please select the image that you perceive to have higher visual complexity. </h3>
  <div class="images">
    <div
      class="clickable-image {selectedImage === 'image1' && 'selected'}"
      on:click={() => {
        handleChoice('image1');
        showNextImages();
      }}
    >
      <img src={image1} alt="Image 1" />
    </div>
    <div
      class="clickable-image {selectedImage === 'image2' && 'selected'}"
      on:click={() => {
        handleChoice('image2');
        showNextImages();
      }}
    >
      <img src={image2} alt="Image 2" />
    </div>
  </div>
  <button on:click={showNextImages}>I'm not sure</button>
</div>


<style>
  .container {
    display: flex;
    justify-content: center;
    align-items: center;
  
    flex-direction: column;
    background-color: #fffefe; 
    border: 2px solid #858585; 
    border-radius: 8px; 
    padding: 5% 10%;
    margin: -4%;
  }

  .images {
    display: flex;
    gap: 20px;
    margin-bottom: 20px;
  }

  .clickable-image {
    cursor: pointer;
    border: 3px solid transparent;
    transition: border-color 0.3s;
  }

  .clickable-image.selected {
    border-color: darkgreen;
  }

  .clickable-image img {
    width: 350px;
  }

  .clickable-image:hover {
    border-color: lightgreen;
  }

    h1,h2,h3 {
    text-align: center;
    display: flex;
    justify-content: center;
    align-items: center;
    }

</style>