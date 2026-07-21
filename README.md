# 🧾 React Tip Calculator

Calculadora de consumo y propina construida con **React**, **TypeScript** y **Tailwind CSS**. Permite armar una orden a partir de un menú, calcular el subtotal, aplicar un porcentaje de propina y obtener el total a pagar.

## 🌐 Demo

🔗 [https://tip-calculator-andresmdevco.netlify.app/](https://tip-calculator-andresmdevco.netlify.app/)

## 👀 Vista previa
https://github.com/user-attachments/assets/df5ba1d7-cca5-46d3-a89b-a905016446ab

## 🛠️ Tecnologías utilizadas

![React](https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)

## ✨ Características

- 📋 Menú de productos con precio, listo para agregar a la orden con un clic.
- ➕ Suma automática de cantidades si el producto ya está en la orden.
- ❌ Eliminación de productos individuales de la orden.
- 💰 Cálculo de propina con opciones predefinidas (10%, 20%, 50%).
- 🧮 Cálculo en tiempo real de subtotal, propina y total, optimizado con `useMemo`.
- 🔄 Botón para guardar/finalizar la orden y reiniciar el estado.
- 💵 Formato de moneda con `Intl.NumberFormat`.
- 📱 Diseño responsive con Tailwind CSS.


## 🧠 Cómo funciona

1. El **menú** (`data/db.ts`) contiene la lista de productos disponibles, cada uno con `id`, `name` y `price`.
2. Al hacer clic en un producto (`MenuItem.tsx`), se agrega a la orden mediante el hook `useOrder`, que:
   - Si el producto ya existe en la orden, incrementa su `quantity`.
   - Si no existe, lo agrega con `quantity: 1`.
3. `OrderContents.tsx` muestra los productos agregados, su cantidad y subtotal por producto, con opción de eliminarlos.
4. `TipPercentageForm.tsx` permite seleccionar el porcentaje de propina (10%, 20% o 50%) mediante inputs de tipo radio.
5. `OrderTotals.tsx` calcula, usando `useMemo`, el **subtotal**, el **monto de la propina** y el **total a pagar**, y muestra el botón para guardar la orden.
6. Al guardar la orden, el estado se reinicia (`order` vacío y `tip` en 0).

## 📚 Conceptos practicados
 
- Tipado de componentes, props y funciones con TypeScript
- Definición de tipos reutilizables (`MenuItem`, `OrderItem`) mediante intersección de tipos (`&`)
- Extracción de lógica de estado a un custom hook (`useOrder`) para separar lógica de presentación
- Estado derivado con `useMemo` para evitar recálculos innecesarios (`subtotalAmount`, `tipAmount`, `totalAmount`)
- Actualización inmutable de estado con `map`, `filter` y spread operator (`...`)
- Comunicación entre componentes mediante props tipadas y funciones callback
- Renderizado condicional según el contenido del estado (orden vacía vs. orden con productos)
- Formularios controlados con inputs `radio` sincronizados al estado (`checked`, `onChange`)
- Formato de moneda con `Intl.NumberFormat`


## 🚀 Cómo ejecutar el proyecto

1. Clonar el repositorio:

   ```bash
   git clone https://github.com/andresmdevco/react-tip-calculator.git
   cd react-tip-calculator
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

