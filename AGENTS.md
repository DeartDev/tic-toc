# AGENTS.md - Guía para Agentes de Código

## Descripción del Proyecto

Este es un proyecto simple de **Tic Tac Toe (3 en Raya)** implementado como un único archivo HTML con CSS y JavaScript embebidos. No requiere compilación ni herramientas de build.

## Tecnologías

- HTML5
- CSS3 (estilos embebidos)
- JavaScript Vanilla (ES6+)

## Validación y Pruebas

### Comandos Disponibles

Este proyecto no tiene un sistema de build configurado. Para validar el código:

**Validación manual:**
```bash
# Abrir en navegador (Termux)
termux-open tic_toc.html

# O simplemente abrir el archivo HTML en cualquier navegador
```

**Validación con herramientas externas:**
- Usa extensiones de VSCode como "Live Server" o "HTML CSS Support"
- Validador HTML: https://validator.w3.org/
- ESLint para JavaScript (si se configura)

### Pruebas

No hay suite de tests configurada. Para probar:
1. Abre `tic_toc.html` en un navegador
2. Prueba todos los flujos del juego:
   - Jugador X hace clic en celda
   - Jugador O hace clic en celda
   - Victoria en cada línea posible
   - Empate
   - Reiniciar tablero
   - Ingresar nombres de jugadores

## Estilo de Código

### HTML

- Usar indentación con 2 espacios
- Siempre incluir atributos `lang` y `charset`
- Etiquetas en minúsculas
- Valores de atributos entre comillas
- Cerrar todas las etiquetas

```html
<!-- Correcto -->
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Título</title>
</head>
<body>
  <div class="container">
    <p>Contenido</p>
  </div>
</body>
</html>
```

### CSS

- Selectores en una línea cuando sea simple
- Propiedades con indentación de 2 espacios
- Usar variables CSS para colores repetidos
- Agrupar propiedades relacionadas
- Preferir clases sobre IDs para reutilización

```css
/* Correcto */
body{
  font-family: Arial, sans-serif;
  background:#111;
  color:white;
}

.container{
  display:flex;
  gap:10px;
}

/* Evitar */
body { font-family: Arial; background: #111; }
```

### JavaScript

#### Variables y Funciones

- Usar `const` por defecto, `let` solo cuando sea necesario
- Nombres en camelCase para funciones y variables
- Nombres descriptivos que expliquen el propósito
- Declarar variables al inicio de su ámbito

```javascript
// Correcto
const board = document.getElementById("board")
let currentPlayer = "X"

function createBoard() {
  // ...
}

function handleCellClick(event) {
  // ...
}

// Evitar
var x = document.getElementById("board")  // usar const/let
function crearTablero() { }  // usar inglés o camelCase consistente
```

#### Estructura de Control

- Siempre usar llaves `{}` incluso para bloques de una línea
- Usar operadores ternarios para condiciones simples
- Preferir `forEach` sobre `for` tradicional cuando sea posible

```javascript
// Correcto
if(condition) {
  doSomething()
}

const status = gameActive ? "Activo" : "Inactivo"

boardState.forEach((cell, index) => {
  // ...
})

// Evitar
if(condition) doSomething()  // sin llaves

for(let i=0; i<arr.length; i++) { }  // preferír forEach
```

#### DOM y Event Listeners

- Usar `addEventListener` en lugar de atributos inline onclick
- Cachear referencias a elementos DOM
- Usar `dataset` para datos personalizados

```javascript
// Correcto
const board = document.getElementById("board")
div.addEventListener("click", handleMove)
div.dataset.index = index

// Evitar
<button onclick="restart()">  // usar addEventListener
```

#### Concatenación de Strings

- Usar template literals (backticks) para strings dinámicos

```javascript
// Correcto
statusText.textContent = `Turno de ${playerName}`
const message = `${player} gana!`

// Evitar
statusText.textContent = "Turno de " + playerName
```

### Convenciones de Nombres

| Tipo | Convención | Ejemplo |
|------|------------|---------|
| Variables | camelCase | `currentPlayer`, `boardState` |
| Constantes | UPPER_SNAKE_CASE | `MAX_SCORE`, `DEFAULT_NAME` |
| Funciones | camelCase | `createBoard()`, `checkWinner()` |
| Clases CSS | kebab-case | `.score-board`, `.game-cell` |
| IDs | camelCase | `playerOne`, `scoreDisplay` |

### Comentarios

- Agregar comentarios en español o inglés (mantener consistencia)
- Comentar funciones complejas o algoritmos
- NO agregar comentarios obvios

```javascript
// Correcto (función compleja)
/**
 * Verifica todas las combinaciones ganadoras
 * @returns {boolean} true si hay ganador
 */
function checkWinner() { }

// Incorrecto (comentario obvio)
// Crear tablero
function createBoard() { }
```

### Manejo de Errores

- Usar try-catch para operaciones que pueden fallar
- Validar inputs antes de usarlos
- Proporcionar mensajes de error claros

```javascript
// Correcto
try {
  const data = JSON.parse(userInput)
  if (!data) throw new Error("Datos inválidos")
} catch (error) {
  console.error("Error:", error.message)
}

// Evitar
try { JSON.parse(userInput) } catch(e) { }  // ignorar errores
```

### Imports y Dependencias

- Este proyecto no usa módulos externos
- Si se agregaran, usar imports explícitos

```javascript
// Si se usa ES modules
import { helperFunction } from './utils.js'
```

## Estructura de Archivos Recomendada

Si el proyecto crece, organizar así:

```
/proyecto
  /src
    /js
      game.js
      utils.js
    /css
      styles.css
  /assets
    /images
  index.html
  README.md
  AGENTS.md
```

## Git y Control de Versiones

- Hacer commits frecuentemente con mensajes descriptivos
- No hacer commit de archivos generated o node_modules
- Usar .gitignore para archivos temporales

## Notas Adicionales

- Este proyecto fue desarrollado usando **Termux** (terminal para Android) y **Neovim** con **LazyVim**
- El código existente usa un estilo consistente que debe mantenerse
- La idioma principal del proyecto es español (comentarios, UI)
