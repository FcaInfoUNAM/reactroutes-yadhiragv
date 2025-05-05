# Laboratorio Rutas en react

Este laboratorio tiene el objetivo demostrar como se importan y se utilizan lar rutas para el front con react
## Requisitos Previos

1. Vite
2. Crear una cuenta en [GitHub](https://github.com/).
3. Utilizar un codespace de git hub o un dev container con docker en tu computadora de forma local

---

## Instrucciones Paso a Paso

### 1. Cargando el proyecto

1.1  Instalar los paquetes del proyecto y tailwind

``` bash
npm install
npm install react-router-dom
```

1.2 Ejecuta react en modo de desarrollo

```
npm run dev -- --host
```

> [!IMPORTANT]
> Se desplegará un pop up en la parte inferior derecha con el mensaje: La aplicación que se ejecuta en el puerto 5173 está disponible. 
> [Ver todos los puertos reenviados] (command:~remote.forwardedPorts.focus) [Abrir en el navegador] [Hacer público] Debes dar click en hacer público

> [!NOTE]
>Si no lograste darle click o no te apareció el pop up en la cinta de terminal, ve a la opción puertos, busca el puerto 5173, da click derecho, selecciona visibilidad de puerto y selecciona público

Abre el proyecto en el navegador web

### 2. Importar componentes

2.1 Revisa los componentes y revisa para que sirve cada uno, puedes probar  mandandolos a llmara en ```src/App.jsx```
2.2 Agrega los componentes y el modulo de ruteo en el archivo ```src/App.jsx```

```jsx
import { BrowserRouter, Routes, Route } from "react-router-dom";
import About from './About';
import ContactUs from './ContactUs';
import TeamSection from './TeamSection'; 

```
2.3 agrega un comentario en el archivo Nav explicando como funciona map en este caso.

### 3. Propiedades de un componente

3.1 Abre el archivo ```App.jsx``` y agrega en el return al inicio el siguiente código
```jsx
//...
function App({props}){
  //...
  return(
    //...
    <BrowserRouter>
      <Routes>
        <Route path="Contact" element={<ContactUs/>} />
        <Route path="Team" element={<TeamSection/>} />
        <Route path="About" element={<About/>} />
      </Routes>
    </BrowserRouter>
    //...
  );
  //..
}
```
Revisa la siguiente documentación:  [routes w3s](https://www.w3schools.com/react/react_router.asp)

3.2 prueba agregar en la url de tu navegador agregando /Contact o /Team
> [!NOTE]
> React renderiza unicamente el contenido del componente App ya que Nav se manda a llamar en main.

3.3 implementa el map de los productos con el componente Card en la ruta / y borra las lineas que mandan a llamar a los componentes fuera del route

```jsx
//...
function App({props}){
  //...
  return(
    //...
        <Route path="/" element={
          <div key="product-grid" className="bg-orange-500 p-8 grid grid-cols-4 gap-4">      
            {products.map(e=>
              <div key={e.model+"div"}><Card key={e.model} title={e.name} paragraph={e.properties} image={e.b64Image} model={e.model}/></div>)}
              </div>
            }
        />
    //...
    {/* ESTO ES LO QUE SE DEBE BORRAR
    <div key="product-grid" className="bg-orange-500 p-8 grid grid-cols-4 gap-4">      
        {products.map(e=><div key={e.model+"div"}><Card key={e.model} title={e.name} paragraph={e.properties} image={e.b64Image} model={e.model}/></div>)}
    </div>
    <div>
    <ContactUs/>
    <TeamSection/>
    <About/>
    </div> */}
  );
  //..
}
```


### 4. Reto

Crea un componente Llamado NotFound que muestre el error 404 que se ve usualmente en sitios web y mandalo allamar con la ruta * en ```App.jsx``` en el apartado de rutas

### 5. Guarda los cambios y subelos al repositorio

Guarda los cambios en el historial del repositorio con un commit:

```bash
cd ..
git add my-app
git commit -m "propiedades de los componentes"
git push origin main
```
 > [!TIP]
 > Documentación instalación tailwind: https://tailwindcss.com/docs/installation/using-vite

 > [!TIP]
 > Documentación ejemplos tailwind react: https://tailwindcss.com/plus/ui-blocks/preview
