# Demo NATS Microservices

Demo de microservicios basado en **NestJS + NATS + PostgreSQL**, diseñado para simular comunicación asíncrona entre servicios mediante eventos.

## Objetivo

Este proyecto demuestra cómo varios microservicios pueden comunicarse usando un broker de mensajería (**NATS**) para procesar eventos desacoplados, manteniendo una arquitectura escalable, observable y fácil de extender.

## Arquitectura general

Componentes principales del demo:

- **Gateway / API Service**: expone endpoints HTTP para iniciar operaciones.
- **Orders Service**: registra órdenes y publica eventos.
- **Notifications Service**: consume eventos y genera notificaciones.
- **NATS Server**: broker de mensajería.
- **PostgreSQL**: persistencia de datos.

## Repositorios

| Repositorio | Descripción | Puerto | Estado |
|---|---|---:|---|
| `demo-nats-orders` | Servicio de órdenes | 3001 | Activo |
| `demo-nats-notifications` | Servicio de notificaciones | 3002 | Activo |
| `demo-nats-gateway` | API Gateway / entrada principal | 3000 | Activo |
| `demo-nats-infra` | Docker Compose, NATS y PostgreSQL | - | Activo |

## Tecnologías usadas

- NestJS
- NATS
- PostgreSQL
- Prisma
- Docker / Docker Compose
- Swagger / Scalar

## Flujo funcional resumido

1. El cliente envía una solicitud HTTP al Gateway.
2. El Gateway delega la operación al servicio correspondiente.
3. El servicio registra información en la base de datos.
4. El servicio publica un evento en NATS.
5. Otro microservicio consume el evento y ejecuta acciones derivadas.
6. El resultado puede consultarse vía endpoint o logs.

## Prerrequisitos

Antes de levantar el proyecto, asegúrate de tener instalado:

- Node.js 20+
- npm 10+ o pnpm
- Docker
- Docker Compose
- Git

## Estructura de repositorios

```bash
demo-nats/
  demo-nats-infra/
  demo-nats-gateway/
  demo-nats-orders/
  demo-nats-notifications/