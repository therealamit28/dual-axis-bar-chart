<script>
    import data from '../data.js'
        export let yScale1;
        export let xScale;
        export let fill="red";
        let newbandwidth;
    
        
        newbandwidth=xScale.bandwidth()*0.7;
    
    
    </script>
    
    
          {#each data as d}
    <rect
     x={xScale(d.month)}
              y={yScale1(d.sales)}
        width={newbandwidth}
        height={yScale1(0)-yScale1(d.sales)}
        {fill}
        />
    
    
                {/each}