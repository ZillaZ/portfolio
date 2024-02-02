<script lang="ts">
    enum Listing {
        None,
        Projects,
        Challenges,
        Socials
    }

    let showing: Listing = Listing.None

    const set_showing = (value: Listing) => {
        if (showing == value) {
            showing = Listing.None
        }else{
            showing = value
        }
    }
</script>

<body>
    <video autoplay muted loop>
        <source src="/background.mp4" type="video/mp4">
    </video>
    <nav>
        <button on:click={() => set_showing(Listing.Projects)}>Projects</button>
        <button id="challenges-button" on:click={() => set_showing(Listing.Challenges)}>Challenges</button>
        <button on:click={() => set_showing(Listing.Socials)}>Socials</button>
    </nav>
    <div role="separator" id="presentation" on:mouseenter={() => set_showing(Listing.None)}>
        <h1> Lucas Henrique Santana Marcelino </h1>
        <p> Software developer graduated from the Federal Institute of São Paulo - IFSP. </p>
    </div>
    <div id="content-wrapper">
        {#if showing == Listing.None}
        <img alt="9S" src="/9s.jpg">
        {/if}
        {#if showing != Listing.None}
        <div id="listing-div">
        {#if showing == Listing.Projects}
            <div class="listing-element">
                <img alt="Rust-icon" src="/rust.png">
                <a target="_blank" href="https://github.com/ZillaZ/Email-Tool"> Email-Tool </a>
                <p>Crafted an email response generator using Rust, empowering seamless integration with the Google Gmail API for email parsing, coupled with dynamic text templates to generate personalized responses.</p>
            </div>
            <div class="listing-element">
                <img alt="Angular-icon" src="/angular.png">
                <a target="_blank" href="https://github.com/ZillaZ/SisCadLogin"> SisCadLogin </a>
                <p>Developed a straightforward CRUD application leveraging the Angular Framework, seamlessly integrating with Google Firebase services for enhanced functionality and data management.</p>
            </div>
        {/if}
        {#if showing == Listing.Challenges}
        <div class="listing-element">
            <img alt="Rust-icon" src="/rust.png">
            <a target="_blank" href="https://github.com/ZillaZ/llvm-fibonacci">[WIP] Rinha de Compiler</a>
            <p>The challenge consists of developing a compiler or interpreter for a language called 'rinha'</p>
        </div>
        {/if}
        {#if showing == Listing.Socials}
        <div id="socials" class="listing-element">
            <img alt="X-icon" src="/x.webp">
            <a target="_blank" href="https://twitter.com/rvnsxm"> @rvnsxm </a>
        </div>
        <div id="socials" class="listing-element">
            <img alt="LinkedIn-icon" src="/linkedin.png">
            <a target="_blank" href="https://www.linkedin.com/in/lucas-hsm/">Lucas Henrique Marcelino</a>
        </div>
        {/if}   
        </div>
        {/if}
    </div>
    <footer>
        <p>This page was built using SvelteKit.</p>
    </footer>
</body>
<style lang="scss">
    @import "./styles.scss"
</style>