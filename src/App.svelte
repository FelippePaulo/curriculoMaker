<script>
	import Template1 from './templates/template1.svelte';
  	import Template2 from './templates/template2.svelte';

	let nome = "";
	let resumo = "";
	let selectedTemplate = null;
	let competencias = [];

  function adicionarCompetencia() {
    competencias = [...competencias, { texto: "" }];
  }

  function removerCompetencia(index) {
    competencias = competencias.filter((_, i) => i !== index);
  }

  function selectTemplate(template) {
    selectedTemplate = template;
  }

  </script>
	<header>
		<h1>Curriculo Maker</h1>
	</header>
	<main>
		<div class="botoes-template">
			<button on:click="{() => selectTemplate('template1')}">Template 1</button>
			<button on:click="{() => selectTemplate('template2')}">Template 2</button>
		</div>
	  <div class="container">
		<div class="form">
		  <h2>Formulário</h2>
		  <form>
			<label>
			  <p>Nome:</p>
			  <input bind:value="{nome}" class="input-nome"/>
			</label>
			<br />
			<label>
			  <p>Texto:</p>
			  <textarea bind:value="{resumo}" class="input-caixa-texto"></textarea>
			</label>
			<br />
			<p>Competências:</p>
			
			{#each competencias as competencia, index}
			  <div class="competencia" key={index}>
				<input bind:value="{competencia.texto}" />
				<button type="button" on:click="{() => removerCompetencia(index)}">Remover</button>
			  </div>
			{/each}
			<button type="button" on:click="{adicionarCompetencia}">Adicionar</button>
			<br />
			<button type='submit' class="exportar-curriculo">Exportar</button>
		  </form>
		</div>
		
		<div class="content ">
		  <!-- <div class= "{selectedTemplate}">
			<p>{nome}</p>
			<p>{resumo}</p>
				{#each competencias as competencia,index}
					{competencia.texto}
					<br />
				{/each}
		  </div> -->
		  
			{#if selectedTemplate === 'template1'}
				<Template1 {nome} {resumo} {competencias} />
			{:else if selectedTemplate === 'template2'}
				<Template2 {nome} {resumo} {competencias} />
			{/if}
		</div>
	  </div>
	</main>

	<style>
	/* .template1  {
		color: #d20000; 
	}

	.template2  {
		color: rgb(0, 0, 247); 
	
	} */


  	header {
    background-color: black; 
    color: white; 
    padding: 10px; 
    position: fixed;
    top: 0;
    left: 0;
    right: 0
	} 
	  header h1 {
		margin: 0; 
	  }
	
	  main{
		position:relative;
		top: 55px;
	  }
	  .container {
		display: flex;
	  }
	
	  .form {
		position:relative;
		flex: 1;
		padding: 10px;
		border-right: 1px solid #ccc;
	  }
	
	  .content {
		flex: 1;
		padding: 20px;
	  }

	  .competencia {
			  margin-bottom: 10px;
			}

	  .exportar-curriculo{
		color: red;
		position: relative;
		
	  }

	  .input-nome{
		width: 98%;
	  }

	  .input-caixa-texto{
		overflow-y: scroll;
		resize: none;
		height: 100px;
		width: 98%;
	  }
	</style>

	
	
	