﻿# proyectocodehouse
//*/*Selectores
// let nombre = document.querySelector("#nombre");
let estado = document.querySelector("#estado");
let nombre = document.querySelector("#nombre");
let modelo = document.querySelector("#modelo");
document.addEventListener("DOMContentLoaded", () => {
  filtrarCarro(carros);
});

const resultadoBusqueda = {
  nombre: "",
  estado: "",
  modelo: "",
  precio: "",
};
/**Eventos */

// nombre.addEventListener("input", atraparDato);
estado.addEventListener("input", (e) => {
  resultadoBusqueda.estado = e.target.value;
  console.log(resultadoBusqueda);
  filtrarCarro();
  console.log(resultadoBusqueda);
});

nombre.addEventListener("input", (e) => {
  resultadoBusqueda.nombre = e.target.value;
  console.log(resultadoBusqueda);
  filtrarCarro();
  console.log(resultadoBusqueda);
});
modelo.addEventListener("input", (e) => {
  resultadoBusqueda.modelo = e.target.value;
  console.log(resultadoBusqueda);
  filtrarCarro();
  console.log(resultadoBusqueda);
});

function mostrarCarros(carros) {
  resetearInfo();
  let carrosContenido = document.querySelector("#carros-contenido");

  carros.forEach((carro) => {
    let carroInfo = document.createElement("p");
    carroInfo.innerHTML = `
  <p> nombre:  ${carro.nombre} || estado: ${carro.estado} || modelo: ${carro.modelo} || ${carro.precio}</p>
  `;
    carrosContenido.appendChild(carroInfo);
  });
}

function filtrarEstado(carro) {
  if (resultadoBusqueda.estado) {
    return carro.estado === resultadoBusqueda.estado;
  }
  return carro;
}

function filtrarCarro() {
  let resultado = carros.filter(filtrarEstado);
  console.log(resultado);
  if (resultado.length) {
    mostrarCarros(resultado);
  } else {
    console.log("no were results found");
  }
}

function resetearInfo() {
  let carrosContenido = document.querySelector("#carros-contenido");
  carrosContenido.innerHTML = ``;
}

for (let i = 2000; i < 2023; i++) {
  const modelosGenerador = document.createElement("option");
  modelosGenerador.innerText = i;
  modelosGenerador.value = i;
  document.querySelector("#modelo").appendChild(modelosGenerador);
}
/**Cuestion de precios */
// for (let i = 55000; i < 600000; i) {
//   const modelosGenerador = document.createElement("option");

//   modelosGenerador.innerText = i;
//   modelosGenerador.value = i;
//   document.querySelector("#modelo").appendChild(modelosGenerador);
//   i += 1000;
// }
