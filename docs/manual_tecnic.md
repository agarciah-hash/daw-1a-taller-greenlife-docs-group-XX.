# Manual tècnic - GreenLife


## Arquitectura
Aplicació client-servidor amb API REST.


## Tecnologies
- Backend: Node.js
- Frontend: React
- Base de dades: PostgreSQL

## Autenticació JWT
L'aplicació utilitza JSON Web Tokens (JWT) per a la gestió de sessions i l'autenticació segura dels usuaris:
- **Generació de tokens:** En fer un login correcte, el servidor genera un token JWT signat amb una clau secreta (`JWT_SECRET`).
- **Encapçalera d'autorització:** Per accedir a les rutes protegides de l'API, el client ha d'enviar el token a l'encapçalera HTTP: `Authorization: Bearer <token>`.
- **Validació:** El middleware del backend verifica la validesa i l'expiració del token abans de processar qualsevol petició als endpoints privats.

## Estructura del codi
- `/backend` - API i lògica de negoci
- `/frontend` - Interfície d'usuari
- `/database` - Migracions i models
