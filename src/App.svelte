<script>
    import App from './main.js';
    import { Router, Route, Link } from 'svelte-routing';
    import LandingPage from './LandingPage.svelte';
    import WhatsappChat from './WhatsappChat.svelte';
</script>

<Router>
    <nav>
        <Link to="/">Home</Link>
        <Link to="/WhatsappChat">Whatsapp Chat W/o Save</Link>
      </nav>
    <Route path="/" component={LandingPage} />
    <Route path="/WhatsappChat" component={WhatsappChat} />
</Router>
