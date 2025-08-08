# **Laboratorio 3**<br>**Modelación y Simulación**

**Sección 20**

- Monica Salvatierra - 22249
- Derek Arreaga - 22537
- Paula Barillas - 22764

>Link del repositorio: https://github.com/FabianKel/ModSim-LAB3

## **Partes individuales:**
- [Ejercicio 1](ejercicio1.ipynb)
- [Ejercicio 2](ejercicio2.ipynb)
- [Ejercicio 3](ejercicio3.ipynb)

---
## [**Ejercicio 1**](ejercicio1.ipynb)
### **Defina y compare**
1. Retraso de primer orden vs. cadena de retrasos

    | Retraso de primer orden | Cadena de retrasos |
    |------------------------ | ------------------ |
    | Modelo simple de ajuste gradual. | Modelo compuesto por varias etapas secuenciales. |
    | Se representa con una ecuación diferencial de primer orden ( ej. $\frac{dx}{dt} = \frac{(objetivo - x)}{\tau}$ ). | Se modela como una serie de variables intermedias, cada una con su propio retardo. |
    | Respuesta más rápida pero menos realista para procesos biológicos complejos. | Más realista al simular tiempos de incubación o procesamiento escalonado.|

<br>

2. Fuerza de infección ($\lambda$) vs. número básico de reproducción ($R_o$)

    | Fuerza de infección $\lambda = \beta c \frac{I}{N}$  |  Número básico de reproducción $R_0$ |
    | ---  |  --- |
    | Tasa instantánea de contagio para un susceptible.    |  Número esperado de infecciones secundarias causadas por un infectado en una población totalmente susceptible. |
    | Depende del número actual de infectados y contactos. |  Es un valor promedio constante al inicio del brote. |
    | Tiene interpretación de riesgo y de tasa de transmisión. | Se usa para estimar el potencial de propagación y el umbral de inmunidad de grupo.|
### **Explique por qué**
1. El sarampión requiere una cobertura de vacunación superior al 95%, mientras que el ébola solo necesita
aproximadamente el 50%.
    - Esto se debe a que el número básico de reproducción $R_0$ del sarampión es extremadamente alto (entre **12** y **18**), lo que implica que una sola persona puede infectar a muchas otras. Para evitar brotes, se necesita una inmunidad colectiva muy alta:
    $$
    \text{Cobertura} = 1 - \frac{1}{R_0}
    $$

    - Para el sarampión $(R_0 \thickapprox 15) → 1 - 1/15 = 0.933 \thickapprox 93\%$
    - Para el ébola ($R_0 \thickapprox 2) → 1 − 1/2 = 0.5 = 50\%$
            
        Por eso el sarampión requiere coberturas cercanas o superiores al 95% para prevenir brotes, mientras que el ébola necesita aproximadamente el 50%.

<br>

2. Las exigencias de vacunación alteran los equilibrios de Nash en modelos de teoría de juegos.
    - En modelos de teoría de juegos aplicados a vacunación, los individuos deciden si vacunarse o no en función del riesgo percibido y del comportamiento de los demás. Sin exigencias, muchos pueden optar por ser "free-riders", que son los que aprovechan la inmunidad de grupo sin vacunarse.

    - Entonces al imponer exigencias estructurales, se eliminan esas opciones, modificando los incentivos del juego. Lo que rompe el equilibrio subóptimo de no vacunarse, llevando al sistema a un nuevo equilibrio con mayor cobertura.
    
### **Defina y compare los mecanismos de:**
* La lotería de vacunas de Ohio (conductual).
    - Es una estrategia de tipo incentivo positivo basada en comportamiento.
    - Ofrecía la oportunidad de ganar dinero cada semana si las personas se vacunaban voluntariamente.
    - Buscaba motivar la vacunación mediante intervención económica.

* Las exigencias de ingreso escolar en Francia (estructural)
    - Esta estrategia consistía en dejar acceder a la educación únicamente a los jóvenes que estaban vacunados.
    - No era opcional para los estudiantes, ya que los privaban de sus estudios de no vacunarse.
    - Se cambiaron las reglas del sistema en lugar de motivar por una recompensa. Es con una intervención no económica.

---

## [**Ejercicio 2**](ejercicio2.ipynb)
### **Considere lo siguiente, analice y responda:**
#### Escenario 1

