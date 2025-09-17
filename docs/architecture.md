# Arquitectura del SGD

El SGD está diseñado sobre una **arquitectura en capas** (three-tier):  
- **Presentación (UI)**: formularios WinForms / WPF (según la implementación), interacción con el usuario.  
- **Lógica de negocio**: validaciones, reglas, servicios que orquestan operaciones.  
- **Acceso a datos**: repositorios/DAOs que ejecutan queries y llaman a procedimientos almacenados en SQL Server.

```mermaid
flowchart TB
  UI[Presentación (UI)]
  BL[Lógica de Negocio]
  DAL[Acceso a Datos]
  DB[(SQL Server)]

  UI --> BL
  BL --> DAL
  DAL --> DB
