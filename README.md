# BD_ConsultoraDeRestaurantes
Base de datos relacional para una consultora de restaurantes desarrollada en SQL Server 2014, incluye modelo lógico, script SQL e informe técnico.
Proyecto académico de Base de Datos Relacional desarrollado en SQL Server 2014, orientado a la gestión y consulta de información sobre restaurantes, clientes, platos y consultas históricas, aplicando buenas prácticas de modelado, integridad y normalización.

**Objetivo del proyecto**
- Diseñar e implementar una base de datos relacional que permita:
- Registrar restaurantes y su ubicación
- Gestionar clientes y sus datos de contacto
- Administrar platos, menús y estados de disponibilidad
- Almacenar consultas realizadas por los clientes (históricas)
- Garantizar integridad referencial y consistencia de datos

**Tecnologías utilizadas**
- SQL Server 2014
- SQL Server Management Studio (SSMS)
- Modelo relacional normalizado
- Script SQL completo (DDL + DML)

**Estructura de la Base de Datos** :
Entidades principales:
- Distrito
- Cliente
- Restaurante
- Plato
- Menu
- Estado
- Consultas
- Telefonos_Cliente
- Telefonos_Rest

**Llaves primarias y foráneas**
- Uso de PRIMARY KEY en todas las tablas
- Relaciones definidas mediante FOREIGN KEY
- Implementación de reglas de integridad (según la lógica del negocio) con:
  - ON UPDATE CASCADE
  - ON DELETE CASCADE / NO ACTION
Ejemplo conceptual:
- Un Distrito puede tener muchos Clientes, pero eliminar un distrito no elimina clientes
- Un Menú depende de Plato y Restaurante
- Las Consultas son históricas y no se eliminan automáticamente

**Reglas de negocio implementadas** :
ON DELETE / ON UPDATE
Se definieron reglas explícitas para cada relación, por ejemplo:
- Eliminación en cascada para datos dependientes (menús, teléfonos)
- Protección de datos históricos (consultas)

**Check Constraints** :
Se aplicaron CHECK CONSTRAINTS para validar datos:
- RUC solo numérico
- DNI con longitud fija
- Precios mayores a cero
- Validación de formatos básicos
Ejemplo:
  CHECK (RUC_Rest NOT LIKE '%[^0-9]%')

**Índices**
- Índices implícitos por claves primarias
- Optimización de búsquedas frecuentes
- Mejora del rendimiento en consultas por cliente, restaurante y plato

**Columnas IDENTITY**
- Uso de IDENTITY(1,1) para claves autonuméricas
- Evita inserciones manuales erróneas
- Asegura unicidad y orden lógico
Ejemplo:
  ID_Consulta INT IDENTITY(1,1)

**Datos de prueba**
- Inserción ordenada respetando dependencias
- Fechas en formato compatible con SQL Server
- Datos realistas para validación funcional

**Stored Procedures**
- Se implementaron procedimientos almacenados para:
- Insertar registros
- Actualizar datos de clientes
- Buscar información por distintos criterios
- Eliminar registros de forma controlada

**Estructura del repositorio**
- BD_ConsultoraDeRestaurantes/
  -│
  -├── Script_BD_Proyecto.sql
  -├── Informe_Final_BD.docx
  -└── README.md

**Contexto académico**
- Proyecto desarrollado como parte del curso de Base de Datos, aplicando:
- Modelo relacional
- Integridad referencial
- Buenas prácticas de diseño
- Documentación técnica

**Licencia**
- Proyecto con fines educativos.