Un país con una cobertura de vacunación contra la COVID-19 del **60%** observa un aumento del $R_t$ de $\bold{0,8}$ a $\bold{1,5}$ tras la
aparición de una nueva variante.
- ¿Cuáles son los dos factores que probablemente causaron este aumento?
        <br>
    1. **Aumento de la transmisibilidad de la nueva variante:** 
        La variante puede portar mutaciones que aumenten la probabilidad de contagio por contacto, haciendo que el COVID-19 se transmita con mayor facilidad y por consecuencia, elevar $\beta$. Si cada caso contagia a más personas en promedio, $R_t$ aumentaría aunque las medidas sigan igual.
        <br>
    2. **Reducción de la efectividad o de la inmunidad de la población:** 
        Si la variante evade parcialmente los anticuerpos generados por vacunas o infecciones previas, la protección efectiva disminuye. Con la misma cobertura del 60%, pero con menor efectividad, hay más personas “susceptibles” de lo que pensamos y $R_t$ aumenta.
        <br>
- Proponga una intervención económica y una no económica para reducir el $R_t$.
        <br>
    1. **Intervención económica:**
        Incentivar a la población mediante subsidios o recompensas por vacunación de refuerzo: Se podría implementar un descuento en impuestos, dar un pago directo o incluso organizar una lotería como en el ejemplo de **Vax-A-Million** en Ohio. Esto incrementaría la cobertura efectiva y reduciría la fracción susceptible $S$, disminuyendo así $R_t$. Además, este tipo de incentivos no solo motiva a quienes dudan en vacunarse, sino que también acelera la aplicación de refuerzos, lo que es clave para contrarrestar la propagación de la nueva variante.
        <br>
    2. **Intervención no económica:**
        Imponer el uso obligatorio de mascarillas en espacios públicos cerrados. Esto reduciría la probabilidad de transmisión por contacto ($\beta$), y sería efectivo mientras se trabaja en una vacuna adaptada para la nueva variante. El uso generalizado de mascarillas de buena calidad en ambientes cerrados y con poca ventilación disminuye la cantidad de partículas virales en el aire, interrumpiendo las cadenas de contagio y ayudando a que $R_t$ vuelva a valores manejables.

        <br>
#### Escenario 2
La tasa de vacunación contra el VPH es del **40%** en una región con una asistencia escolar del **80%**.
¿Sería más eficaz un mandato de ingreso a la escuela o clínicas móviles gratuitas? Justifique con:
- Umbral de inmunidad de grupo ($R_0$ del VPH $\thickapprox$ 4)
- Principios de la teoría de juegos

**Umbral de inmunidad de grupo:**
$$
R_0 = 4
$$
$$
\text{Cobertura necesaria} = 1− \frac{1}{R_0}=1−\frac{1}{4}=0.75=75\%
$$

La tasa de vacunación actual contra el VPH **(40%)** está muy por debajo del umbral de inmunidad de grupo, que para un $R_0$ ≈ 4 se estima en un **75%**. En una región donde el **80%** de la población en edad escolar asiste a clases, un mandato de vacunación como requisito para el ingreso escolar tiene el potencial de aumentar de forma significativa la cobertura en poco tiempo, ya que obliga a un alto porcentaje de la población objetivo a vacunarse para poder continuar sus estudios.

| Criterio | Mandato escolar | Clínicas móviles gratuitas |
| -------- | --------------- | -------------------------- |
| Cobertura potencial | Hasta el 80% del grupo | Potencialmente el 100% del grupo |
| Eficiencia logística | Centralizado (escuelas) | Descentralizado, costoso de operar |
| Equidad | Excluye a los niños fuera del sistema escolar | Abarca zonas rurales y poblaciones vulnerables |
| Incentivo estratégico (teoría de juegos) | Aumenta el **costo de no vacunarse** (exclusión escolar) | Reduce el **costo de vacunarse** (acceso gratuito) |


**Teoría de Juegos**
* En modelos de teoría de juegos, los individuos eligen vacunarse si el beneficio percibido supera el costo.

* El mandato escolar introduce una penalización estructural que es no asistir a clases, alterando el equilibrio y empujando hacia la vacunación.

* Las clínicas móviles reducen el costo, pero no alteran tanto el equilibrio si el incentivo aún es bajo, dado que no perciben la vacunación como prioritaria

Por ello, con la alta asistencia escolar de la región **(80%)**, el mandato escolar tiene más probabilidades de acercar rápidamente la cobertura al umbral del **75%** necesario para lograr inmunidad de grupo.

---

## [**Ejercicio 3**](ejercicio3.ipynb)

Simule el impacto de las intervenciones con Python. Para ello, modele una epidemia bajo tres políticas:

