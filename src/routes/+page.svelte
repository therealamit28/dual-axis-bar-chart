<script>
    import data from '$lib/data.js';
 import AxisLeft from '../lib/components/AxisLeft.svelte';
import AxisBottom from '../lib/components/AxisBottom.svelte';
    import {max} from 'd3-array';
    import {scaleLinear, scaleBand} from 'd3-scale';
  import Axisright from '../lib/components/Axisright.svelte';
  import Labels from '../lib/components/Labels.svelte';
  import Linepath from '../lib/components/Linepath.svelte';
  import Bar from '../lib/components/Bar.svelte';
  


    console.log(data);

    let xScale,yScale1,yScale2;
    let ticksNumber;

let width;
let height=700;
const  margin={top:50,right:160,bottom:20,left:160};


$: if (data && width){

    xScale=scaleBand()
    .domain(data.map(d=>d.month))
    .range([margin.left, width-margin.right])
    .padding(0.2);


    yScale1=scaleLinear()
    .domain([0,max(data, d=>d.sales)])
    .range([height-margin.bottom, margin.top]);



yScale2=scaleLinear()
.domain([0,max(data, d=>d.profit)])
.range([height-margin.bottom, margin.top]);



}



</script>


<div class="wrapper" bind:clientWidth={width} >

    {#if data && width}

    <svg {width}
     height={height+margin.top+margin.bottom}>

<AxisBottom {width} {height}{margin} xScale={xScale}
formatFunction={(d)=>d.slice(0,3)}
FilterFunction={(d,i)=>i%2===0}
/>
     <AxisLeft {margin} yScale={yScale1} {ticksNumber}/>

<Axisright {width} {margin} yScale={yScale2} {ticksNumber}/>


<Bar {xScale} {yScale1} fill="orange" />

<Linepath {xScale} {yScale2} stroke= "green"/>


    </svg>


{/if}
</div>
