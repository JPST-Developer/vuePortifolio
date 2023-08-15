<script setup>
  import { ref, onMounted } from 'vue';

const activeSection = ref('');

onMounted(() => {
  window.addEventListener('scroll', updateActiveSection);
});

function updateActiveSection() {
  const sections = document.querySelectorAll('section');
  
  sections.forEach(section => {
    const rect = section.getBoundingClientRect();
    if (rect.top <= window.innerHeight / 2 && rect.bottom >= window.innerHeight / 2) {
      activeSection.value = section.id;
    }
  });
}

const sections = [
  { id: 'about', name: 'About' },
  { id: 'experiences', name: 'Experiences' },
  { id: 'projects', name: 'Projects' }
];  
</script>

<template>
  <header class="stick-header">
    <div class="inside-header">
      <h1>João Pedro Teixeira</h1>
      <h2>Front-end developer at Mercado Eletrônico</h2>
      <p>I build accessible, inclusive products and digital experiences for the web.</p>

      <nav class="d-block">
          <ul>
            <a v-for="section in sections" :key="section.id" :href="`#${section.id}`" :class="{ active: activeSection === section.id }">
              <span class="nav-indicator"></span>
              <span>{{ section.name }}</span>
            </a>
          </ul>
      </nav>
    </div>
  </header>
</template>

<style scoped>
.stick-header {
  width: 50vw;
  padding-top: 6rem;
  padding-bottom: 6rem;
  align-items: center;
  position: sticky;
  top: 0;
  display: flex;
  flex-direction: column;
  max-height: 70vh;
  flex: 1;
}

.d-block {
  display: block;
}

ul {
  width: max-content;
  display: grid;
}

a {
  padding-top: 0.75rem;
  padding-bottom: 0.75rem;
  align-items: center;
  display: flex;
  color: inherit;
  text-decoration-color: inherit;
  text-decoration: inherit;
}


header h1 {
  letter-spacing: -.025em;
  margin: 0;
  font-size: 3rem;
  line-height: 1;
  font-weight: 700;
  color: rgb(201, 215, 227);
}

header h2 {
  font-size: 1.25rem;
  line-height: 1.75rem;
  margin-top: 0.75rem;
  letter-spacing: -.025em;
  font-weight: 500;
  color: rgb(201, 215, 227);
}

header p {
  line-height: 1.5;
  max-width: 20rem;
  margin-top: 1rem;
  color: rgb(176, 169, 159);
}

.active {
  color: rgb(201, 215, 227);   
}    

.active .nav-indicator {
  width: 4rem;
  border: 1px solid rgb(201, 215, 227); 
}

.nav-indicator {
  box-sizing: border-box;
  margin-right: 1rem;
  transition: all .2s ease-in-out;
  width: 2rem;
  border: 1px solid rgb(36, 39, 41);
  color: rgb(36, 39, 41);
}    
</style>
