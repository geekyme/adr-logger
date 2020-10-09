<script>
  let form = { username: '', repo: '' };
  let url;
  let authenticated = false;
  let message = null; 

  function connectGithub() {
    authenticated = true;
  }

  function logAdr() {
    message = {
      text: "Logging..."
    };
    
    google.script.run.withSuccessHandler(() => {
      message = {
        text: "ADR Logged!"
      };

      setTimeout(() => {
        message = null;
      }, 5000);
    }).commitSingleFileToGithub(form.username, form.repo);
  }

  google.script.run.withSuccessHandler(() => {
    url = result;
  }).getGithubAuthURL()
</script>

<style>
	label {
		width: 70px;
    display: inline-block;
	}
</style>

<div>
  <p>
    <label for="username">Username: </label>
    <input
      id="username"
      name="username"
      label="Github username"
      bind:value={form.username}
    />
  </p>
  <p>
    <label for="username">Repo: </label>
    <input 
      id="repo"
      name="repo" 
      label="Repository name" 
      bind:value={form.repo} 
    />
  </p>
  <div>
    {#if authenticated}
      <button on:click={logAdr} class="blue">Log ADR</button>
      {#if message}
        <div class="message">{ message.text }</div>
      {/if}
    {:else}
      <a on:click={connectGithub} target="_blank" href={url}>Connect with Github</a>
    {/if}
  </div>
</div>
