<script>
    export let nome;
    export let resumo;
    export let competencias;
  </script>
  
  <div class="template2">
    <p>{nome}</p>
    <p>{resumo}</p>
    {#each competencias as competencia,index}
      {competencia.texto}
      <br />
    {/each}
  </div>
  
  <style>
    .template2 {
      color: rgb(0, 0, 247);
    }
  </style>