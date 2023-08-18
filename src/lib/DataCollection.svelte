<script>
    import PreExperiment from './PreExperiment.svelte';
  
  let showPreExperiment = false;

    let userAnswers = {
      takenTestBefore: '',
      gender: '',
      age: '',
      education: '',
      experience: '',
      userID: ''
    };

    let isAllQuestionsAnswered = false;
    let isSubmitClicked = false;

    function validateAnswers() {
    isAllQuestionsAnswered = Object.values(userAnswers).every(answer => !!answer);
    return isAllQuestionsAnswered;
    }
  
    function submitAnswers() {
    isSubmitClicked = true;
    if (validateAnswers()) {
      console.log('User answers:', userAnswers);
      // data collection
    }
    }

    function next() {
    if (isAllQuestionsAnswered) {
        showPreExperiment = true 
      // enter experiment
    }
  }
  </script>

   {#if !showPreExperiment}
  <div class="content-container">
    <h1>Visual Complexity Measures</h1>
    <h2>Please tell us a bit about yourself.</h2>
    <p> We need this information for data analysis. 
        Please note that none of the answers are personally identifiable. 
        We take your privacy seriously. 
        You may email Professors Jian Chen (<a href="mailto:chen.8028@osu.edu">chen.8028@osu.edu</a>) 
        and Michael Sedlmair (<a href="mailto:michael.sedlmair@visus.uni-stuttgart.de">michael.sedlmair@visus.uni-stuttgart.de</a>) for more information.</p>
    <div class="question">
      <label>
        Have you taken this test before?
        <select bind:value={userAnswers.takenTestBefore}>
          <option value="No">No</option>
          <option value="Yes">Yes</option>
        </select>
      </label>
    </div>
    <div class="question">
      <label>
        What is your gender?
        <select bind:value={userAnswers.gender}>
          <option value="Man">Man</option>
          <option value="Woman">Woman</option>
          <option value="Non-binary">Non-binary</option>
          <option value="Prefer not to disclose">Prefer not to disclose</option>
          <option value="Prefer to self-describe">Prefer to self-describe</option>
        </select>
      </label>
    </div>
    <div class="question">
      <label>
        How old are you?
        <select bind:value={userAnswers.age}>
          <option value="18-25">18-25</option>
          <option value="26-35">26-35</option>
          <option value="36-45">36-45</option>
          <option value="46-55">46-55</option>
          <option value="Over 55">Over 55</option>
        </select>
      </label>
    </div>
    <div class="question">
      <label>
        What is the highest level of education you have received?
        <select bind:value={userAnswers.education}>
          <option value="Some high-school">Some high-school</option>
          <option value="College">College</option>
          <option value="Graduate school">Graduate school</option>
          <option value="Professional school">Professional school</option>
          <option value="PhD">PhD</option>
        </select>
      </label>
    </div>
    <div class="question">
      <label>
        What is your subjective experience of something being more visually complex?
        <textarea bind:value={userAnswers.experience}></textarea>
      </label>
    </div>
    <div class="question">
      <label>
        Please provide your Prolific ID：
        <input type="text" bind:value={userAnswers.userID} />
      </label>
    </div>

    <div class="button-container">
    <button class:enabled={isAllQuestionsAnswered && !isSubmitClicked} on:click={submitAnswers}>
        Submit</button>
        {#if isSubmitClicked && !isAllQuestionsAnswered}
        <p class="error">You haven't finished all questions</p>
      {/if}
    </div>
  </div>
  
  <div class="next-button-container">
  <button class:enabled={isAllQuestionsAnswered} on:click={next}>
    Next
  </button>
  </div>

  {:else}
  <PreExperiment />
  {/if}

  <style>
    h1,h2 {
    text-align: center;
    display: flex;
    justify-content: center;
    align-items: center;
    }
    .content-container {
      margin: 0 4%;
    }
  
    .question {
      margin-top: 20px;
      align-items: left;
    }
  
    /* 其他样式 ... */
    .enabled {
    background-color: blue;
    color: white;
    cursor: pointer;
    padding: 10px 20px; /* 调整按钮尺寸 */
  }

  .error {
    color: red;
    font-weight: bold;
  }

  .button-container {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 20px;
  }
  .next-button-container {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 50px;
  }
  </style>