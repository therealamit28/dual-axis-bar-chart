<script>
import { line, curveBasis } from 'd3-shape';
import data from '../data.js';

let linePath;

export let xScale;
export let yScale2;
export let stroke='red';



linePath= line()
.x((d) => xScale(d.month) + xScale.bandwidth() / 2)
      .y((d) => yScale2(d.profit))
      .curve(curveBasis);

</script>
<path d={linePath(data)} stroke={stroke} fill="none" stroke-width="2" />


