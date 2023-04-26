<script>
import { onMount } from "svelte";


    // Dimensions
    const width = 800;
    const height = 100;
    const margin = { top: 10, right: 20, bottom: 20, left: 20 };
    const innerWidth = width - margin.left - margin.right;
    const innerHeight = height - margin.top - margin.bottom;
  
    // Arrays
    const points = [
      innerWidth / 2 - 60,
      innerWidth / 2 - 30,
      innerWidth / 2,
      innerWidth / 2 + 30,
      innerWidth / 2 + 60
    ];
  
    // All lights with a higher index are on!
    let index = points.length;
    let op_list = Array(5).fill(0.3);
  
    // Color
    let color = "darkred";

    function animation(handle) {
      if (index == -1) {
        color = 'darkgreen';
        clearInterval()
      }

      op_list[index] = 1;
      index -= 1;
    }

    onMount(async() => {
      setInterval(animation, 700);
    });
  </script>
  
  <svg viewBox="0 0 {width} {height}">
    <g transform="translate({margin.left},{margin.top})">
      {#each points as p, i}
        <circle cx={p} r=10 fill={color} opacity={op_list[i]}/>
      {/each}
    </g>
  </svg>
  