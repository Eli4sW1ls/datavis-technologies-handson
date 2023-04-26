<script>
    export let data = [];

    // Dimensions
    const [height, width] = [400, 600];
    const margin = { top: 50, right: 5, bottom: 55, left: 50 };
    const innerWidth = width - margin.left - margin.right;
    const innerHeight = height - margin.top - margin.bottom;

    import { scaleLinear, scaleLog, scaleOrdinal } from 'd3-scale';
    import { schemeSet2 } from 'd3-scale-chromatic'
    import { axisBottom, axisLeft } from 'd3-axis';
    import { select } from 'd3-selection';

    const scaleX = scaleLinear()
      .domain([0, 2900])
      .range([0, innerWidth])

      const scaleY = scaleLinear()
      .domain([0,45])
      .range([innerHeight, 0])

      const scale_rad = scaleLog()
      .domain([1, 200000000])
      .range([0, 4])

      const scale_cont = scaleOrdinal(schemeSet2)

      const xAxis = axisBottom(scaleX);
      const yAxis = axisLeft(scaleY);

      function addxAxis(handle) {
        xAxis(select(handle));
      };
      function addyAxis(handle) {
        yAxis(select(handle));
      };
  </script>

  <!-- {data} -->
  <svg viewBox="0 0 {width} {height}" style="max-width: {width}px">
    <g transform="translate({margin.left}, {margin.top})">
      <text transform="translate({innerWidth/4}, -20)">Income vs. life expectancy in 1800</text>
      {#each data as d}
        {#each d.countries as cntry}
        <circle cx={scaleX(+cntry.income)} cy={scaleY(+cntry.life_exp)} r={scale_rad(+cntry.population)} fill={scale_cont(cntry.continent)} />
        
        <!-- <text x={scaleX(value.x)} y={scaleY(value.y)-15} fill={scaleCat(value.category)} font-size=15px>y={value.y}</text> -->
        {/each}
      {/each}
      <g use:addxAxis transform="translate(0, {innerHeight+10})">
        <text fill="currentColor" font-size=13px x={innerWidth/2} y=30>Income</text>
      </g>
      <g use:addyAxis transform="translate(-10, 0)">
        <text fill="currentColor" font-size=13px x={-innerHeight/2+20} y=-30 transform="rotate(-90)">Life expectancy</text>
      </g>
    </g>
  </svg>
  