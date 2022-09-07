<script>
    let links = [
        {
            title: "Homepage",
            link: "https://www.gymnasium-marienstatt.de",
        },
        {
            title: "Instagram",
            link: "https://instagram.com/pgm_abi_2023",
        }
    ]
</script>

<footer class="py-3 w-full mt-4 h-20 text-center" id="footer">
    <ul>
        {#each links as link}
        <li class="inline-block mx-6 my-3">
            <a href="{link.link}" target="_blank">{link.title}</a></li>
        {/each}
    </ul>

</footer>

<style>
    #footer {
        background-color: #0a0a0a;
        transition: background-color 0.3s;
    }
</style>