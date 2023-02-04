<script setup>
import { reactive, ref, computed } from "vue";

//COMPONENTES
import ProductDisplay from "./components/ProductDisplay.vue";
import ReviewForm from "./components/ReviewForm.vue";
import ReviewList from "./components/ReviewList.vue";

//VARIABLES
const cart = ref([]);
const premiun = ref(false);
const reviews = [];
const contador = ref(0);

const productos = [
  {
    id: 1,
    nombre: "VENTILADOR DE TAMBOR USO INDUSTRIAL",
    precio: "1,850.00 + envio",
    garantia: "1 año",
    descripcion:
      "Ventilador de tambor tipo industrial de 24 pulgadas con 2 velocidades, ideal para bodegas, garajes, talleres, ferreterías, etc.",
    imagen: "https://picsum.photos/200/200",
    listaEspecificaciones: [
      {
        Voltaje: "b",
        Potencia: "a",
        Revoluciones: "z",
        Velocidades: "y",
        Peso: "x",
      },
    ],
  },
  {
    id: 2,
    nombre: 'Allanadora de concreto a gasolina 40" 6.5HP',
    precio: "8,950.00 + envio",
    garantia: "1 año",
    descripcion:
      "Este equipo es utilizado para un rápido y perfecto acabado de superficies de concreto de cualquier dimensión",
    imagen: "https://picsum.photos/200/200",
    listaEspecificaciones: [
      {
        Voltaje: "b",
        Potencia: "a",
        Revoluciones: "z",
        Velocidades: "y",
        Peso: "x",
      },
    ],
  },
  {
    id: 3,
    nombre: "WINCH ELECTRICO DE CABLE DE 6000LB",
    precio: "4,590.00 + envio",
    garantia: "1 año",
    descripcion:
      "Ideal para instalar en Jeeps, Camionetas, Pick-up, Camión Grúa, Cuatrimotos y equipos de arrastre como maquinaria agrícola",
    imagen: "https://picsum.photos/200/200",
    listaEspecificaciones: [
      {
        Voltaje: "b",
        Potencia: "a",
        Revoluciones: "z",
        Velocidades: "y",
        Peso: "x",
      },
    ],
  },
  {
    id: 4,
    nombre: "MOTOCULTOR A GASOLINA DE 7HP MARCA HOTECHE CON IMPLEMENTOS",
    precio: "9,995.00 + envio",
    garantia: "1 año",
    descripcion:
      "Motoazada/motocultor de gran calidad, con caja de cambio de 2 velocidades y 1 reversa.",
    imagen: "https://picsum.photos/200/200",
    listaEspecificaciones: [
      {
        Voltaje: "b",
        Potencia: "a",
        Revoluciones: "z",
        Velocidades: "y",
        Peso: "x",
      },
    ],
  },
];

//FUNCIONES
function update(id) {
  cart.value.push(id);
}

function addReview(review) {
  reviews.push(review);
  console.log(reviews);
}
</script>

<template>
<nav class="navbar navbar-expand-lg bg-dark navbar-dark">
  <div class="container-fluid">
    <span class="navbar-brand mb-0 h1">Importaciones JAH</span>
    <button
      class="navbar-toggler"
      type="button"
      data-bs-toggle="collapse"
      data-bs-target="#navbarSupportedContent"
      aria-controls="navbarSupportedContent"
      aria-expanded="false"
      aria-label="Toggle navigation"
    >
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">
        <li class="nav-item">
          <a class="nav-link active" href="">Inicio</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Catalogo</a>
        </li>
        <li class="nav-item dropdown">
          <a
            class="nav-link dropdown-toggle"
            href="#"
            role="button"
            data-bs-toggle="dropdown"
            aria-expanded="false"
            >Opciones</a
          >
          <ul class="dropdown-menu">
            <li><a class="dropdown-item" href="#">Tipo 1</a></li>
            <li><a class="dropdown-item" href="#">Tipo 2</a></li>
            <li><hr class="dropdown-divider" /></li>
            <li><a class="dropdown-item" href="#">Tipo 3</a></li>
          </ul>
        </li>
      </ul>
      <div class="d-flex">
        <form class="d-flex" role="search">
        <input
          type="search"
          class="form-control me-2"
          placeholder="Buscar"
          aria-label="Buscar"
        />
        <button class="btn btn-outline-success me-2" type="submit">
          Buscar
        </button>
      </form>
      <button class="btn btn-info position-relative">
        Carrito
        <span
          class="position-absolute top-0 start-100 translate-middle badge rounded-pill bg-warning"
        >
          {{ contador }}
          <span class="visually-hidden">carrito</span>
        </span>
      </button>
      </div>
      
    </div>
  </div>
