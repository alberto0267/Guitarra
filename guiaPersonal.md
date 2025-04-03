En el caso de app.vue

es mejor ponerlo en onMounted:

state.guitarras = db dentro de onMounted() Si los datos se cargan después, como desde una API.

state = reactive({ guitarras: db }) directamente Si los datos ya están disponibles en el momento de cargar el componente (como con un import estático).

\*\*Directivas en vue
Son atributos html con cierta funcionalidad de js

## 🎯 v-bind

**Enlaza datos dinámicos a atributos HTML.**

```html
<img v-bind:src="imagenUrl" />
<!-- Atajo -->
<img :src="imagenUrl" />

<li v-for="(item, index) in lista" :key="index">{{ item }}</li>

<p v-if="activo">Está activo</p>
<p v-else>Está inactivo</p>

<p v-show="visible">Visible o no</p>

<input v-model="nombre" />
<textarea v-model="comentario"></textarea>
```

"NOTE:"

v-bind:src="/img/ + guitarra.imagen + '.jpg'"
asi se mete una iamgen cuando llamas de json con vue

v-on sirve para escuchar eventos del navegador y ejecutar funciones cuando esos eventos ocurren.

Es como decirle a Vue:

“Cuando el usuario haga esto (click, input, submit...), ejecuta esta función.”

"NOTE:"
los props se usar para mandarle del padre al hijo

const props = defineProps({
guitarra: {
type: Object,
required: true,
},
});

"NOTE:"
Lo que hace este código es calcular el total a pagar por todos los productos en el carrito de compras, multiplicando la cantidad de cada producto por su precio y sumando todo. Este valor se guarda en totalPagar, y si algún producto en el carrito cambia, totalPagar se actualizará automáticamente gracias a que es una propiedad computada.

const totalPagar = computed(()=>{
return props.carrito.reduce((total,producto) => total + (producto.cantidad \* producto.precio),0);

})
