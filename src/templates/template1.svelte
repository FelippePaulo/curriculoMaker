<script>
    export let nome;
    export let resumo;
    export let competencias;
  </script>
  
  <div class="template1">
    <p>{nome}</p>
    <p>{resumo}</p>
    {#each competencias as competencia,index}
      {competencia.texto}
      <br />
    {/each}
  </div>
  
  <style>
    .template1 {
      color: #d20000; 
    }
  </style>