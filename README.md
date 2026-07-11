# AUY1104_Primary_Fork — Entorno de pruebas de la plantilla reutilizable

Este repositorio es un **fork de `AUY1104_PRUEBA_2_Primary`** usado como
entorno de staging/pruebas: aquí se prototipan y validan cambios al pipeline
reutilizable (blue-green, validación de salud, remediación) antes de
promoverlos al repo `Primary` (que es el que consumen las apps en
producción, como `AUY1104_PRUEBA_2_Apache`).

## Qué se probó aquí antes de mergear a Primary

- Se detectó que el job `build-and-push` original no tenía pasos reales de
  build/push (bug corregido en la versión final).
- Se prototipó el mecanismo de rollback (`kubectl rollout status` +
  `kubectl rollout undo`), que evolucionó hasta el enfoque final de
  Blue-Green con Validación de Salud + watchdog en tiempo real que hoy vive
  en `Primary`.

## Estado actual

El archivo `.github/workflows/deploy-api.yaml` de este repo está sincronizado
con la versión final de `Primary` (ver ese repo para el detalle completo de
cada etapa, documentado en su README).

![dohenknow](dohenknow.jpg)
