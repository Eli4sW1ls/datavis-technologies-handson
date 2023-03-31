<script>
    // Dimensions
    const width = 600;
    const height = 300;
    const margin = { top: 10, right: 10, bottom: 30, left: 60 };
    const innerWidth = width - margin.left - margin.right;
    const innerHeight = height - margin.top - margin.bottom;
  
    // Array
    const data = [
      { service: "Netflix", viewers: 2.9 },
      { service: "Amazon Prime Video", viewers: 1.3 },
      { service: "Disney+", viewers: 2.1 },
      { service: "Hulu", viewers: 0.9 },
      { service: "Apple TV", viewers: 1.1 },
      { service: "Rakuten", viewers: 0.4 }
    ];

    import { scaleLinear, scaleOrdinal, scalePoint, scaleBand } from 'd3-scale';
    import { schemeSet2 } from 'd3-scale-chromatic'
    const uniques = [...new Set(data.map(d => d.service))]
    console.log(uniques);
    const scaleX = scalePoint()
      .domain(uniques)
      .range([0, innerWidth-100])

      const scaleY = scaleLinear()
      .domain([0,3])
      .range([innerHeight, 0])

      const scaleCol = scaleOrdinal(schemeSet2);

      import { axisBottom, axisLeft } from 'd3-axis';
      import { select } from 'd3-selection';
      const xAxis = axisBottom(scaleX);
      const yAxis = axisLeft(scaleY).tickFormat(x => `${x.toFixed(1)}k`);;

      function addxAxis(handle) {
        xAxis(select(handle));
      };
      function addyAxis(handle) {
        yAxis(select(handle));
      };
  </script>
  
  <!-- setting a viewBox and max-width allows the SVG to shrink but not grow! -->
  <svg viewbox="0 0 {width} {height}" style="max-width: {width}px">
    <g transform={`translate(${margin.left},${margin.top})`}>
      {#each data as point}
        <rect x={scaleX(point.service)} y={innerHeight - scaleY(point.viewers)} height={scaleY(point.viewers)} width={innerWidth / 10} fill={scaleCol(point.service)}/>
      {/each}
      <g use:addxAxis transform="translate({innerWidth / 20}, {innerHeight+10})">
        <text fill="currentColor" font-size=20px x={innerWidth/2} y=30>x</text>
      </g>
      <g use:addyAxis transform="translate(-10, 0)">
        <text fill="currentColor" font-size=10px x={-innerHeight/2} y=-40 transform="rotate(-90)">Viewer count</text>
      </g>
    </g>
  </svg>
  