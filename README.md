# FORM-AC-01 — Análisis de caso: caída de Cloudflare del 21 de junio de 2022

**Universidad Técnica Estatal de Quevedo** · Facultad de Ciencias de la Computación y Diseño Digital · Carrera de Software

| | |
|---|---|
| Asignatura | Aplicaciones Distribuidas (ISR-701) |
| Actividad | FORM-AC-01 — Análisis de caso: fallo real en un sistema distribuido (grupal, formativa) |
| Caso | Cloudflare, 21 de junio de 2022: retiro de prefijos BGP en 19 centros de datos MCP |
| Docente | Gleiston Guerrero Ulloa, PhD |
| Nivel y paralelo | Séptimo nivel, paralelo B |
| Semana | 3 (9 al 15 de noviembre de 2026) |

## Integrantes (equipo ALM)

| Integrante | A cargo de |
|---|---|
| Apunte Pazmiño Washington German | Repositorio y estructura base · 4. Relación con la Unidad 1 · declaración de uso de IA · hoja del SGA · PDF final |
| Loor Suarez Jordan Josue | 1. Descripción del incidente · 5. Mitigación · 6. Lecciones aprendidas para el PFC (SREI) · tabla de observaciones |
| Macias Vasquez Cesar Abrahan | 2. Causas raíz y diagrama de Ishikawa · 3. Impacto cuantificado · referencias |

## Estructura

```
.
├── main.tex                 # documento principal: carátula, apartados, referencias
├── main.pdf                 # PDF compilado de la versión final
├── referencias.bib          # referencias (biblatex, estilo IEEE)
├── secciones/
│   ├── 01-descripcion.tex
│   ├── 02-causas-raiz.tex
│   ├── 03-impacto.tex
│   ├── 04-unidad1.tex
│   ├── 05-mitigacion.tex
│   ├── 06-lecciones-pfc.tex
│   ├── declaracion-ia.tex
│   └── observaciones.tex
├── diagramas/
│   ├── ishikawa-cloudflare-2022.drawio   # diagrama editable (draw.io)
│   └── ishikawa-cloudflare-2022.pdf      # exportación que incluye main.tex
├── img/                     # logos de la UTEQ y de la Facultad (carátula y hoja del SGA)
├── evaluaciones-pares/      # evaluaciones entre pares recibidas
└── sga/
    ├── entrega-sga.tex      # hoja de una página que se sube al SGA
    └── entrega-sga.pdf
```

## Compilación

- Compilador: pdfLaTeX. Bibliografía: biblatex con Biber, estilo IEEE (`biblatex-ieee`).
- Requisitos: TeX Live 2023 o posterior, o MiKTeX actualizado (instala los paquetes que falten en la primera compilación).

```
pdflatex main.tex
biber main
pdflatex main.tex
pdflatex main.tex
```

También sirve `latexmk -pdf main.tex`. En Overleaf: *New Project → Upload Project* con el ZIP del repositorio, compilador pdfLaTeX y documento principal `main.tex`; Overleaf ejecuta Biber solo.

La hoja del SGA se compila aparte:

```
cd sga
pdflatex entrega-sga.tex
```

### Diagrama de Ishikawa

1. Abrir `diagramas/ishikawa-cloudflare-2022.drawio` en draw.io (app.diagrams.net o la aplicación de escritorio).
2. Después de editarlo: *Archivo → Exportar como → PDF*, marcar *Recortar* y guardar encima de `diagramas/ishikawa-cloudflare-2022.pdf`.
3. Volver a compilar `main.tex`.

### Extensión

Los apartados 1 a 6 ocupan dos páginas (páginas 1 y 2 después de la carátula). Las referencias, la declaración de uso de IA y la tabla de observaciones van a continuación y no cuentan para ese límite.

## Fuentes

Fuente principal (informe oficial de la empresa):

1. T. Strickx y J. Hartman, "Cloudflare outage on June 21, 2022", *The Cloudflare Blog*, 21 de junio de 2022. <https://blog.cloudflare.com/cloudflare-outage-on-june-21-2022/>

Fuentes complementarias con DOI (metadatos comprobados en Crossref el 14/11/2026):

2. Y. Rekhter *et al.*, "A Border Gateway Protocol 4 (BGP-4)", RFC 4271, 2006. DOI: [10.17487/RFC4271](https://doi.org/10.17487/RFC4271)
3. M. van Steen y A. S. Tanenbaum, "A brief introduction to distributed systems", *Computing*, 2016. DOI: [10.1007/s00607-016-0508-7](https://doi.org/10.1007/s00607-016-0508-7) (acceso abierto)
4. S. Gilbert y N. Lynch, "Brewer's conjecture and the feasibility of consistent, available, partition-tolerant web services", *ACM SIGACT News*, 2002. DOI: [10.1145/564585.564601](https://doi.org/10.1145/564585.564601) (acceso abierto)
5. R. Govindan *et al.*, "Evolve or die: High-availability design principles drawn from Google's network infrastructure", ACM SIGCOMM 2016. DOI: [10.1145/2934872.2934891](https://doi.org/10.1145/2934872.2934891) (acceso abierto)

Reportes de clientes afectados y acuerdo de nivel de servicio:

6. GitLab, incidente de producción n.º 7288: <https://gitlab.com/gitlab-com/gl-infra/production/-/issues/7288>
7. Acquia Status, incidente del 21/06/2022: <https://status.acquia.com/incidents/sdxb90z6d0vn>
8. Cloudflare, *Business Service Level Agreement*: <https://www.cloudflare.com/business-sla/>

La numeración de esta lista no coincide con la del PDF; en el PDF las referencias van en orden de aparición.

## Uso de inteligencia artificial

La declaración está al final de `main.pdf` (archivo `secciones/declaracion-ia.tex`).

## Evaluaciones entre pares

Ver la carpeta `evaluaciones-pares/`.
