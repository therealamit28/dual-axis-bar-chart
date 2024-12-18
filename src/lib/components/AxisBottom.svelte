<script>

export let xScale;
  export let margin;
  export let height;
  export let width;

export let FilterFunction = (d) => true;
export let formatFunction = (d) => d;


const FilterTicks =(domain)=>domain.filter(FilterFunction);
</script>


{#if xScale}
  <g transform="translate(0,{height - margin.bottom })">
    <line stroke="black" 
    x1={margin.left} 
    x2={width - margin.right} />



    {#each xScale.domain() as tick}
      <line
        stroke="Blue"
        x1={xScale(tick)+xScale.bandwidth()/2}
        x2={xScale(tick)+xScale.bandwidth()/2}
        y1={6} />
    {/each}


   
{#each FilterTicks(xScale.domain()) as tick}

<g transform="translate({xScale(tick)+xScale.bandwidth()/2},0)">

<text 
font-size="10px"
fill="black"
text-anchor="middle"
dy="15">
{formatFunction(tick)}

</text>

</g>


{/each}


    </g>

    
{/if}