1. **Línea base**: Sin intervenciones (modelo SIR)
2. **Lotería**: Tasa de vacunación ↑ en 0,02/día después de 100 casos
3. **Mandato**: Refuerzo inmediato de la vacunación del 50 % cuando $R_t > 1$

Para ello considere:
- Utilizar `scipy.integrate.odeint` para la dinámica del **SIR**
- Parámetros:
    * $\beta = 0.35$
    * $\gamma = 0.1$
    * infectados iniciales = 10
    * población = 10,000

Para sus resultados, deberá presentar
- Gráfico de series temporales de infecciones bajo los tres escenarios
- Análisis y comparación del recuento final de infectados

### **Lógica Básica del Código Implementado**
1. Definición del modelo SIR y su variante con vacunación.
2. Ejecución del escenario base (sin vacunación).
3. Simulación paso a paso de los escenarios con intervención para permitir que las políticas cambien en función del tiempo o la situación epidemiológica.
4. Generación de gráficos para comparar los escenarios.
5. Cálculo de métricas clave:
    - Pico máximo de infecciones.
    - Total de infectados acumulados.
    - Porcentaje de reducción respecto a la línea base.

### **Resultados**
Simulando Escenario A: Línea base (sin intervenciones)
Simulando Escenario B: Lotería
Simulando Escenario C: Mandato

![Comparación de Infecciones bajo 3 políticas de intervención](image.png)

```
============================================================
ANÁLISIS DE RESULTADOS
============================================================

PICO DE INFECCIONES:
Línea base:    3565 personas
Lotería:       1857 personas
Mandato:       13 personas

TOTAL DE PERSONAS QUE SE INFECTARON AL FINAL:
Línea base:    9660 personas (96.6%)
Lotería:       9971 personas (99.7%)
Mandato:       7816 personas (78.2%)

REDUCCIÓN EN EL TOTAL DE INFECTADOS:
Lotería vs Línea base:   -3.2% de reducción
Mandato vs Línea base:   19.1% de reducción

================================================================================
TABLA RESUMEN DE RESULTADOS
================================================================================
 Escenario Pico de Infecciones Total Infectados Porcentaje de Población (%) Reducción vs Línea base (%)
Línea base               3,565            9,660                       96.6%                        0.0%
   Lotería               1,857            9,971                       99.7%                       -3.2%
   Mandato                  13            7,816                       78.2%                      +19.1%

============================================================
MÉTRICAS DE EFECTIVIDAD DE LAS POLÍTICAS
============================================================
Política Reducción del Pico (%) Reducción Total (%)       Evaluación
 Lotería                 +47.9%               -3.2% Contraproducente
 Mandato                 +99.6%              +19.1%     Muy Efectiva
```
### **Análisis** 

En el análisis se puede observar que la política de mandato es la estrategia más eficaz para controlar la epidemia. Ya que reduce el pico de infecciones en un 99.6%, pasando de 3,565 a solo 13 personas, y disminuye la tasa de ataque final de 96.6% a 78.2%, lo que representa 1,844 infecciones evitadas (una reducción total del 19.1%). Esta alta efectividad se debe a la activación inmediata de medidas cuando el número reproductivo efectivo (Rt) supera 1, permitiendo contener la transmisión en etapas tempranas, cuando Rt alcanza valores de hasta 3.50. El escenario sin intervención muestra un pico epidémico del 35.6% de la población (3,565 personas) y un total de 9,660 infectados de los 10,000 habitantes (96.6%).

Por otro lado, la política de lotería aunque reduce el pico de contagios en un 47.9% (de 3,565 a 1,857 personas),  incrementa el total final de infectados en un 3.2%, alcanzando 9,971 casos (99.7% de la población). Este resultado negativo se atribuye a que la intervención se activa tardíamente, una vez que ya hay 100 casos confirmados, lo cual equivale a que el 1.0% de la población ha sido afectada. Esta demora de aproximadamente 9 días frente a la política de mandato permite que la epidemia se establezca, prolongando su duración y aumentando la transmisión. La diferencia de 2,155 infecciones entre ambas estrategias no solo es epidemiológicamente relevante, sino que también implica un impacto considerable en términos de morbilidad, mortalidad y carga hospitalaria.

## **Referencias**

1. Clinical Infectious Diseases, Volume 52, Issue 7, 1 April 2011, Pages 911–916, https://doi.org/10.1093/cid/cir007

2. Reluga, T. C. (2010). Game theory of social distancing in response to an epidemic. PLoS Computational Biology, 6(5), e1000793. https://doi.org/10.1371/journal.pcbi.1000793

