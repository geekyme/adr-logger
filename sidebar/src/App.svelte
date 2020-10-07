<script>
  export let name;
  let githubLoginContainer;

  const logAdr = () => {
    google.script.run.commitSingleFileToGithub();
  }

  function createElementFromHTML(htmlString) {
    var div = document.createElement('div');
    div.innerHTML = htmlString.trim();

    // Change this to div.childNodes to support multiple top-level nodes
    return div.firstChild; 
  }

  function onSuccess(urlHtml) {
    const node = createElementFromHTML(urlHtml);
    githubLoginContainer.appendChild(node);
  }

  google.script.run.withSuccessHandler(onSuccess).getGithubAuthURL()
</script>

<main>
	<h1>Hello {name}!</h1>
  <p>Visit the <a href="https://svelte.dev/tutorial" target="_blank">Svelte tutorial</a> to learn how to build Svelte apps.</p>
  <strong>Open the following in a new tab:</strong>
  <div bind:this={githubLoginContainer} />
  <button on:click={logAdr} class="blue">Testing ADR logger.</button>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
    line-height: initial;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
