# push_swap

Un proyecto de la escuela 42 que ordena una pila de enteros usando dos pilas y un conjunto limitado de operaciones, generando la secuencia más corta posible de movimientos.

## Resumen del Proyecto

**push_swap** recibe una lista de enteros como argumentos, los carga en una pila (stack_a) e imprime por salida estándar la secuencia ordenada de operaciones necesarias para ordenar stack_a con el menor número de movimientos posible. Se dispone de una segunda pila auxiliar (stack_b). El programa no imprime valores — únicamente los nombres de las operaciones.

El programa emplea dos estrategias:
- **Pila pequeña** (≤ 5 elementos): ordenación por inserción optimizada.
- **Pila grande** (> 5 elementos): algoritmo voraz/radix basado en índices.

## Habilidades Adquiridas

- Diseño de algoritmos y análisis de complejidad (algoritmos de ordenación)
- Manipulación de listas doblemente enlazadas en C
- Operaciones sobre pilas y diseño de estructuras de datos
- Análisis de argumentos, validación de entrada y manejo de errores
- Gestión de memoria y programación sin fugas en C
- Trabajo bajo flags de compilación estrictos (`-Wall -Wextra -Werror`)
- Organización de proyectos con Makefile e integración de biblioteca externa (libft)

## Compilación y Ejecución

Todos los comandos deben ejecutarse desde el directorio `pushswap/`.

```bash
cd pushswap

# Compilar el proyecto (compila primero libft y luego push_swap)
make

# Eliminar los archivos objeto
make clean

# Eliminar archivos objeto y el binario
make fclean

# Recompilar completamente
make re
```

Tras una compilación exitosa, el binario `push_swap` se crea dentro de `pushswap/`.

### Uso

```bash
# Ordenar una lista de enteros — imprime la secuencia de operaciones
./push_swap 3 1 4 1 5 9 2 6

# Pasar la salida al checker incluido para verificar la corrección
./push_swap 3 1 4 1 5 9 2 6 | ./checker_linux 3 1 4 1 5 9 2 6

# Los números también pueden pasarse como una cadena entre comillas
./push_swap "3 1 4 1 5 9 2 6"
```

El programa termina en silencio (sin salida) cuando la entrada ya está ordenada o sólo se proporciona un número. Escribe `Error` en la salida de error estándar ante entradas no válidas (no enteros, duplicados, valores fuera de rango).

## Estructura del Proyecto

```
pushswap/
├── Makefile
├── pushswap.h          # Cabecera — structs (t_node, t_args_info) y prototipos
├── main.c              # Punto de entrada, asignación de índices, despachador de ordenación
├── case_smll.c         # Algoritmo de ordenación para ≤ 5 elementos
├── case_lrge.c         # Algoritmo de ordenación para > 5 elementos
├── checker_linux       # Binario checker precompilado (Linux)
├── libft/              # Biblioteca C personalizada (ft_printf, libft)
├── operations/
│   ├── swap.c          # sa, sb, ss
│   ├── push.c          # pa, pb
│   ├── rotate.c        # ra, rb
│   └── rr.c            # rr, rra, rrb, rrr
└── parsing/
    ├── validate_args.c
    ├── parse_stack.c
    ├── parsing_plus.c
    ├── parsing_plus1.c
    └── parsing_plus2.c
```

### Operaciones Disponibles

| Operación | Descripción |
|-----------|-------------|
| `sa` / `sb` | Intercambia los dos elementos superiores de stack_a / stack_b |
| `ss` | `sa` y `sb` simultáneamente |
| `pa` / `pb` | Empuja el tope de stack_b a stack_a / y viceversa |
| `ra` / `rb` | Rota stack_a / stack_b hacia arriba (tope → fondo) |
| `rr` | `ra` y `rb` simultáneamente |
| `rra` / `rrb` | Rotación inversa de stack_a / stack_b (fondo → tope) |
| `rrr` | `rra` y `rrb` simultáneamente |

## Autor

**ruortiz-** — [42 School](https://42.fr)
