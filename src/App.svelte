<script>
	let nome = "";
	let resumo = "";
	
	//$: conteudo = `Nome: ${nome}\nResumo: ${resumo}`;
	
  </script>
	<header>
		<h1>Curriculo Maker</h1>
	</header>
	<main>
		<div class="container">
			<div class="form">
			<h2>Formulário</h2>
			<form>
				<label>
					<p>Nome:</p>
					<input bind:value="{nome}" />
				</label>
				<br />
				<label>
					<p>Texto:</p>
					<textarea bind:value="{resumo}"></textarea>
				</label>
				<button type='submit'>Exportar</button>
			</form>
			</div>
			
			<div class="content">
				<div>
					<p>{nome}</p>
					<p>{resumo}</p>
				</div>
			</div>
		</div>
	</main>
  
  <style>
  .container {
    display: flex;
  }

  .form {
    flex: 1;
    padding: 20px;
    border-right: 1px solid #ccc; /* Adiciona uma borda à direita */
  }

  .content {
    flex: 1;
    padding: 20px;
  }
  </style>
	