<script>
	import { onMount } from 'svelte';
	//import template from './templates/templateTeste1.txt'
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
  let fileContent = '';

	onMount(async () => {
	const response = await fetch('//templates//templateTeste1.txt');
	fileContent = await response.text();
	console.log(fileContent)
	});
	;
  
  	let props = {
	nome: nome ,
	resumo: resumo
	}
	let template = '<h2>{nome}</h2> <h1>{resumo}</h1>'; 
	let filledTemplate = Object.entries(props).reduce((template, [key,value]) => {
		return template.replaceAll(`{${key}}`, value)
	},template)

	function handleChange(event, variavel) {
		props[variavel]  = event.target.value;
		// console.log(props);
		updateFilledTemplate();
	}
	
	function updateFilledTemplate() {
    	filledTemplate = Object.entries(props).reduce((template, [key,value]) => {
      return template.replaceAll(`{${key}}`, value)
    },template)
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
			  <input bind:value="{nome}" class="input-nome" on:input="{(e) => handleChange(e,'nome')}"/>
			</label>
			<br />
			<label>
			  <p>Texto:</p>
			  <textarea bind:value="{resumo}" class="input-caixa-texto" on:input="{(e) => handleChange(e,'resumo')}"></textarea>
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
			
			{@html filledTemplate}
			
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

	
	
	