<template>
  <div class="hero-container">
    <img src="54161682575_e27d2b25a6_o.jpg" alt="Hero Background" class="background-image" />

    <header class="nav-bar">
      <div class="logo">fiverr like website<span class="dot">.</span></div>
      <nav>
        <a href="FiverrService.vue" @click.prevent="$emit('change-page', 'serviceWeb')">find experts</a>
        <a href="#">Explore</a>
        <a href="register.vue" @click.prevent="$emit('change-page', 'register')">register</a>
        <a href="#">Fiverr Go</a>
        <a href="sign_in.vue" @click.prevent="$emit('change-page', 'login')">sign in</a>
        <button class="join-btn">Join</button>
      </nav>
    </header>

    <div class="hero-content">
      <h1 class="main-title">Our freelancers<br>will take it from here</h1>
      <div class="search-bar">
        <input type="text" placeholder="Search for any service..." />
        <button class="search-btn">>>></button>
      </div>

      <div class="tags">
        <button>website development →</button>
        <button>architecture & interior design →</button>
        <button>UGC videos →</button>
        <button>video editing →</button>
      </div>

    </div>
  </div>
</template>

<script>
export default {
  name: 'HeroFiverrReplica'
}
</script>

<style scoped>
.hero-container {
  position: relative;
  height: 100vh;
  color: white;
  overflow: hidden;
}

.background-image {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  z-index: -1;
}

.nav-bar {
  display: flex;
  justify-content: space-between;
  padding: 1.2rem 2rem;
  background: rgba(255, 255, 255, 0.95);
  color: #000;
  font-weight: bold;
}

.nav-bar .logo {
  font-size: 1.5rem;
}

.nav-bar .dot {
  color: #1dbf73;
}

.nav-bar nav a {
  margin: 0 10px;
  text-decoration: none;
  color: #333;
}

.join-btn {
  background: none;
  border: 1px solid #000;
  padding: 5px 10px;
  border-radius: 4px;
}

.hero-content {
  padding: 10rem 4rem 0 4rem;
}

.main-title {
  font-size: 3rem;
  line-height: 1.2;
  margin-bottom: 1.5rem;
  color: #1dbf73;
}

.search-bar {
  display: flex;
  max-width: 600px;
  background: white;
  border-radius: 4px;
  overflow: hidden;
  margin-bottom: 1.5rem;
}

.search-bar input {
  flex: 1;
  padding: 12px;
  border: none;
  font-size: 1rem;
}

.search-btn {
  background: black;
  color: white;
  border: none;
  padding: 0 20px;
  font-size: 1.2rem;
  cursor: pointer;
}

.tags {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-bottom: 2rem;
}

.tags button {
  background: none;
  border: 1px solid white;
  padding: 8px 12px;
  border-radius: 20px;
  color: white;
  font-size: 0.9rem;
}

.trusted {
  display: flex;
  align-items: center;
  gap: 20px;
  flex-wrap: wrap;
  font-size: 0.9rem;
  opacity: 0.8;
}

.trusted img {
  height: 24px;
  filter: grayscale(100%);
}
</style>