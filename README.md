# Bookstore API

API simples para gerenciar autores, gêneros e livros.

## Stack
- .NET 8 (ASP.NET Core Web API)
- EF Core 9 (SQL Server)
- Swagger/OpenAPI

## Como rodar (Docker)
- Pré-requisito: Docker e Docker Compose.
- Comando: `docker compose up -d`
- A API sobe em `http://localhost:8080` e HTTPS em `https://localhost:8081`.
- Swagger: `http://localhost:8080/swagger/v1`
- Variáveis úteis: `ConnectionStrings__DefaultConnection` para ajustar a conexão do SQL Server.

## Como rodar (sem Docker)
- Garanta um SQL Server acessível e ajuste `Bookstore.Api/appsettings.json`.
- Comandos:
  - `cd Bookstore.Api`
  - `dotnet run`
- A API inicia em `http://localhost:8080` se configurado via env; caso contrário, porta padrão do Kestrel.

## Endpoints (v1)
- Autores: `api/v1/Authors`
  - `GET /api/v1/Authors` — lista
  - `GET /api/v1/Authors/{id}` — detalhe
  - `POST /api/v1/Authors` — cria
  - `PUT /api/v1/Authors/{id}` — atualiza
  - `DELETE /api/v1/Authors/{id}` — remove
- Gêneros: `api/v1/Genres`
  - `GET /api/v1/Genres` — lista
  - `GET /api/v1/Genres/{id}` — detalhe
  - `POST /api/v1/Genres` — cria
  - `PUT /api/v1/Genres/{id}` — atualiza
  - `DELETE /api/v1/Genres/{id}` — remove (bloqueia se houver livros)
- Livros: `api/v1/Books`
  - `GET /api/v1/Books` — lista
  - `GET /api/v1/Books/{id}` — detalhe
  - `POST /api/v1/Books` — cria
  - `PUT /api/v1/Books/{id}` — atualiza
  - `DELETE /api/v1/Books/{id}` — remove

## Formato de resposta
- Envolvido por `ApiResponse` ou `ApiResponse<T>` com campos `success`, `message`, `data`.

## Projetos
- `Bookstore.Api` — API e configuração (Swagger, versionamento, DI).
- `Bookstore.Infrastructure` — EF Core, `DbContext`, repositórios.
- `Bookstore.Domain` — entidades e contratos.
- `Bookstore.Appication` — DTOs.
- `Bookstore.UnitTests` — testes de unidade.

## Testes
- Comando: `dotnet test`

## Observações
- Troque senhas de exemplo no `docker-compose.yml` e `appsettings.json` para produção.
