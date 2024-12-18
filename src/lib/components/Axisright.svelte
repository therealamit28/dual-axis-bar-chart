
<script>
    export let yScale;
    export let width;
    export let margin;
    export let ticksNumber = 5;
  </script>
  
  {#if yScale}
    <g transform="translate({width - margin.right},0)">
      
      <line
        stroke="Black"
        stroke-width="1px"
        y1={yScale(0)}
        y2={yScale(yScale.domain()[1])} />
      {#each yScale.ticks(ticksNumber) as tick}
        {#if tick !== 0}
          <line
            stroke-width="1px"
            stroke="Blue"
            x1={0}
            x2={6}
            y1={yScale(tick)}
            y2={yScale(tick)} />
        {/if}
  
        <text
       
          text-anchor="start"
          font-weight="bold"
          font-size="10"
          dominant-baseline="middle"
          x={12}
          y={yScale(tick)}>
          {tick}
        </text>
      {/each}
    </g>
  {/if}