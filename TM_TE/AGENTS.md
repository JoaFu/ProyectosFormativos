# Instrucciones de mantenimiento — Simulación TE/TM

## Alcance y prioridades
Proyecto académico de Teoría Electromagnética 2, Universidad del Valle de Guatemala.
Implementa y visualiza soluciones analíticas conocidas para una guía rectangular
ideal PEC con medio homogéneo, lineal, isotrópico y sin pérdidas. No atribuir una
deducción original de esas soluciones al proyecto.

Conservar las interfaces públicas de modos.py, campos.py, validacion.py y graficas.py.
app.py integra los módulos sin duplicar sus cálculos. Inspeccionar los archivos
antes de editar. Hacer cambios puntuales; no añadir 3D, FDTD, FEM, pérdidas u otras
geometrías sin una solicitud expresa. Comentarios y mensajes en español.

## Convenciones físicas
- Sección 0≤x≤a, 0≤y≤b; propagación en z; unidades internas SI.
- Convención exp(jωt−jβz); para evanescencia β=−jα con α>0.
- TE: m,n enteros no negativos y m+n>0. TM: m,n≥1.
- Distinguir modo inexistente, propagante, evanescente y en el corte.
- No imponer máximos modales físicos arbitrarios. Informar límites de precisión,
  resolución y recursos del equipo.
- Amplitud longitudinal H₀=1 A/m para TE y E₀=1 V/m para TM por defecto.
- No cambiar ecuaciones, convenciones ni tolerancias sin fundamento y pruebas.

## Desarrollo y comprobación
Entorno comprobado: Windows, Python 3.13.5. Instalar requirements.txt, que usa
requirements-lock.txt para restringir dependencias. No versionar ni distribuir .venv.

```powershell
python -m streamlit run app.py
python -m unittest discover -s tests -v
python -m pip check
python scripts/verificar_resultados.py
python scripts/empaquetar.py
```

La suite contiene 36 pruebas de física, gráficas e integración; conservar las que
comprueban comportamiento real. Los scripts manuales antiguos prueba_campos.py y
prueba_graficas.py fueron retirados por duplicar esa cobertura. Después de cambios,
ejecutar las pruebas relacionadas. Para cambios de interfaz, comprobar además el
navegador; las pruebas no sustituyen la inspección visual. No afirmar que se ha
probado algo sin evidencia ni elevar tolerancias para hacer pasar una prueba.

## Informe y entrega
El informe está en documento_article/Informe_TE_TM.docx. El archivo
SciencePG_Manuscript_Template.docx conserva el borrador original y no se modifica.
Mantener el formato SciencePG y redactar en español, incluida la terminología de
secciones. Conservar los objetivos y relacionar las conclusiones con ellos.
No inventar resultados, validaciones, bibliografía, datos personales ni autorías.
No insertar imágenes: dejar indicaciones en negrilla. La biografía se reserva al autor.
El video se incorpora cuando el usuario lo aporte; no afirmar que ya está entregado.

La entrega compartible se genera en entrega/Simulacion_TE_TM.zip con una lista
explícita de archivos. Excluir entornos, cachés, capturas, instrucciones de agentes,
borradores originales y pruebas de desarrollo. Mantener tests/ en el proyecto de
trabajo. El paquete incluye código, configuración visual, instrucciones, resultados
reproducibles e informe. Validar su integridad antes de compartirlo.

La aplicación está destinada a ejecución local. Una publicación externa o una
capacidad multiusuario solo pueden declararse verificadas después de medirlas.
