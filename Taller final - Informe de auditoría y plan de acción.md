# Taller final: informe de auditoría y plan de acción

**Asignatura:** ET0114 · Auditoría de Sistemas  
**Docente:** Juan Duque  
**Integrante:** Samuel Muriel Meneses  
**Organización / caso:** Bancolombia S.A. – Servicio digital *Mi Bancolombia* y componentes de soporte  
**Fecha de emisión:** 17 de noviembre de 2026  
**Repositorio:** [Auditoria-de-Sistemas-Samuel-Muriel-Meneses](https://github.com/SamuelMurielM/Auditoria-de-Sistemas-Samuel-Muriel-Meneses)  
**Naturaleza del documento:** Informe académico con **prueba, datos y criterio operativo simulados**. No contiene evidencia real de Bancolombia S.A. ni emite opinión real sobre sus controles o cumplimiento.

---

## 1. Identificación y continuidad del caso

Este informe final, elaborado por **Samuel Muriel Meneses** el **17 de noviembre de 2026**, consolida la auditoría académica sobre **Bancolombia S.A.** (*Mi Bancolombia* y procesos de soporte), dando continuidad directa a los tres entregables del semestre:

1. **Marcos ([Taller 1](https://github.com/SamuelMurielM/Auditoria-de-Sistemas-Samuel-Muriel-Meneses/blob/main/Taller%20Auditoria%20Bancolombia.md)):** secuencia **COBIT 2019 → ISO/IEC 27001:2022 → ITIL 4** sobre canales digitales, contextualizada con cifras públicas de **2025** (*Informe de Gestión 2025*: 9,4 millones de clientes digitales activos/mes, 98 % de transacciones monetarias digitales y 83 % de pérdidas operacionales del ecosistema asociadas a fraude externo; contexto general, no específico de cuentas administrativas de *Mi Bancolombia*).
2. **Matriz inicial ([Sesión 7](https://github.com/SamuelMurielM/Auditoria-de-Sistemas-Samuel-Muriel-Meneses/blob/main/Matriz%20de%20riesgos%20Bancolombia%20-%20Actualizada.md)):** cinco riesgos académicos sobre *Mi Bancolombia* (`R-01` a `R-05`) tratados como supuestos por validar y `Control actual: No determinado`.
3. **Plan ([Entregable 2](https://github.com/SamuelMurielM/Auditoria-de-Sistemas-Samuel-Muriel-Meneses/blob/main/Entregable%202%20-%20Auditor%C3%ADa%20de%20Sistemas.md)):** priorización de **`R-02` (Uso de cuentas administrativas después del retiro)** sobre **`A-02`** (`P=3 × I=5 = 15`, Alto), criterios `C-01`–`C-05` y procedimientos `P-01`–`P-05` para **`2026-04-01` a `2026-09-30`**.
4. **Informe actual:** documenta la prueba simulada **`PT-01`**, sus hallazgos y el plan de acción propuesto.

---

## 2. Resumen ejecutivo

Se ejecutó una prueba académica **simulada** (`PT-01`) sobre el control preventivo por evento del Entregable 2 —codificado aquí como **`CTRL-01`**— para el riesgo **`R-02`**, usando datos ficticios coherentes entre el **`2026-04-01 00:00`** y el corte único **`2026-09-30 23:59` (`COT, UTC-5`)**. Ante la ausencia de política interna real (`C-01`), se empleó el parámetro operativo simulado **`C-01-SIM`**: máximo **4 horas continuas en reloj 24/7** desde la hora efectiva del retiro hasta el cierre completo del control.

Sobre **`N = 24`** retiros efectivos simulados (`16` empleados, `8` contratistas), la conciliación (`P-02`) emparejó los `24` titulares con IAM/PAM y detectó `3` alertas (`E-009`, `E-015`, `E-019`). En la muestra estratificada de **`n = 8`** casos (`3` alertas + `5` estratificados sin alerta; `5` empleados, `3` contratistas), **`5` casos cumplieron el ciclo completo** (`0 h 42 min` a `2 h 35 min` hasta revocación de sesión; bajas IAM entre `0 h 40 min` y `2 h 30 min`, más reasignación y rotación en `2 h 15 min` para `E-012`) y **`3` presentaron excepciones**, originando **dos hallazgos simulados**:

- **`H-01` (Prioridad Alta):** demora de **`65 h 15 min`** en baja IAM y falta de revocación explícita en **`E-009`** (retiro de viernes atendido el lunes), más cuenta **`adm_sop_019` (`E-019`)** activa sin ticket durante **`41 días y 11 h 59 min` (`995 h 59 min`)** hasta el corte **`2026-09-30 23:59`**.
- **`H-02` (Prioridad Media-Alta):** baja nominal oportuna en **`E-015` (`1 h 50 min`)**, pero omisión de reasignación de custodio y rotación de secreto en la cuenta compartida **`svc_pagos_ops`** durante **`84 días y 5 h 59 min` (`2021 h 59 min`)** al corte.

**Alcance probatorio:** la prueba ilustra la mecánica verificable de `CTRL-01` sobre datos ficticios; no demuestra cumplimiento ni incumplimiento real de Bancolombia S.A. ni sustituye `P-01`, validación con custodios ni `P-04`.

---

## 3. Objetivo, alcance y ajuste metodológico

### 3.1 Objetivo, responsable y continuidad de `CTRL-01`

Evaluar mediante simulación trazable si **`CTRL-01`** bloqueó oportunamente cuentas nominales, sesiones activas y custodias no personales tras el retiro dentro de **`R-02` (`A-02`)**.

- **Responsable del control bajo prueba (simulado):** **Coordinación / Líder de Control de Accesos (IAM/PAM)** como dueño operativo del control en articulación con **Gestión Humana / Contratación** para el aviso oportuno de retiro *(rol atribuido al modelo simulado; el dueño real en Bancolombia se confirmaría mediante `P-01`)*.

> **Continuidad con Entregable 2:** El identificador `CTRL-01` no existía en el Entregable 2 (Secciones 3 y 6), donde se definieron tres controles objetivo: (1) notificación de retiro, (2) desactivación IAM y revocación de sesión, y (3) conciliación periódica. **`CTRL-01`** consolida aquí los **dos controles preventivos por evento (1 y 2)** más el seguimiento a cuentas compartidas o de emergencia previsto en la Sección 4 y paso 4 de `P-03` (notificación, baja IAM, revocación de sesión y reasignación/rotación PAM). El tercer control (conciliación periódica) quedó excluido al omitirse `P-04`.

### 3.2 Alcance de la prueba simulada

- **Ventana y corte único:** retiros efectivos entre **`2026-04-01 00:00`** y **`2026-09-30 23:59` (`COT, UTC-5`)**, evaluados al snapshot **`2026-09-30 23:59`**.
- **Población (`N = 24`):** empleados y contratistas retirados con cuentas privilegiadas nominales o custodia PAM en módulos simulados de soporte a *Mi Bancolombia*.
- **Exclusiones heredadas:** usuarios finales, nómina financiera, proveedores sin privilegios y riesgos `R-01`, `R-03`, `R-04` y `R-05`.

### 3.3 Ajuste respecto al Entregable 2 y deslinde Real / Simulado

Sin acceso real a Bancolombia ni papel de trabajo previo de clase, los cinco procedimientos (`P-01`–`P-05`) del Entregable 2 se ajustaron así:
1. **`P-01` (No ejecutado):** sin acceso interno no se validaron diseño documental real, componentes dependientes ni SLA real.
2. **`P-02` y `P-03` (Priorizados en simulación):** se eligió probar el control preventivo **`CTRL-01`** sobre el control detectivo de conciliación periódica (`P-04`) porque actúa como barrera primaria ante retiros y exige correlacionar toda la cadena horaria (`GH → Ticket → IAM → Sesión → PAM`).
3. **`P-05` (Parcial):** incluyó clasificación de evidencia, `PT-01` y hallazgos preliminares simulados; quedó **pendiente** validar hechos y causas raíz con custodios.
4. **Modelo simulado:** términos como `FUENTE-IAM-SIM`, `FUENTE-PAM-SIM`, `bóveda PAM`, `adm_*`, `pam_emerg_02` y `svc_pagos_ops` son ficticios y no presumen sistemas ni arquitectura real de Bancolombia S.A.

---

## 4. Criterios y metodología

### 4.1 Criterios de auditoría

| ID | Criterio / Fuente | Rol en la prueba y estado real |
|---|---|---|
| **`C-01`** (Real) | Política de identidades, bajas por retiro y SLA oficial de Bancolombia S.A. | **Por solicitar / No suministrado en el ejercicio** (trazabilidad con Entregable 2). |
| **`C-01-SIM`** (Ficticio) | Regla simulada `POL-IAM-RET-SIM v1.0`: cierre íntegro de `CTRL-01` en **≤ 4 h continuas en reloj 24/7 (`UTC-5`, incluye fines de semana y festivos)** desde el retiro efectivo en `GH`. | **Criterio operativo aplicado en `PT-01` (simulado).** |
| **`C-02`** | COBIT 2019 (práctica de gestión de identidad y acceso lógico, *DSS05.04*). | Marco de control y rendición de cuentas. |
| **`C-03`** | ISO/IEC 27001:2022 (cláusulas aplicables y Anexo A: `A.5.15`, `A.5.16` y `A.5.18`). | Referencia técnica; exige revisar edición licenciada y *SoA* vigente en auditoría real. |
| **`C-04` / `C-05`** | *Ley 1581 de 2012* y *CBJ SFC Parte I*. | Marco regulatorio sujeto a validación vigente con Legal/Cumplimiento en auditoría real. |

*Nota de alcance normativo:* **ITIL 4** se mantiene como contexto operativo (gestión de tickets/servicios, no como criterio independiente de conformidad) y la **Ley 1273 de 2009** queda excluida como criterio para evaluar tiempos de baja.

### 4.2 Fuentes simuladas, muestra y procedimientos

El diccionario de campos y reglas de emparejamiento constan en el **Anexo A (`PT-01`)**. Se inspeccionaron tres fuentes simuladas al corte **`2026-09-30 23:59 COT`**: **`FUENTE-GH-SIM`** (`24` retiros), **`FUENTE-IAM-SIM`** (`68` cuentas en alcance, tickets ITSM, marcas de baja/sesión y logs post-retiro) y **`FUENTE-PAM-SIM`** (`6` cuentas no personales en bóveda simulada).

Mediante conciliación automatizada (`P-02`, `24 = 24`) e inspección de trazabilidad (`P-03`), se seleccionó una **muestra dirigida estratificada de `n = 8`** (criterios por estrato en A.2): **Estrato A (censo 100 % alertas `P-02`, `3`):** `E-009`, `E-015`, `E-019`; **Estrato B (censo 100 % otra custodia PAM, `1`):** `E-012`; **Estratos C y D (casos sin alerta, `4` sobre `20`):** `E-003` (emp. Q2 soporte), `E-006` (cont. Q2 vespertino `17:00`, par de `E-009`), `E-017` (emp. Q3 pagos) y `E-022` (cont. Q3 terminación urgente cercana al corte).

**Pasos y condición de excepción (detalle en Anexo A):** (1) conciliar totales y emparejar `24 = 24` por `id_pseudonimo` (`P-02`); (2) extraer la muestra estratificada (`n = 8`); (3) comparar marcas horarias `Retiro GH → Ticket → Baja IAM → Revocación sesión → Custodia PAM` y autorización del ejecutor (`P-03`); y (4) verificar `ts_ultimo_log_auth` hasta el corte `2026-09-30 23:59`. Se clasifica como **excepción** todo caso con demora `> 4 h continuas 24/7` en baja, revocación o reasignación/rotación PAM, ausencia de evento de revocación por retiro o permanencia activa/sin rotación al corte.

---

## 5. Resultados y hallazgos simulados

### 5.1 Síntesis de ejecución (`PT-01`, `n = 8`)

*(El detalle completo de tickets, ejecutores autorizados, logs y marcas horarias obra en el Anexo A, tabla A.3).*

| Caso (Vínc.) | Cuenta(s) sim. | Retiro efectivo (`GH`) | Baja IAM (`Δ`) | Revoc. sesión (`Δ`) | Custodia PAM (`Δ` / Corte) | Estado (`C-01-SIM` 4h) |
|---|---|---|---|---|---|---|
| `E-003` (Emp.) | `adm_core_003` | `2026-04-14 16:00` | `1 h 05 min` | `1 h 08 min` | N/A | **Cumple** |
| `E-006` (Cont.) | `adm_red_006` | `2026-05-05 17:00` | `2 h 30 min` | `2 h 35 min` | N/A | **Cumple** |
| `E-009` (Emp.) | `adm_app_009` | `2026-06-12 17:00` | **`65 h 15 min`** | Sin evento (timeout 2h desde `16:55` → `18:55`) | N/A | **Excepción (`H-01`)** |
| `E-012` (Emp.) | `adm_bd_012` + `pam_emerg_02` | `2026-06-24 11:00` | `1 h 20 min` | `1 h 22 min` | Reasig. `13:10` + rot. `2 h 15 min` | **Cumple** |
| `E-015` (Emp.) | `adm_pag_015` + `svc_pagos_ops` | `2026-07-08 18:00` | `1 h 45 min` | `1 h 50 min` | **Sin reasig./rotar (`84 d 5 h 59 m`)** | **Excepción (`H-02`)** |
| `E-017` (Emp.) | `adm_pag_017` | `2026-07-29 09:00` | `2 h 00 min` | `2 h 10 min` | N/A | **Cumple** |
| `E-019` (Cont.) | `adm_sop_019` | `2026-08-20 12:00` | **Activa al corte** (`41 d 11 h 59 m`) | **Sin revocación** | N/A | **Excepción (`H-01`)** |
| `E-022` (Cont.) | `adm_api_022` | `2026-09-14 14:00` | `0 h 40 min` | `0 h 42 min` | N/A | **Cumple** |

**No extrapolación:** los conteos **`5 de 8`** y **`3 de 8`** aplican únicamente a esta muestra dirigida y ficticia; no representan tasa de fallo (37,5 %) del universo simulado (`N = 24`) ni de Bancolombia S.A. Los logs simulados no mostraron inicios exitosos atribuibles a los `8` IDs tras su retiro.

### 5.2 Hallazgos simulados

#### `H-01` (Prioridad Alta): Demora severa y omisión de desactivación privilegiada tras el retiro (`CTRL-01`)
- **Criterio (`C-01-SIM` / `C-02` / `C-03` — Anexo A `A.5.15`, `A.5.16` y `A.5.18`):** Todo retiro efectivo exige notificación, baja de cuenta y revocación de sesión dentro de **4 h continuas en reloj 24/7**.
- **Condición observada (simulada):** **`2 de 8`** casos incumplieron: **`E-009`** (retiro **viernes `2026-06-12 17:00`**) recibió ticket `INC-SIM-4510` el **lunes `2026-06-15 08:30`** (`63 h 30 min` después) y baja IAM a las **`10:15`** (`1 h 45 min` tras ticket; **`65 h 15 min`** totales), sin evento explícito de revocación por baja (expiró por *timeout* simulado de inactividad de 2 h desde su última actividad registrada a las `16:55` → `18:55` del `06-12`); y **`E-019`** (`adm_sop_019`, retiro **`2026-08-20 12:00`**) careció de ticket y seguía **`Activa`** al corte **`2026-09-30 23:59`** (**`41 días y 11 h 59 min` = `995 h 59 min`**).
- **Causa:** **Pendiente de confirmar** al omitirse `P-01` y validación de `P-05`. Hipótesis por verificar: falta de integración automática 24/7 GH/Contratación→ITSM/IAM y brechas en avisos de contratistas o turnos no hábiles.
- **Efecto:** *Observado (simulado):* acceso potencial vigente `65 h 15 min` (`E-009`) y `41 d 11 h 59 m` (`E-019`), sin autenticaciones posteriores registradas. *Riesgo potencial:* alteración o exfiltración en soporte a *Mi Bancolombia*.
- **Recomendación:** Ejecutar contención inmediata sobre cuentas remanentes (`adm_sop_019`), diagnosticar causas en flujos GH/Contratación/IAM (incluyendo 24/7), implementar integración automática con revocación forzada conforme al SLA aprobado y validar cobertura con la conciliación periódica aplicable (`P-04`).

#### `H-02` (Prioridad Media-Alta): Omisión de reasignación de custodio y rotación de secreto en cuenta compartida (`svc_pagos_ops`)
- **Criterio (`C-01-SIM` / `C-02` / `C-03` — Anexo A `A.5.16` y `A.5.18`):** El retiro de un custodio exige reasignar custodia y rotar el secreto no personal en **≤ 4 h continuas**.
- **Condición observada (simulada):** En **`E-015`** (retiro **`2026-07-08 18:00`**), la cuenta nominal `adm_pag_015` cerró en `1 h 50 min`, pero su titular seguía como custodio en `svc_pagos_ops` al corte **`2026-09-30 23:59`** (**`84 días y 5 h 59 min` = `2021 h 59 min`**) sin rotación (contraste con `E-012`, cerrado en `2 h 15 min`).
- **Causa:** **Pendiente de confirmar** (sin `P-01` ni entrevistas). Posibles hipótesis: inventario desactualizado o ausencia de disparador PAM automático al retiro del custodio.
- **Efecto:** *Observado (simulado):* secreto potencialmente conocido por excolaborador durante `84 d 5 h 59 m`, con `0` accesos atribuidos a `E-015` (sin individualización plena por cuenta compartida). *Riesgo potencial:* uso encubierto transversal y **pérdida de trazabilidad individual y no repudio** (`DSS05.04`).
- **Recomendación:** Mantener inventario de custodios principal/alterno; **previa evaluación de dependencias operativas en aplicaciones** para evitar indisponibilidad, automatizar reasignación/rotación por retiro y migrar hacia cuentas nominales o bóveda con rotación automatizada.

---

## 6. Conclusión y limitaciones

- **Respaldo de evidencia simulada:** `PT-01` evidencia cómo operar y auditar `CTRL-01`: cuando existió aviso oportuno (`6` bajas nominales —incluidas `E-012` y `E-015`— más la custodia PAM de `E-012`), las bajas IAM oscilaron entre `0 h 40 min` y `2 h 30 min`, y los `5` casos conformes cerraron el ciclo completo entre `0 h 42 min` y `2 h 35 min`, mientras el diseño simulado falló en horario no hábil (`E-009`), contratista sin ticket (`E-019`) y custodia compartida (`E-015`).
- **Incertidumbres y límites clave:**
  1. Sin **`P-01`**, se desconocen el SLA real (`C-01`), la arquitectura real y las causas raíz reales.
  2. Sin **`P-04`** (conciliación periódica detectiva), **no es posible determinar si un control compensatorio habría detectado y cerrado una falla como `E-019` (`41 d 11 h 59 m`) dentro del semestre**.
  3. **`P-05` parcial** (sin validación con custodios), datos ficticios y muestra dirigida (`n = 8`) no generalizable (aseguramiento ilustrativo, nunca absoluto).

---

## 7. Plan de acción propuesto

*(Responsables, plazos y cuentas pertenecen al escenario simulado; no representan compromisos ni arquitectura real de Bancolombia S.A.).*

| ID del hallazgo | Acción propuesta | Responsable propuesto | Prioridad y justificación | Plazo propuesto | Evidencia de cierre |
|---|---|---|---|---|---|
| **`H-01`**: Demora severa y omisión de desactivación privilegiada (`CTRL-01`) | **Fase 1 (Contención):** dar de baja `adm_sop_019` (`E-019`), revocar sesiones y depurar los retiros vigentes en IAM.<br>**Fase 2 (Estructural):** diagnosticar causas (contratistas y 24/7), automatizar flujo GH/Contratación→ITSM/IAM con revocación forzada 24/7 según SLA aprobado y verificar vía conciliación periódica (`P-04`). | Líder de Seguridad IAM / Control de Accesos *(propuesto, coord. GH y Contratación)* | **Alta:** deja cuentas nominales con privilegios vigentes tras el retiro (`41 d 11 h 59 m` en `E-019` y `65 h 15 m` en `E-009`), con riesgo directo de acceso no autorizado sobre soporte a *Mi Bancolombia*. | **Contención:** ≤ 48 h propuestas.<br>**Estructural:** ≤ 30 días calendario propuestos. | **Fase 1:** ticket y log de baja de `adm_sop_019` + acta de barrido sin remanentes activos.<br>**Fase 2:** diagnóstico de causa raíz, pase a producción automático 24/7, reprueba controlada (`≥ 5` retiros o primer ciclo tras cambio) conforme al SLA aprobado y primera conciliación periódica con diferencias trazadas y cerradas. |
| **`H-02`**: Omisión de reasignación y rotación de secreto en cuenta compartida (`svc_pagos_ops`) | Actualizar inventario PAM (custodio principal/alterno); **validar dependencias operativas**, reasignar y rotar `svc_pagos_ops`, activar disparador automático por baja y evaluar cuentas nominales o rotación automatizada. | Líder de Infraestructura / Plataforma y Custodio Líder PAM *(propuestos)* | **Media-Alta:** aunque la cuenta nominal cerró en plazo (`1 h 50 min`), la credencial compartida sin rotar (`84 d 5 h 59 m`) habilita acceso transversal encubierto y rompe el no repudio individual. | ≤ 15 días calendario propuestos. | Análisis de impacto en dependencias, timestamp de rotación de `svc_pagos_ops` en gestor PAM, ticket de reasignación vigente, inventario actualizado y prueba controlada de disparo automático por baja. |

---

## 8. Referencias y anexos

### 8.1 Repositorio del curso
- **Repositorio base:** [`Auditoria-de-Sistemas-Samuel-Muriel-Meneses`](https://github.com/SamuelMurielM/Auditoria-de-Sistemas-Samuel-Muriel-Meneses)
- **Taller 1 (Marcos):** [`Taller Auditoria Bancolombia.md`](https://github.com/SamuelMurielM/Auditoria-de-Sistemas-Samuel-Muriel-Meneses/blob/main/Taller%20Auditoria%20Bancolombia.md)
- **Sesión 7 (Matriz):** [`Matriz de riesgos Bancolombia - Actualizada.md`](https://github.com/SamuelMurielM/Auditoria-de-Sistemas-Samuel-Muriel-Meneses/blob/main/Matriz%20de%20riesgos%20Bancolombia%20-%20Actualizada.md)
- **Entregable 2 (Plan R-02):** [`Entregable 2 - Auditoría de Sistemas.md`](https://github.com/SamuelMurielM/Auditoria-de-Sistemas-Samuel-Muriel-Meneses/blob/main/Entregable%202%20-%20Auditor%C3%ADa%20de%20Sistemas.md)
- **Informe final:** `Taller final - Informe de auditoría y plan de acción.md` *(para carga en `main` al momento de la entrega)*.

### 8.2 Fuentes consultadas y salvedades
- **Bancolombia S.A. (2026).** *Informe de gestión 2025* (cifras año 2025). [grupocibest.com](https://www.grupocibest.com/corporativo/informe-gestion)
- **Duque, J. (2026).** *Taller: Elige el marco correcto para tu auditoría*; *Taller: matriz inicial de riesgos de sistemas*; *Taller: del riesgo priorizado al plan de auditoría*; y *Taller final: informe de auditoría y plan de acción*. Curso Auditoría de Sistemas (ET0114).
- **ISACA.** *COBIT 2019* (nota pública *DSS05.04* en [ISACA Journal](https://www.isaca.org/resources/isaca-journal/issues/2022/volume-3/integrating-mitre-with-cobit); consultar texto licenciado oficial en auditoría real).
- **ISO (2022).** *ISO/IEC 27001:2022*. [iso.org/standard/27001](https://www.iso.org/standard/27001) *(consultar edición autorizada y SoA antes de calificar controles reales)*.
- **República de Colombia / SFC.** *Ley 1581 de 2012* ([Función Pública](https://www1.funcionpublica.gov.co/eva/gestornormativo/norma.php?i=49981)) y *CBJ Parte I* ([SFC](https://www.superfinanciera.gov.co/publicaciones/10083444/normativanormativa-generalcircular-basica-juridica-ce-parte-i-instrucciones-generales-aplicables-a-las-entidades-vigiladas-10083444/)) *(verificar vigencia consolidada con Legal/Cumplimiento)*.

---

## Anexo A — Papel de trabajo `PT-01` (Reproducible — Datos simulados)

| Atributo de control | Especificación de `PT-01` |
|---|---|
| **ID / Control / Riesgo** | `PT-01` · Prueba simulada de `CTRL-01` (notificación, baja IAM, revocación de sesión y custodia PAM) · **`R-02` (`A-02`)** |
| **Responsable del control (sim.)** | **Líder / Coordinación de Control de Accesos (IAM/PAM)** en articulación con Gestión Humana/Contratación *(modelo simulado; por confirmar en `P-01`)*. |
| **Ventana y corte único** | **`2026-04-01 00:00` a `2026-09-30 23:59`** · Zona horaria: **`America/Bogota` (`UTC-5`)** · Snapshot único: **`2026-09-30 23:59`** |
| **Criterio (`C-01-SIM`)** | SLA ficticio: **≤ 4 h continuas 24/7** desde `fecha_hora_retiro_UTC5` en `FUENTE-GH-SIM`. |
| **Pasos y datos comparados** | 1. Validar totales (`24 = 24`, `68`, `6`) y cruzar `FUENTE-GH-SIM ↔ FUENTE-IAM-SIM ↔ FUENTE-PAM-SIM` por `id_pseudonimo` (`P-02`).<br>2. Seleccionar muestra estratificada (`n = 8`, tabla A.2).<br>3. Comparar `fecha_hora_retiro_UTC5` frente a `ts_ticket`, `ts_baja_iam`, `ts_revoc_sesion`, `ts_reasignacion`/`ts_rotacion_secreto` y verificar `ejecutor_autorizado = S` (`P-03`).<br>4. Inspeccionar `ts_ultimo_log_auth` hasta `2026-09-30 23:59`. |
| **Condición de excepción** | Falla cualquiera de los umbrales: (a) `Δ baja IAM > 4 h` o sin ticket/baja al corte (`estado = Activa`); (b) `Δ revocación sesión > 4 h` o sin evento explícito de revocación por retiro; (c) en cuenta PAM, `Δ reasignación/rotación > 4 h` o sin rotación/reasignación al corte; o (d) ejecutor no autorizado / accesos exitosos post-retiro. |
| **Preparado / Entorno** | Samuel Muriel Meneses (`2026-11-17`) · Datos 100 % ficticios y seudonimizados (`E-001`..`E-024`), sin credenciales reales. |

### A.1 Diccionario mínimo de fuentes simuladas y conciliación (`P-02`)

1. **`FUENTE-GH-SIM`:** `{id_pseudonimo, vinculo [Empleado|Contratista], fecha_hora_retiro_UTC5, motivo [Voluntario|Terminacion|Urgente]}` · Filtro: retiros efectivos en ventana de titulares con privilegios previos · **Total:** **`24` registros** (`16` emp., `8` cont.).
2. **`FUENTE-IAM-SIM`:** `{cuenta_id, id_pseudonimo, estado_al_corte, ticket_itsm_id, ts_ticket, ejecutor_id, ejecutor_autorizado [S|N], ts_baja_iam, ts_revoc_sesion, ts_ultimo_log_auth, excepcion_aprobada}` · Universo al corte: **`68` cuentas** (`44` activas vigentes + `23` desactivadas de retirados + `1` de retirado aún activa [`adm_sop_019`]); `23` tickets de baja (`1` ausente en `E-019`). Regla de cruce exacto por `id_pseudonimo`: **`24 = 24` conciliados (0 huérfanos en GH)**.
3. **`FUENTE-PAM-SIM`:** `{cuenta_nopers_id, tipo [Emergencia|Tecnica_Compartida], custodio_id, ts_reasignacion, nuevo_custodio_id, ts_rotacion_secreto}` · Universo: **`6` cuentas** (`4` emergencia, `2` compartidas técnicas), **`2`** con custodio retirado en el periodo (`E-012` → `pam_emerg_02`; `E-015` → `svc_pagos_ops`).

### A.2 Estratificación de `N = 24` y selección de `n = 8`

| Estrato | Descripción (`N = 24`) | `N` | Regla de selección | Casos (`n = 8`) |
|---|---|---:|---|---|
| **A. Alertas `P-02`** | Discrepancias en cruce poblacional (`baja > 4h`, `activa al corte` o `custodia PAM abierta`). | `3` | Censo 100 % del estrato con alerta (`2` emp., `1` cont.). | `E-009`, `E-015`, `E-019` |
| **B. PAM sin alerta** | Otros retirados con custodia en `FUENTE-PAM-SIM`. | `1` | Censo 100 % del estrato PAM para contraste con `E-015`. | `E-012` |
| **C. Emp. sin alerta** | Empleados retirados sin alerta (`7` en Q2, `6` en Q3). | `13` | `1` caso representativo por trimestre/módulo crítico: soporte Q2 (`E-003`) y pagos Q3 (`E-017`). | `E-003`, `E-017` |
| **D. Cont. sin alerta** | Contratistas retirados sin alerta (`3` Q2 vespertinos, `4` Q3). | `7` | `1` retiro `17:00` en Q2 comparable a `E-009` (`E-006`) + `1` terminación urgente Q3 próxima al corte (`E-022`). | `E-006`, `E-022` |
| **Totales** | **`16` emp. + `8` cont.** | **`24`** | **Muestra dirigida estratificada (`5` emp. + `3` cont.)** | **`8` casos** |

### A.3 Matriz completa de trazabilidad por caso (`PT-01`, `COT / UTC-5`)

| Caso (`Vínculo`) | Cuenta(s) sim. | Retiro efectivo (`GH`) | Ticket ITSM (`ID` / `ts` / `Δ`) | Ejecutor (`¿Autorizado?`) | Baja IAM (`ts` / `Δ`) | Revoc. sesión (`ts` / `Δ`) | Custodia PAM (`ts` / `Δ` o corte) | Excep. | `ts_ultimo_log_auth` / Post-retiro hasta `09-30 23:59` | Resultado |
|---|---|---|---|---|---|---|---|---|---|---|
| **`E-003`** (Emp.) | `adm_core_003` | `2026-04-14 16:00` (Mar) | `INC-SIM-4012` `16:12` (`+0h 12m`) | `IAM-OP-01` (`Sí`) | `17:05` (`1h 05m`) | `17:08` (`1h 08m`) | N/A | No | `04-14 15:40` / `0` exitosos post-retiro | **CUMPLE** |
| **`E-006`** (Cont.) | `adm_red_006` | `2026-05-05 17:00` (Mar) | `INC-SIM-4198` `17:40` (`+0h 40m`) | `IAM-OP-02` (`Sí`) | `19:30` (`2h 30m`) | `19:35` (`2h 35m`) | N/A | No | `05-05 16:45` / `0` exitosos post-retiro | **CUMPLE** |
| **`E-009`** (Emp.) | `adm_app_009` | `2026-06-12 17:00` (Vie) | `INC-SIM-4510` `06-15 08:30` (`+63h 30m`) | `IAM-OP-01` (`Sí`) | `06-15 10:15` (`65h 15m`; `1h 45m` tras ticket) | **Sin evento** (timeout inact. 2h desde `16:55` → `06-12 18:55`) | N/A | No | `06-12 16:55` / `0` exitosos post-retiro | **EXCEPCIÓN `H-01`** |
| **`E-012`** (Emp.) | `adm_bd_012` + `pam_emerg_02` | `2026-06-24 11:00` (Mié) | `INC-SIM-4633` `11:18` (`+0h 18m`) | `IAM-OP-01` / `PAM-OP-01` (`Sí`) | `12:20` (`1h 20m`) | `12:22` (`1h 22m`) | Reasig. `EMP-ALT-012` `13:10` + rot. `13:15` (`2h 15m`) | No | `06-24 10:50` / `0` exitosos de `E-012` | **CUMPLE** |
| **`E-015`** (Emp.) | `adm_pag_015` + `svc_pagos_ops` | `2026-07-08 18:00` (Mié) | `INC-SIM-4790` `18:25` (`+0h 25m`) | `IAM-OP-02` (`Sí` IAM; s/o PAM) | `19:45` (`1h 45m`) | `19:50` (`1h 50m`) | **Sin reasig./rotar** (`84d 5h 59m` = `2021h 59m`) | No | `07-08 17:40` / `0` atribuibles a `E-015` (sin indiv. plena) | **EXCEPCIÓN `H-02`** |
| **`E-017`** (Emp.) | `adm_pag_017` | `2026-07-29 09:00` (Mié) | `INC-SIM-4915` `09:20` (`+0h 20m`) | `IAM-OP-03` (`Sí`) | `11:00` (`2h 00m`) | `11:10` (`2h 10m`) | N/A | No | `07-29 08:45` / `0` exitosos post-retiro | **CUMPLE** |
| **`E-019`** (Cont.) | `adm_sop_019` | `2026-08-20 12:00` (Jue) | **Sin ticket ITSM** | `N/A` (sin baja) | **Activa al corte** (`41d 11h 59m` = `995h 59m`) | **Sin revocación** | N/A | No | `08-20 11:30` / `0` exitosos post-retiro | **EXCEPCIÓN `H-01`** |
| **`E-022`** (Cont.) | `adm_api_022` | `2026-09-14 14:00` (Lun) | `INC-SIM-5304` `14:05` (`+0h 05m`) | `IAM-OP-01` (`Sí`) | `14:40` (`0h 40m`) | `14:42` (`0h 42m`) | N/A | No | `09-14 13:50` / `0` exitosos post-retiro | **CUMPLE** |
