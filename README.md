# IllustrisTNG-CurvasRotacionBatch

Este repositorio contiene un script en Python que calcula y guarda curvas de rotación estelar (3D y proyectadas) para un conjunto de 100 subhalos centrales simulados en **IllustrisTNG TNG100-1**, snapshot 99 (redshift z ≈ 0).

El análisis está diseñado para generar datos numéricos útiles en estudios de dinámica galáctica, perfiles de velocidad y distribución de materia, con fines comparativos frente a observaciones astronómicas.

---

##  Descripción científica y técnica

Las **curvas de rotación galáctica** muestran cómo varía la velocidad de rotación del material en función de la distancia al centro de una galaxia. En el universo real, estas curvas tienden a aplanarse a grandes radios, lo que indica la presencia de materia oscura. En este proyecto se reproducen estas curvas usando partículas estelares simuladas.

Para ello, el script:

- Filtra **subhalos centrales** con masas estelares entre 10⁹ y 10¹⁰ M☉.
- Centra las partículas utilizando el potencial gravitacional mínimo y aplica **condiciones periódicas de contorno (PBC)**.
- Calcula:
  - La **curva de rotación 3D** a partir de la velocidad tangencial (`v_tan`).
  - La **curva proyectada** en línea de visión (`v_los`).
- Normaliza las distancias por el **radio efectivo estelar R₁/₂**.
- Genera histogramas 2D de densidad estelar y gaseosa usando `np.histogram2d`.
- Maneja la ausencia de gas de forma robusta.
- Guarda todos los resultados en un archivo `.npz` comprimido para análisis posterior.

---

## Contenido del `.npz` generado

El archivo `curvas_rotacion_datos.npz` contiene las siguientes variables:

- `subhalo_ids`: IDs de subhalos seleccionados.
- `r_bins_all`: Radios normalizados (3D).
- `vrot_all`: Curvas de rotación 3D.
- `r_proj_bins_all`: Radios proyectados (en plano XY).
- `vlos_rot_all`: Curvas de rotación proyectadas (v_los).
- `coords_stars_all`: Coordenadas centradas de partículas estelares.
- `coords_gas_all`: Coordenadas centradas del gas (si existe).
- `r_half_all`: Radios efectivos `R₁/₂`.
- `vtan_all`: Velocidades tangenciales por partícula.
- `vlos_all`: Velocidades proyectadas por partícula.
- `hist2d_stars_all`: Histogramas de densidad estelar.
- `hist2d_gas_all`: Histogramas de densidad de gas (si existen).

---
