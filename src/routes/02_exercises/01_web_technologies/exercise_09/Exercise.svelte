The circumference of a circle with radius {radius} m is {circf} m.

<script>
    const radius = 4234;

    function compute_circumference(radius) {
        return (2*Math.PI*radius).toFixed(2)
    }

    const circf = compute_circumference(radius);
</script>