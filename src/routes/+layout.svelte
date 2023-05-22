<script>
    import Navbar from "../lib/Navbar.svelte";
    import Footer from "../lib/Footer.svelte";
    import Notifications from "../lib/Notifications.svelte";
</script>

<Navbar/>
<Notifications/>
<slot/>
<Footer/>