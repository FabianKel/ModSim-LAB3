## Ejercicio 1
### **Defina y compare**
1. Retraso de primer orden vs. cadena de retrasos

    | Retraso de primer orden | Cadena de retrasos |
    |------------------------ | ------------------ |
    | Modelo simple de ajuste gradual. | Modelo compuesto por varias etapas secuenciales. |
    | Se representa con una ecuación diferencial de primer orden (ej. $dx/dt = (objetivo - x)/\tau$). | Se modela como una serie de variables intermedias, cada una con su propio retardo. |
    | Más rápido pero menos realista en procesos biológicos complejos. | Más realista al simular tiempos de incubación o procesamiento escalonado.|


2. Fuerza de infección (λ) vs. número básico de reproducción (R₀)

    | Fuerza de infección $\lambda = \beta c \frac{I}{N}$  |  Número básico de reproducción $R_0$ |
    | ---  |  --- |
    | Tasa instantánea de contagio para un susceptible.    |  Número esperado de infecciones secundarias causadas por un infectado en una población totalmente susceptible. |
    | Depende del número actual de infectados y contactos. |  Es un valor promedio constante al inicio del brote. |
    | Tiene interpretación de riesgo y de tasa de transmisión. | Se usa para determinar el potencial de propagación.|


### **Explique por qué**
1. El sarampión requiere una cobertura de vacunación superior al 95%, mientras que el ébola solo necesita
aproximadamente el 50%.
    - Esto se debe a que el número básico de reproducción $R_0$ del sarampión es extremadamente alto (entre **12** y **18**), lo que implica que una sola persona puede infectar a muchas otras. Para evitar brotes, se necesita una inmunidad colectiva muy alta:
    $$
    Cobertura = 1 - \frac{1}{R_0}
    $$

    - Para el sarampión $(R_0 ≈ 15) → 1 - 1/15 = 0.933 ≈ 93\%$
    - Para el ébola ($R_0 ≈ 2) → 1 − 1/2 = 0.5 = 50\%$
    Es por eso que el sarampión exige una cobertura de vacunación mayor para alcanzar el umbral de inmunidad de grupo.
<br>
2. Las exigencias de vacunación alteran los equilibrios de Nash en modelos de teoría de juegos.
    - .

**Defina y compare los mecanismos de:**
- La lotería de vacunas de Ohio (conductual).
- Las exigencias de ingreso escolar en Francia (estructural)