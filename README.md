# -An-lisis-ConnectaTel

# 📊 Análisis ConnectaTel — Sprint 7

Análisis estadístico del comportamiento de clientes de **ConnectaTel**, una empresa de telecomunicaciones en Latinoamérica, con datos registrados hasta el año 2024.

---

## 🎯 Objetivo del Proyecto

Evaluar el comportamiento de los clientes de ConnectaTel para:
- Identificar **patrones de consumo** en llamadas y mensajes
- Detectar **comportamientos atípicos** (outliers)
- Crear **segmentos de clientes** por edad y nivel de uso
- Proponer **estrategias de retención** y mejoras en los planes

## 🔍 Etapas del Análisis

### Paso 1 — Carga y Exploración
- Importación de librerías: `pandas`, `numpy`, `matplotlib`, `seaborn`
- Carga de los 3 datasets
- Inspección inicial con `.head()`, `.info()`, `.shape`

### Paso 2 — Identificación de Problemas de Calidad
- **Valores nulos**: `city` (11.7%), `churn_date` (88.4%), `duration` y `length` (MAR)
- **Sentinels detectados**: valor `-999` en `age`, `"?"` en `city`
- **Fechas fuera de rango**: 40 registros con año 2026 en ambas tablas

### Paso 3 — Limpieza Básica
- Reemplazo de `-999` en `age` por la **mediana**
- Reemplazo de `"?"` en `city` por `pd.NA`
- Marcado de fechas futuras (> 2024) como `pd.NaT`
- Verificación de nulos MAR en `duration` y `length` (correctos por diseño)

### Paso 4 — Perfil de Usuario y Estadísticas
- Agregación de `usage` por usuario: total de mensajes, llamadas y minutos
- Merge con `users` para crear tabla `user_profile`
- Resumen estadístico descriptivo y distribución de planes

### Paso 5 — Visualización y Detección de Outliers
- Histogramas por plan (Básico vs Premium) para: edad, mensajes, llamadas y minutos
- Boxplots para identificar outliers por variable y plan
- Detección cuantitativa con método IQR

### Paso 6 — Segmentación de Clientes
- **Por nivel de uso**: Bajo / Medio / Alto (usando percentiles 33 y 66)
- **Por edad**: Joven (< 30) / Adulto (30–59) / Adulto Mayor (≥ 60)

---

## 📈 Principales Hallazgos

### ⚠️ Problemas en los datos
- Valores sentinel `-999` en `age` → imputados con la mediana
- **11.7%** de usuarios sin ciudad registrada
- **40 registros** con fechas futuras (año 2026) → marcados como nulos
- Nulos en `duration` y `length` son MAR (correctos por diseño del sistema)

### 🔍 Segmentación por Edad
- **Adultos (30–59 años)**: segmento mayoritario → principal base de clientes de ConnectaTel
- **Jóvenes (< 30)** y **Adultos Mayores (≥ 60)**: segmentos menores con potencial de crecimiento

### 📊 Segmentación por Nivel de Uso
- **Uso Bajo y Medio**: concentra la mayor parte de usuarios (consumo moderado)
- **Uso Alto**: grupo reducido con altos niveles de mensajes, llamadas y minutos → alto valor potencial para la empresa

### 💡 Conclusión
ConnectaTel tiene una base sólida de usuarios de consumo moderado y un nicho estratégico de usuarios intensivos que representan una oportunidad de mayor ingreso con planes diferenciados.

---

## 💼 Recomendaciones Estratégicas

1. **Diseñar un plan específico** para usuarios de alto uso (mensajes y minutos ilimitados)
2. **Enfocar campañas de marketing** en el segmento Adulto (30–59 años), grupo predominante
3. **Implementar estrategias de fidelización** para usuarios intensivos por su alto valor potencial
4. **Mejorar la captura de datos** para reducir el porcentaje de ciudades faltantes (actualmente 11.7%)
