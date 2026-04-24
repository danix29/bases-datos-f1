# 🏁 Base de Datos Fórmula 1

> **Asignatura**: Bases de Datos — UAH  
> **Curso**: 2025-26  
> **Stack**: SQL · Oracle · Python

## Descripción

Base de datos relacional completa de Fórmula 1 con datos históricos reales.
Incluye consultas avanzadas, lógica de negocio con triggers y
gestión de usuarios con control de acceso por roles.

## Volumen de datos

| Tabla | Registros |
|-------|-----------|
| circuitos | 77 |
| temporadas | 75 |
| escuderías | 212 |
| pilotos | 861 |
| GPS | 1.125 |
| pilotos_corren_gps | 26.685 |
| pilotos_califican_gps | 10.494 |
| vueltas | 589.081 |
| pit stops | 11.371 |

## Consultas implementadas

- Circuitos ordenados por número de GPs albergados
- Pilotos ganadores de al menos un GP
- Piloto con la vuelta más rápida de la historia (sin `LIMIT`)
- Pit stops por piloto en Monaco 2023
- Campeones por temporada (2010-2015) mediante vistas

## Triggers implementados

- **Auditoría**: registra INSERT/UPDATE/DELETE con tabla, usuario y timestamp
- **Puntos acumulados**: actualiza tabla de puntos totales al insertar resultado de carrera

## Roles de usuario

| Rol | Permisos |
|-----|----------|
| Admin | Todo |
| Gestor | DML (no DDL) |
| Analista | Solo SELECT |
| Invitado | SELECT limitado (sin vueltas ni pit stops) |

## Conector Python

Script que se conecta a la BD con cualquier usuario,
ejecuta consultas parametrizadas e inserta nuevos GPs
si el usuario tiene permisos suficientes.
