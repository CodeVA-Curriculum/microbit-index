<script>
    import Nav from "$lib/components/Nav.svelte";
    import "bulma/css/bulma.css";
</script>
<Nav />
<div class='container'>
    <slot></slot>
</div>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Raleway:ital,wght@0,100..900;1,100..900&display=swap');
    * {
        font-family: "Raleway", sans-serif;
        font-optical-sizing: auto;
        font-weight:500;
        font-style: normal;
    }
</style>