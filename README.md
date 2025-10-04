# 🔧 PREDICCIÓN DE FALLAS EN HERRAMIENTAS ROTATIVAS INDUSTRIALES

## 📝 DESCRIPCIÓN DEL PROYECTO  
Análisis técnico para anticipar fallas en herramientas rotativas industriales. Se aplican criterios de desgaste y modelos de clasificación para priorizar revisiones, optimizar mantenimiento predictivo y reducir paros no planeados.

## 🛠️ TECNOLOGÍAS UTILIZADAS  
- 🐍 **Python**: análisis y modelado  
- 🧹 **Pandas**: limpieza y estructuración  
- 📊 **Scikit-learn**: clasificación y cálculo de probabilidades  
- 📈 **Matplotlib**: visualización funcional

## 🌳 MODELO 1: ÁRBOL DE DECISIÓN  
- Variables: `torque [nm]`, `tool wear [min]`  
- Separación perfecta entre falla y no falla  
- Gini = 0.0 en ambas ramas  
- Precisión: 100%  
- Aplicación: útil por su lógica directa y explicable

## 🌲 MODELO 2: RANDOM FOREST  
- Mejora la detección de fallas reales y reduce falsas alertas  
- 🔍 Métricas:  
  - 🎯 Recall: 41%  
  - ✅ Precisión: 76%  
- Filtro aplicado: probabilidad de falla ≥ 0.85  
- Se identificaron 13 registros marcados como “Revisar”

## 🚨 FILTRO DE RIESGO EXTREMO  
```python
riesgo['accion'] = riesgo['prob_falla'].apply(lambda x: 'Revisar' if x > 0.85 else '')
revisiones = riesgo[riesgo['accion'] == 'Revisar']

🔎 El filtro por probabilidad ≥ 0.85 permite enfocar únicamente en los equipos con riesgo crítico.  
Esto mejora la eficiencia operativa, evita revisiones innecesarias y convierte la salida del modelo en una herramienta práctica para mantenimiento.