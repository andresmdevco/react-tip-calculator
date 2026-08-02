# 🧾 React Tip Calculator

Calculadora de consumo y propina construida con **React**, **TypeScript** y **Tailwind CSS**. Permite armar una orden a partir de un menú, calcular el subtotal, aplicar un porcentaje de propina y obtener el total a pagar.

## 🌐 Demo

🔗 [https://tip-calculator-andresmdevco.netlify.app/](https://tip-calculator-andresmdevco.netlify.app/)

## 👀 Vista previa
https://github.com/user-attachments/assets/df5ba1d7-cca5-46d3-a89b-a905016446ab

## 🛠️ Tecnologías Utilizadas

![React](https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)

- React 19
- Tailwind CSS 4

## ✨ Características

- 📋 Menú de productos con precio, listo para agregar a la orden con un clic.
- ➕ Suma automática de cantidades si el producto ya está en la orden.
- ❌ Eliminación de productos individuales de la orden.
- 💰 Cálculo de propina con opciones predefinidas (10%, 20%, 50%).
- 🧮 Cálculo en tiempo real de subtotal, propina y total, optimizado con `useMemo`.
- 🔄 Botón para guardar/finalizar la orden y reiniciar el estado.
- 💵 Formato de moneda con `Intl.NumberFormat`.
- 📱 Diseño responsive con Tailwind CSS.
- **Estado global con `useReducer`** — Todo el estado de la orden (`order`, `tip`) se gestiona desde un único reducer.
- **Acciones tipadas con discriminated unions** — Cada acción (`add-item`, `remove-item`, `add-tip`, `place-order`) tiene su propio `payload` tipado.
- **Lógica extraída a un reducer** — `order-reducer.ts` centraliza el estado y las transiciones de la orden, desacoplándolas de la UI.

## 📂 Archivos principales

| Archivo | Descripción |
|---|---|
| `App.tsx` | Componente raíz. Inicializa el estado con `useReducer` y distribuye `state` y `dispatch` a los componentes hijos. |
| `order-reducer.ts` | Define el reducer (`orderReducer`), el estado inicial (`initialState`) y las acciones tipadas (`OrderActions`) que gestionan la orden y la propina. |
| `MenuItem.tsx` | Muestra un producto del menú y dispara la acción `add-item` al hacer clic. |
| `OrderContents.tsx` | Renderiza los productos agregados a la orden y dispara `remove-item` para eliminarlos. |
| `TipPercentageForm.tsx` | Formulario de radios para seleccionar el porcentaje de propina; dispara `add-tip`. |
| `OrderTotals.tsx` | Calcula subtotal, propina y total con `useMemo`, y dispara `place-order` al guardar. |
| `data/db.ts` | Lista de productos disponibles (`id`, `name`, `price`). |
| `helpers/index.ts` | Función `formatCurrency` para formatear valores como moneda. |
| `types/index.ts` | Tipos `MenuItem` y `OrderItem` compartidos por la aplicación. |

## 🧠 Cómo funciona

1. El **menú** (`data/db.ts`) contiene la lista de productos disponibles, cada uno con `id`, `name` y `price`.
2. `App.tsx` inicializa el estado con `useReducer(orderReducer, initialState)`, obteniendo `state` (con `order` y `tip`) y `dispatch`, que se distribuyen como props a los componentes hijos.
3. Al hacer clic en un producto (`MenuItem.tsx`), se dispara la acción `add-item`, que el `orderReducer` procesa así:
   - Si el producto ya existe en la orden, incrementa su `quantity`.
   - Si no existe, lo agrega con `quantity: 1`.
4. `OrderContents.tsx` muestra los productos agregados, su cantidad y subtotal por producto, y dispara `remove-item` para eliminarlos.
5. `TipPercentageForm.tsx` permite seleccionar el porcentaje de propina (10%, 20% o 50%) mediante inputs de tipo radio, disparando la acción `add-tip`.
6. `OrderTotals.tsx` calcula, usando `useMemo`, el **subtotal**, el **monto de la propina** y el **total a pagar**, y muestra el botón para guardar la orden.
7. Al guardar la orden, se dispara `place-order`, y el reducer reinicia el estado (`order` vacío y `tip` en 0).

## 📚 Conceptos practicados

- Migración de `useState` + custom hook a `useReducer` para centralizar el estado
- Modelado de acciones con discriminated unions (`OrderActions`) para tipar `type` y `payload` de forma segura
- Uso de `Dispatch<OrderActions>` para tipar la función `dispatch` recibida por los componentes hijos
- Actualizaciones inmutables del estado dentro del reducer (`map`, `filter`, spread operator)
- Tipado de componentes, props y funciones con TypeScript
- Definición de tipos reutilizables (`MenuItem`, `OrderItem`) mediante intersección de tipos (`&`)
- Estado derivado con `useMemo` para evitar recálculos innecesarios (`subtotalAmount`, `tipAmount`, `totalAmount`)
- Renderizado condicional según el contenido del estado (orden vacía vs. orden con productos)
- Formularios controlados con inputs `radio` sincronizados al estado (`checked`, `onChange`)
- Formato de moneda con `Intl.NumberFormat`

## 🚀 Cómo ejecutar el proyecto

1. Clonar el repositorio:

```bash
   git clone https://github.com/andresmdevco/tip-calculator.git
   cd tip-calculator
```

2. Instalar las dependencias:

```bash
   npm install
```

3. Ejecutar el proyecto en modo desarrollo:

```bash
   npm run dev
```

4. Abrir [http://localhost:5173](http://localhost:5173) en el navegador.