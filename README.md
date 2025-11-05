# Trabajo Final - Análisis y Diseño de Algoritmos

**Problema asignado (cédula termina en 3): Camino mínimo en una matriz (grid)**  
Encuentra el costo mínimo desde `(0,0)` hasta `(n-1,n-1)` moviéndote **solo Derecha o Abajo**.  
Los costos están en una matriz `n x n` de enteros no negativos.

> **Salida del programa (sin acentos):** se registra en `results/resultados.csv` con columnas:  
> `case_id,n,algorithm,cost,time_ms`

---

## Estructura
```
TrabajoFinal_Algoritmos/
├─ README.md
├─ data/
│  └─ casos_prueba.txt
├─ results/
│  └─ resultados.csv          (se genera al ejecutar)
├─ src/
│  ├─ backtracking.cpp
│  ├─ greedy.cpp              (Dijkstra)
│  ├─ programacion_dinamica.cpp (Bottom-Up)
│  └─ main.cpp
├─ report/
│  └─ Informe.md              
└─ video/
   └─ presentacion.mp4        (coloca tu video)
```

---

## Compilar (C++17)

```bash
cd src
 g++ -O2 -std=c++17 main.cpp backtracking.cpp greedy.cpp programacion_dinamica.cpp -o caminos
```

---

## Ejecutar

```bash
# Ejecuta los 4 algoritmos y escribe CSV
./caminos all ../data/casos_prueba.txt ../results/resultados.csv
```

---

## Formato de entrada (`data/casos_prueba.txt`)

- Cada caso inicia con `n` y luego `n` lineas con `n` enteros (costo >= 0).

Ejemplo:
```
3
1 3 1
1 5 1
4 2 1
```

---

## Complejidades

- **Backtracking (Derecha/Abajo, poda por mejor actual):** En el peor caso, explora ~`C(2n-2, n-1)` caminos (exponencial); con poda, suele mejorar en matrices con grandes costos.
- **Dijkstra (Greedy con cola de prioridad):** `O(n^2 log n)` sobre grid `n x n` (considerando 2 aristas por nodo en promedio cuando solo derecha/abajo; con 4 direcciones: ~4 aristas/nodo).
- **PD Bottom-Up:** `O(n^2)` tiempo y `O(n^2)` espacio (se puede optimizar a `O(n)` por fila).
- **DyV Top-Down con memo:** mismas cotas que PD (`O(n^2)` tiempo y espacio); la recurrencia es  
  `T(i,j) = cost[i][j] + min(T(i+1,j), T(i,j+1))` con memo. Sin memo: `O(2^{2n})`.

---
