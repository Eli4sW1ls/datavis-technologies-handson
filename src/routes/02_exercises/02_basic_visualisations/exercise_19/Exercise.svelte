<script>
    // Dimensions
    const width = 800;
    const height = 100;
    const margin = { top: 20, right: 5, bottom: 5, left: 5 };
    const innerWidth = width - margin.left - margin.right;
    const innerHeight = height - margin.top - margin.bottom;
  
    // Array
    const values = [
      { x: 2, y: 1, category: "cat1" },
      { x: 4, y: 2, category: "cat3" },
      { x: 6, y: 1, category: "cat2" },
      { x: 7, y: 3, category: "cat3" },
      { x: 9, y: 1, category: "cat2" }
    ];

    import { scaleLinear, scaleOrdinal } from 'd3-scale';
    import { schemeSet2 } from 'd3-scale-chromatic'
    const scaleX = scaleLinear()
      .domain([0,10])
      .range([0, innerWidth])

      const scaleY = scaleLinear()
      .domain([0,3.5])
      .range([innerHeight, 0])

      const scaleCat = scaleOrdinal(schemeSet2)
      // const uniques = [...new Set(values.map(v => v.category))]
  </script>
  
  <svg viewBox="0 0 {width} {height}">
    <g transform="translate({margin.left},{margin.top})">
      {#each values as value}
        <circle cx={scaleX(value.x)} cy={scaleY(value.y)} fill={scaleCat(value.category)} r=10 />
        <text x={scaleX(value.x)} y={scaleY(value.y)-15} fill={scaleCat(value.category)} font-size=15px>y={value.y}</text>
      {/each}
    </g>
  </svg>
  
  <style>
    text {
      text-anchor: middle;
      font-size: small;
    }
  </style>
  