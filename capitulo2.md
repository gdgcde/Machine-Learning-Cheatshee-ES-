<h2 style="color:#00686E"> Conjunto de datos de entrenamiento no representativos </h2>
Cuando los datos disponibles durante el entrenamiento no son suficientes para capturar la
modelo, en relación con el conjunto de datos de validación.

<center>

&#013;

![GrafoPerdida](https://imgur.com/T4tpiWe.png)

</center>

Las curvas de tren y validación están mejorando, pero hay una gran brecha entre ellos, lo que significa que operan como conjuntos de datos de diferentes distribuciones.

<h2 style="color:#00686E"> Conjunto de datos de validación no representativos </h2>

<center>

&#013;

![GrafoPerdida](https://imgur.com/b7Wa8iG.png)

</center>

Como podemos ver, la curva de entrenamiento parece estar bien, pero la función de validación se mueve ruidosamente alrededor de la curva de entrenamiento. Podría darse el caso de que Los datos de validación son escasos y poco representativos de la formación datos, por lo que el modelo tiene dificultades para modelar estos ejemplos.

<center>

&#013;

![GrafoPerdida](https://imgur.com/qKe38s7.png)

</center>

Aquí, la pérdida de validación es mucho mejor que la de entrenamiento, que refleja el conjunto de datos de validación y es más fácil de predecir que el de entrenamiento conjunto de datos. Una explicación podría ser que los datos de validación son escasos pero ampliamente representado por el conjunto de datos de entrenamiento, por lo que el modelo realiza muy bien en estos pocos ejemplos.

<h2 style="color:#00686E"> Evaluación del modelo </h2>

<h2 style="color:#00686E"> Problemas de clasificación </h2>

<p style="color:#BF0040; font-weight:bold ">Matriz de confusión</p>

- Los datos nos dan **resultados** ("verdad") $(y | Y)$.
- El modelo toma **decisiones** $(d | D)$ (Guardando yˆ Puntuaciones).

Luego comparamos las decisiones (d) a los resultados (y).

**Error tipo I:** La hipótesis nula $H_0$ se **rechaza** cuando es **verdad.**

**Error tipo II:** la hipótesis nula $H_0$ no es **rechazado** cuando es
**falso.**

&#8594; **Falso negativo** ( **Error tipo I:** ) &#8213; decidir incorrectamente **no**.

&#8594; **Falso positivo** ( **Error tipo II:** ) &#8213; decidir incorrectamente **si**.

<center>

&#013;

![GrafoPerdida](https://imgur.com/KmFo90v.png)

</center>

**Ej:** asumimos la hipótesis nula $H_0$ es verdadero.

&#8594; $H_0$ : La persona no es culpable.

&#8594; $H_1$ : La persona es culpable.

<center>

&#013;

![GrafoPerdida](https://imgur.com/6g4oZrT.png)

</center>

$(1)$ **Exactitud** : $\frac {TP + TN} {TP + TN + FP + FN}$ &#8594; Relacion de **predicciones correctas** sobre **predicciones totales.**

**Estimado** de $P[D = Y]$, La probabilidad de decisión es igual al resultado.

$(2)$ **Recuerdo** o **Sensibilidad** o **Tasa de verdaderos positivos:** $\frac{TP}{TP + FN}$

Completitud del modelo. &#8594; Del **total de valores positivos reales (1)**, Con qué frecuencia el clasificador es correcto. **Probabilidad**: $P[D=1|Y=1]$.

<span style="color: #0000FF; font-weight:bold">Ejemplo:</span> **"Detección de transacciones fraudulentas"** o **Cancer de persona** &#8594; $+$ ve $(1)$ es "fraude": optimizar para sensibilidad porque falso positivo (**FP** transacciones normales que están marcadas como posible fraude) son más aceptables que los falsos negativos (**FN** transacciones fraudulentas que no son detectado)

$(3)$ **Precision :** $\frac{TP}{TP + FN}$ Exactitud del modelo. &#8594; Del **total de valores positivos previstos (1)**, con qué frecuencia el clasificador es correcto. **Probabilidad**: $P[D=1|Y=1]$. Si nuestro modelo dice positivo, ¿qué probabilidades hay de que sea correcto en ese juicio?

<span style="color: #0000FF; font-weight:bold">Ejemplo:</span> "Filtro de spam" $+$ ve $(1)$ la clase es spam &#8594; Optimice la precisión o la especificidad debido a los falsos negativos. (**FN** el spam va a la bandeja de entrada) son más aceptables que los falsos positivos (**FP** el filtro de spam detecta lo que no es spam). <span style="color: #0000FF; font-weight:bold">Ejemplo:</span> **"Reserva de hotel cancelada"** $+$ ve $(1)$ la clase está cancelada &#8594; Optimice la precisión o la especificidad porque los falsos negativos (**FN** cancelado etiquetado como "no cancelado" 0) son más aceptables que los falsos positivos (**FP** cancelado no etiquetado como "cancelado" 1).

$(4)$ **Puntuación F1** $= 2 *\frac{Precision * Recorda}{Precision + Recorda}$ &#8594; Los falsos positivos (FP) y los falsos negativos (FN) son igualmente importantes.

$(5)$ **Tasa de falsos positivos:** $\frac{FP}{TN + FP}$ &#8213; Fracción de **negativos** equivocadamente clasificado positivo. **Probabilidad**: $P[D=1|Y=0]$.

$(6)$ **Tasa de falsos negativos:** $\frac{FN}{TN + FN} =$ 1-Recordar &#8213; Fracción de **positivos** equivocadamente clasificado negativos. **Probabilidad**: $P[D=0|Y=1]$.

$(7)$ **Especificidad**: $\frac{TN}{TN + FP} =$ 1-FPR &#8213; Fracción de **negativos** correctamente clasificados como negativos. **Probabilidad**: $P[D=0|Y=0]$.

$(8)$ **"Detección de transacciones fraudulentas"**, FPR $=$ $\frac{FP}{FP+TN}$ &#8594; probabilidad de rechazar falsamente la "hipótesis nula" $H_0$

$(9)$ **Curva ROC:** **¿Qué FPR debes tolerar para un determinado TPR?** Una curva ROC traza TPR frente a FPR en diferentes umbrales de clasificación &#10716;.

&#8594; Reducir el umbral de clasificación clasifica más elementos como
positivo, aumentando así tanto los falsos positivos como los verdaderos positivos.

<center>

&#013;

![GrafoPerdida](https://imgur.com/vJ2we7o.png)

</center>

**Nota:** Podemos pensar en la gráfica como la fracción de predicciones correctas para la clase positiva (eje - y) versus la fracción de errores para la clase negativa (eje - x).

$(10)$ AUC: Área bajo la curva ROC: Para calcular los puntos en una curva ROC, un algoritmo eficiente basado en clasificación llamado AUC. AUC su valor varía de 0 a 1. El área bajo la curva mide cuánto es probable que el modelo diferencie lo positivo y lo negativo (AUC perfecta $=$ 1, línea de base $=$ 0.5).

<center>

&#013;

![GrafoPerdida](https://imgur.com/1KSRicx.png)

</center>
