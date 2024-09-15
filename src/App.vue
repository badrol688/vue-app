<template>
  <div id="app">
    <header>
      <h1>Vue.js Interactive App</h1>
    </header>

    <main>
      <!-- Click Counter -->
      <section class="card">
        <h2>1. Click Counter</h2>
        <div class="content">
          <p class="count">Count: {{ count }}</p>
          <button @click="incrementCount" class="btn">Increment</button>
        </div>
      </section>

      <!-- Box Color Changer -->
      <section class="card">
        <h2>2. Box Color Changer</h2>
        <div class="content">
          <div class="color-box" :style="{ backgroundColor: boxColor }"></div>
          <button @click="changeColor" class="btn">Change Color</button>
        </div>
      </section>

      <!-- Image Carousel -->
      <section class="card">
        <h2>3. Image Carousel</h2>
        <div class="content">
          <img :src="currentImage" alt="Carousel Image" class="carousel-image" />
          <div class="carousel-controls">
            <button @click="prevImage" class="btn">Previous</button>
            <button @click="nextImage" class="btn1">Next</button>
          </div>
        </div>
      </section>
    </main>
  </div>
</template>

<script>
export default {
  data() {
    return {
      count: 0,
      boxColor: '#C96868',
      images: [
        "https://www.teahub.io/photos/full/44-448523_kucing-anggora.jpg",
        "https://sahabatnesia.com/wp-content/uploads/2019/01/Gambar-Sasuke-dan-Naruto.jpg",
        "https://th.bing.com/th/id/OIP.XG4V_Zef8ZQf9fwpR2GruAHaEK?rs=1&pid=ImgDetMain",
        // 'https://picsum.photos/id/1018/400/300',
        // 'https://picsum.photos/id/1015/400/300',
        // 'https://picsum.photos/id/1019/400/300',
        // 'https://picsum.photos/id/1016/400/300',
        // 'https://picsum.photos/id/1021/400/300'
      ],
      currentImageIndex: 0
    }
  },
  computed: {
    currentImage() {
      return this.images[this.currentImageIndex]
    }
  },
  methods: {
    incrementCount() {
      this.count++
    },
    changeColor() {
      const colors = [
        '#C96868',
        '#FADFA1',
        '#FFF4EA',
        '#7EACB5',
        '#E57373',
        '#81C784',
        '#64B5F6',
        '#FFB74D',
        '#BA68C8'
      ]
      let newColor
      do {
        newColor = colors[Math.floor(Math.random() * colors.length)]
      } while (newColor === this.boxColor)
      this.boxColor = newColor
    },
    nextImage() {
      this.currentImageIndex = (this.currentImageIndex + 1) % this.images.length
    },
    prevImage() {
      this.currentImageIndex =
        (this.currentImageIndex - 1 + this.images.length) % this.images.length
    }
  }
}
</script>

<style>
:root {
  --primary-color: #000000;
  --secondary-color: #a8faa1;
  --background-color: #3210f1;
  --accent-color: #b612e8;
}

body {
  background-color: var(--background-color);
  color: #333;
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
}

#app {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
}

header {
  background-color: var(--primary-color);
  color: white;
  padding: 20px;
  text-align: center;
  /* position: sticky; */
  top: 0;
  z-index: 1000;
  border-radius: 50px ;
}

h1 {
  margin: 0;
}

main {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
  padding: 20px 0;
}

.card {
  background-color: white;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  padding: 20px;
}

h2 {
  color: var(--primary-color);
  margin-top: 0;
}

.content {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.btn {
  background-color: var(--accent-color);
  color: white;
  border: none;
  padding: 10px 20px;
  margin: 10px 0;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.btn1 {
  background-color: green;
  color: white;
  border: none;
  padding: 10px 20px;
  margin: 10px 0;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.btn:hover {
  background-color: var(--primary-color);
}

.count {
  font-size: 24px;
  font-weight: bold;
  margin: 10px 0;
  color: var(--primary-color);
}

.color-box {
  width: 100px;
  height: 100px;
  margin: 10px 0;
  border-radius: 8px;
  transition: background-color 0.3s;
}

.carousel-image {
  max-width: 100%;
  height: auto;
  border-radius: 8px;
}

.carousel-controls {
  display: flex;
  justify-content: space-between;
  width: 100%;
  margin-top: 10px;
}
</style>