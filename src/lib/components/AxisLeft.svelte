
<script>

export let yScale;
export let margin;
export let ticksNumber=5;



</script>

{#if yScale}



<g transform="translate({margin.left},0)">

    <line
    
    y1={yScale(0)}
    y2={yScale(yScale.domain()[1])}
    stroke="black" />

    {#each yScale.ticks(ticksNumber) as tick}
{#if tick!==0}
<line 
stroke="blue"
x1={0}
X2={-6}
y1={yScale(tick)}
y2={yScale(tick)}
/>
{/if}

<text
text-anchor="end"
dominant-baseline="middle"
x={-9}
font-size="10px"
font-weight="bold"
y={yScale(tick)}
>

{tick}</text>
    {/each}
   
</g>

{/if}