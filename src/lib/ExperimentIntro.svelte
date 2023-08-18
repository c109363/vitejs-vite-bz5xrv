
<script>
    import DataCollection from './DataCollection.svelte';
    let showDataCollection = false;
    let agreed = false;
    function toggleAgree() {
    agreed = !agreed;
    }
    function startDataCollection() {
    if (agreed) {
      showDataCollection = true;
    }
  }
  </script>

{#if !showDataCollection}
<h1>Visual Complexity Measures</h1>
    <p><strong>Description: </strong>We would like to know the perceived visual complexity of a scene.  In this experiment, you will see two images side-by-side, and your task will be to say which one is more complex. At this point, we do not have metrics to measure visual complexity. So you can use your own subjective experience to choose the higher one or “I don’t know” when there is no obvious difference to you.</p>
    <p><strong>Who can participate: </strong>Anyone who is an English speaker, has some visualization experience, and is of legal age (18 years in most countries) can participate.</p>
    <p><strong>Duration: </strong>The study takes about 4-10 minutes. After this informed consent, you will see a training image telling you about the interface and how to click to choose an answer. Then you will be asked to do a brief 3-task practice session After this, there will be 100 visual complexity comparison tasks followed by a brief questionnaire seeking your input.</p>
    <p><strong>Privacy and Data Collection: </strong>This study is anonymous - we do not require participants to provide any information that could identify them in the consent form or in the survey.</p>
    <p><strong>Contact information: </strong>If you have questions about this research, please contact one of us:
    </p>
    <p style = "text-indent: 20px"><strong>
        · Jian Chen</strong>, Associate Professor, Computer Science and Engineering, The Ohio State University, 
        <a href="mailto:chen.8028@osu.edu">chen.8028@osu.edu</a>.</p>
    <p style = "text-indent: 20px"><strong>
        · Michael Sedlmair</strong>, Professor, Computer Science, University of Stuttgart, 
        <a href="mailto:michael.sedlmair@visus.uni-stuttgart.de">michael.sedlmair@visus.uni-stuttgart.de</a>.</p>
    <p style = "margin-top: 10px;text-align: left;">Participation in this research is voluntary, and can stop at any time by simply closing the web browser without penalty.</p>
   
   <label >
      <input type="checkbox" bind:checked={agreed} /> 
      <span class="custom-label-text">I agree to participate in this research.</span>
    </label>

    <div class="button-container">
        {#if agreed}
        <button class:active={agreed} on:click={startDataCollection}>
            START
          </button>

        {:else}
        <button class:active={agreed} class:enabled={agreed} on:click={startDataCollection}>
            START
          </button>
        {/if}
      </div>

  {:else}
  <DataCollection />
  {/if}

<style>
    
    .button-container {
    display: flex;
    justify-content: center;
    margin-top: 20px; 
    }
    button {
      background-color: #ccc;
      border: none;
      padding: 10px 20px;
      cursor: pointer;
    }
  
    button.active {
      background-color: blue;
      color: white;
      padding: 10px 20px; 
    }

    h1 {
    text-align: center;
    display: flex;
    justify-content: center;
    align-items: center;
    }
    p {
    text-align: left;
    margin: 0 4%; 
    font-size: 16px;
    }
    label{
        margin: 0 4%; 
    }
  </style>