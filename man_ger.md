<div align="center">

# Informe Gerencial: Estrategia de Gobierno y Despliegue de Plataformas SIG (OSGeo4W)

</div>

---

## 1. Resumen Ejecutivo
El presente documento define la estrategia institucional para la instalación, actualización y mitigación de riesgos asociados con la plataforma geoespacial **QGIS**, desplegada a través del entorno corporativo **OSGeo4W**. El objetivo es equilibrar la innovación y las capacidades analíticas de la organización con la continuidad de los procesos de negocio y las políticas de ciberseguridad corporativa.

---

## 2. Perspectiva de Continuidad de Negocio: Selección de Versiones

Para asegurar que los flujos de trabajo de producción (ingeniería, medio ambiente, planeamiento y analítica de datos) no sufran interrupciones críticas, se establece la siguiente directiva de despliegue de software:

* **Estándar Corporativo Obligatorio (Línea Base): QGIS LTR (`qgis-ltr`)**
    Las versiones LTR (Soporte a Largo Plazo) son el pilar de nuestra infraestructura de escritorio. Garantizan que las herramientas y modelos de automatización implementados en la empresa funcionen sin alteraciones durante ciclos anuales completos. Esto minimiza drásticamente los costos de soporte técnico interno (*Helpdesk*) y elimina tiempos muertos por incompatibilidades imprevistas.
* **Exclusión de Versiones de Desarrollo (`qgis-dev` / `qgis-ltr-dev`):**
    Queda estrictamente prohibida la instalación de versiones marcadas con el sufijo `-dev` en equipos de producción. Estas versiones representan software en etapa beta o experimental. Su uso eleva el riesgo operativo debido a fallos críticos que pueden corromper bases de datos geoespaciales o generar inconsistencias en los entregables técnicos de los proyectos.

---

## 3. Gobierno de TI y Gestión de Riesgos de Ciberseguridad

El entorno OSGeo4W es seguro en sus componentes base, pero introduce vectores de riesgo que la Gerencia de Tecnología e Innovación debe gobernar bajo un enfoque de **Confianza Cero (Zero Trust)**:

1.  **Políticas de Plugins de Terceros (Ecosistema Python):**
    El principal riesgo no reside en el instalador, sino en la capacidad de los usuarios para descargar complementos externos. Algunos complementos mal diseñados o de fuentes no verificadas pueden abrir brechas de seguridad que expongan información confidencial a servidores externos.
    * *Acción Gerencial:* Implementar un catálogo interno de "Plugins Autorizados" por el área de Seguridad de la Información antes de su despliegue general.
2.  **Mitigación de Vulnerabilidades en Componentes Heredados:**
    Herramientas específicas como los conectores para bases de datos propietarias (`oracle-provider`) añaden componentes de terceros (archivos `.dll`) que incrementan la superficie de exposición del sistema operativo Windows ante posibles ciberataques.
    * *Acción Gerencial:* Excluir conectores que no correspondan a la arquitectura actual de la empresa (ej. si la organización no usa Oracle, este paquete debe desmarcarse por defecto).

---

## 4. Cuadro de Mando: Plan de Adopción y Mitigación

| Componente | Nivel de Riesgo Operativo | Recomendación de Adopción Corporativa | Impacto Financiero / Productivo |
| :--- | :--- | :--- | :--- |
| **QGIS LTR (`qgis-ltr`)** | **Bajo** | Adoptar como software estándar corporativo para todos los analistas SIG. | **Positivo:** Alta estabilidad, costo cero de licenciamiento, capacitación uniforme. |
| **QGIS Estándar (`qgis`)** | **Medio** | Permitido únicamente para laboratorios de innovación o validación de nuevas herramientas. | **Neutro:** Acceso temprano a funciones analíticas con riesgo menor de desajuste. |
| **Familias `-dev` (Desarrollo)** | **Alto** | **Prohibido.** Bloquear su instalación mediante políticas de restricción de Windows. | **Negativo:** Pérdida de horas hombre por fallos imprevistos y fugas potenciales de seguridad. |
| **QGIS Server** | **Medio** | Restringido exclusivamente al entorno de servidores centralizados del área de TI. | **Positivo:** Permite centralizar mapas web reduciendo costos de servidores de mapas comerciales. |
