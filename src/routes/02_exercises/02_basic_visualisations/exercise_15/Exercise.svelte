<script>
    const width = 100;
    const height = 100;
    const margin = { top: 5, right: 5, bottom: 5, left: 5 };
    const innerWidth = width - margin.left - margin.right;
    const innerHeight = height - margin.top - margin.bottom;
  </script>
  
  <svg {width} {height}>
    <g transform="translate({margin.left}, {margin.top})">
      <rect x={innerWidth/4} y={innerHeight/4} width="40px" height="40px" />
      <circle cx={innerWidth/4 + 40} cy={innerWidth/4 + 40} r=20 />
    </g>
  </svg>
  
  <style>
    svg {
      border: 1px solid black;
      border-radius: 5px;
    }

    rect {
      fill: yellow
    }

    circle {
      fill: skyblue
    }
  </style>
  