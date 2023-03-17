<script>
    export let items, title;
</script>

<h1>{title}</h1>
    <ul>
        {#each items as item}
            <li>
                {item.name}
                <input type="checkbox" bind:checked={item.done}>
            </li>

        {/each}
    </ul>