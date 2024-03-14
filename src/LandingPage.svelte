<script>
    // Add any script logic here
    import { Link } from 'svelte-routing';
</script>
  
<style>
  /* Page styles */
  .container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 100vh;
    font-family: Arial, sans-serif;
  }

  .content {
    text-align: center;
    margin-bottom: 20px;
  }

  .links {
    position: absolute;
    bottom: 20px;
    text-align: center;
    width: 100%;
  }

  h1 {
    font-size: 2.5rem;
    margin-bottom: 10px;
    color: #333;
  }

  a {
    text-decoration: none;
    color: #333;
    font-size: 1.2rem;
  }

  a:hover {
    color: #007bff;
  }

  /* Mobile Styles */
  @media (max-width: 768px) {
    h1 {
      font-size: 2rem;
    }

    .links {
      bottom: 10px;
    }
  }
</style>

<div class="container">
  <div class="content">
    <h1>Welcome to <span style="color: #007bff;">rojinphilip.com</span></h1>
  </div>

  <!-- Link to App.svelte page -->
  <div class="links">
    <Link to ="/WhatsappChat">WhatsApp to Chat</Link>
  </div>
</div>
