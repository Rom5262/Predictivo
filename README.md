
# 🔧 PREDICCIÓN DE FALLAS EN FRESADO INDUSTRIAL 🔧

## 📝 DESCRIPCIÓN DEL PROYECTO
Análisis técnico para anticipar fallas en herramientas de corte accionadas por husillo en fresadoras industriales.  
Se aplican criterios de desgaste y modelos de clasificación para:  
- Priorizar revisiones  
- Optimizar mantenimiento predictivo  
- Reducir paros no planeados

## 🛠️ TECNOLOGÍAS UTILIZADAS
- 🐍 Python: análisis y modelado  
- 🧹 Pandas: limpieza y estructuración de datos  
- 📊 Scikit-learn: clasificación y cálculo de probabilidades  
- 📈 Matplotlib: visualización de resultados

## 🌳 MODELO 1: ÁRBOL DE DECISIÓN
- Variables: torque [nm], tool wear [min]  
- Separación perfecta entre falla y no falla  
- Gini = 0.0 en ambas ramas  
- Precisión: 100%  
- Aplicación: útil por su lógica directa y explicable

## 🌲 MODELO 2: RANDOM FOREST
- Mejora la detección de fallas reales y reduce falsas alertas  
- Métricas:  
  - Recall: 41%  
  - Precisión: 76%  
- Filtro aplicado: probabilidad de falla ≥ 0.85  
- Se identificaron 13 registros marcados como “Revisar”

## 🚨 FILTRO DE RIESGO EXTREMO
Aplicación del filtro de riesgo:  
riesgo['accion'] = riesgo['prob_falla'].apply(lambda x: 'Revisar' if x > 0.85 else '')  
revisiones = riesgo[riesgo['accion'] == 'Revisar']  
print(f"Equipos en riesgo crítico: {len(revisiones)}")

Comentario práctico:  
El filtro por probabilidad ≥ 0.85 permite enfocar únicamente en los equipos con riesgo crítico.  
Esto mejora la eficiencia operativa, evita revisiones innecesarias y convierte la salida del modelo en práctica para mantenimiento.

# 📈 CIERRE OPERATIVO
Ambos modelos permiten anticipar fallas con criterios técnicos claros.  
🌿 El árbol ofrece una regla directa por desgaste.  
🌲 Random Forest permite priorizar por nivel de riesgo.  
🔧 La aplicación en planta es inmediata: se priorizan revisiones, se reduce el gasto operativo y     se respalda la toma de decisiones.
