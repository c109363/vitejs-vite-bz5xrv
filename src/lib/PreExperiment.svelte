<script lang="ts">
  import Formal from './Formal.svelte';
  let showFirstGroup = true;
  let selectedImage = null; // Track the selected image
 
 let showFormal = false;

  function next() {
        showFormal = true 
    }

  function handleImageClick(event) {
    showFirstGroup = !showFirstGroup;
    selectedImage = event.target.alt;
  }

  function handleButtonClick() {
    showFirstGroup = !showFirstGroup;
    selectedImage = null;
  }
  </script>

 {#if !showFormal}
<div>
    <h1>Visual Complexity Measures</h1>
    <h2>Intro to interface</h2>
    <p>Before we practice, 
        let us see how to finish rating the image during the experiment. 
        The interface is rather simple:</p>
        <p>1. The task: which image has higher visual complexity?
        </p>
        <p>2. Click the more complex one by clicking the image directly or “I am not sure” if you simply cannot tell.
        </p>
        <p>3. Click "I am not sure" to skip the question.</p>
        <p>You will be taken to the next trial as soon as you select your answer. 
            You can click the image with higher visual complexity or 
            “I am not sure” button to proceed to the next trial. 
            You can use the back arrow to go back. 
            Please answer each question carefully. 
        </p>
        <h2>Let’s give it a try before we start the formal experiment.</h2>
    <!-- 添加其他内容 -->
  </div>

<div class="container">
    <main>

    <div>
    <h3 style = "color:black;">Please select the image that you perceive to have higher visual complexity. </h3>
    </div>
      {#if showFirstGroup}
      <img src="/src/lib/images-test/1.jpg" alt="Image 1" 
         on:click={handleImageClick} 
         class:selected={selectedImage === 'Image 1'}>
      <img src="/src/lib/images-test/2.jpg" alt="Image 2" 
         on:click={handleImageClick} 
         class:selected={selectedImage === 'Image 2'}>
      {:else}
      <img src="/src/lib/images-test/3.jpg" alt="Image 3" 
         on:click={handleImageClick} 
         class:selected={selectedImage === 'Image 3'}>
      <img src="/src/lib/images-test/4.jpg" alt="Image 4" 
         on:click={handleImageClick} 
         class:selected={selectedImage === 'Image 4'}>
      {/if}
  
      <div class="unknown-button-container">
      <button class="unknown-button" on:click={handleButtonClick}>I'm not sure.</button>
  
      </div>
  
    </main>
    </div>

  <div class="next-button-container" on:click={next}>
    <button style = "
    background-color: blue;
    color: white;
    cursor: pointer;
    padding: 10px 20px;">
    Start the Formal Experiment
    </button>
    </div>

  {:else}
  <Formal />
  {/if}
  
  <style>
    h1,h2,h3 {
    text-align: center;
    display: flex;
    justify-content: center;
    align-items: center;
    }

    .next-button-container {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 50px;
  }
	img {

	  border: 2px solid transparent; 
	}
  
	img:hover {
	  border-color: #8aff8a; 
	}
  
	img.selected {
	  border-color: #00b300; 
	}

img {
    width: 360px;
    height: 360px;
    margin: 0 1%;
    cursor: pointer;
  }

  .container {
    background-color: #fffefe; 
    border: 2px solid #858585; 
    border-radius: 8px; 
    margin: 4%;
    padding: 2% 4%;
	text-align: center;
	align-items: center;
  }

  .image-container {
    display: flex;
    justify-content: center;
    margin-bottom: 2%;
  }

  .unknown-button {
    font-size: 16px; 
    padding: 8px 16px; 
    margin-top: 16px; 
	display: block;
	align-items: center;
  }
  .unknown-button-container {
    display: flex;
    justify-content: center;
    margin-top: 20px;
  }
  </style>