</nav>

<div
  id="carouselExampleIndicators"
  class="carousel slide"
  data-bs-ride="true"
>
  <div class="carousel-indicators">
    <button
      type="button"
      data-bs-target="#carouselExampleIndicators"
      data-bs-slide-to="0"
      class="active"
      aria-current="true"
      aria-label="Slide 1"
    ></button>
    <button
      type="button"
      data-bs-target="#carouselExampleIndicators"
      data-bs-slide-to="1"
      aria-label="Slide 2"
    ></button>
    <button
      type="button"
      data-bs-target="#carouselExampleIndicators"
      data-bs-slide-to="2"
      aria-label="Slide 3"
    ></button>
  </div>
  <div class="carousel-inner">
    <div class="carousel-item active">
      <img
        src="https://picsum.photos/720/220"
        class="d-block w-100"
        alt="oferta1"
      />
    </div>
    <div class="carousel-item">
      <img
        src="https://picsum.photos/720/220"
        class="d-block w-100"
        alt="oferta2"
      />
    </div>
    <div class="carousel-item">
      <img
        src="https://picsum.photos/720/220"
        class="d-block w-100"
        alt="oferta3"
      />
    </div>
  </div>
  <button
    class="carousel-control-prev"
    type="button"
    data-bs-target="#carouselExampleIndicators"
    data-bs-slide="prev"
  >
    <span class="carousel-control-prev-icon" aria-hidden="true"></span>
    <span class="visually-hidden">Previous</span>
  </button>
  <button
    class="carousel-control-next"
    type="button"
    data-bs-target="#carouselExampleIndicators"
    data-bs-slide="next"
  >
    <span class="carousel-control-next-icon" aria-hidden="true"></span>
    <span class="visually-hidden">Next</span>
  </button>
</div>

<br />
<h3>Productos</h3>
<hr />

<div id="catalogo">
  <div class="row row-cols-auto row-cols-md-3">
    <div v-for="(producto, id) in productos" :key="producto.id" class="col">
      <div class="card red">
        <img :src="producto.imagen" class="card-img-top" alt="..." />
        <div class="card-body">
          <h5 class="card-title">{{ producto.nombre }}</h5>
          <p class="card-text">{{ producto.descripcion }}</p>
          <h4>Q. {{ producto.precio }}</h4>
          <button class="btn btn-success" @click="contador++">Agregar al carrito</button>
        </div>
      </div>
    </div>
  </div>
</div>

<hr />
<footer id="footer">
  <h6>Contacto: 5495-0434</h6>
  <h6>Mas informacion: correo@gmail.com</h6>
  <p>@AGB76</p>
  <a href="#">Facebook</a>
</footer>
</template>

<style>
#catalogo {
  background: rgba(255, 255, 255, 0.25);
  box-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.37);
  backdrop-filter: blur(4px);
  -webkit-backdrop-filter: blur(4px);
  border-radius: 10px;
  border: 1px solid rgba(255, 255, 255, 0.18);
}

.carrousel {
  height: 50px;
}

.red {
  border: solid red 2px !important;
  margin-left: 15px;
}
</style>
