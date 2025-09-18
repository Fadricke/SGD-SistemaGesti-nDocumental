# 🏛️ Arquitectura del Sistema - Sistema de Gestión Documental (SGD)

El **Sistema de Gestión Documental (SGD)** fue desarrollado bajo una **arquitectura en capas**, asegurando separación de responsabilidades, escalabilidad y facilidad de mantenimiento.

---

## 🔹 Diagrama de Arquitectura

```mermaid
flowchart TD
  UI["🖥️ Capa de Presentación
(Windows Forms)"]
  BLL["⚙️ Capa de Negocio
  (Reglas de Negocio)"]
  DAL["💾 Capa de Acceso a Datos
  (Procedimientos almacenados)"]
  DB["🗄️ SQL Server
  (Base de datos)"]

  UI --> BLL
  BLL --> DAL
  DAL --> DB
