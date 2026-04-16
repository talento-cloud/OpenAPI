# AGENTS.md

This file provides guidance to Agents when working with code in this repository.

## Project Overview

This repository contains OpenAPI documentation for the Talento Cloud REST API, which provides data to external consumers (e.g., datalake, chatbots) and internal modules. The API is documented using OpenAPI 3.0 specification files and rendered as HTML documentation using Redocly CLI.

## Repository Structure

The repository is organized by functional modules, each in its own directory:

- **autogestion/** - Self-service module (certificates, payslips, vacations)
- **autogestion_ausentismos/** - Absence management
- **competencias360/** - 360-degree competency assessments
- **datalake/** - Public API for external data providers with OAuth 2.0 authentication
- **disciplinarios/** - Disciplinary processes
- **estructura_organizacional/** - Organizational structure
- **magneto/** - Magneto module
- **objetivossmart_chatbot/** - SMART objectives chatbot API
- **seleccion/** - Selection/recruitment processes
- **transversal/** - Cross-cutting/shared user data
- **gral/** - General reference and legacy files

Each module directory contains:
- `openapi.yaml` - OpenAPI specification
- `index.html` - Generated HTML documentation
- `README.md` - Module-specific instructions
- `custom-template.hbs` (some modules) - Custom Handlebars template for documentation rendering. Optional

## Common Commands

### Generate HTML Documentation

From a module directory:
```bash
npx @redocly/cli build-docs openapi.yaml -t ../custom-template.hbs -o index.html
```

Or for modules with their own template:
```bash
npx @redocly/cli build-docs openapi.yaml -t custom-template.hbs -o index.html
```

### Validate OpenAPI Specification

```bash
redocly lint --extends=minimal ./openapi.yaml
```

### Split Large OpenAPI Files

```bash
redocly split ./TalentoPublicoOpenApi3Json.json --outDir=openapi
```

### Bundle Split Files

```bash
redocly bundle openapi/openapi.json --output dist/openapi.json
```

### Install Redocly CLI Globally

```bash
npm install -g @redocly/cli
```

## API Architecture

### Authentication

The datalake API uses OAuth 2.0 client credentials flow:

```bash
curl -X POST https://clientex.talento.cloud/oauth2/token \
  -H "Content-Type: application/x-www-form-urlencoded" \
  -d "grant_type=client_credentials" \
  -d "client_id=webhook-servicio" \
  -d "client_secret=mi-secreto" \
  -d "scope=talento.read"
```

### Server Environments

- **Production**: `https://clientex.talento.cloud/api`
- **Development**: `https://clientex.talento-dev.cloud/api`

### Response Format

All API responses follow this structure:

```json
{
  "codigo": 200,
  "mensaje": "OK",
  "data": {
    "reporte": []
  }
}
```

### Error Codes

- `400 Bad Request` - Missing or invalid parameters
- `401 Unauthorized` - Invalid, expired, or missing JWT token
- `403 Forbidden` - Insufficient permissions
- `404 Not Found` - Resource not found
- `500 Internal Server Error` - Unexpected server error

## Working with OpenAPI Files

When editing OpenAPI specifications:

1. Maintain consistent structure across modules
2. Use the existing `openapi.yaml` format (YAML, not JSON)
3. Include proper error response documentation
4. Follow the standard response format with `codigo`, `mensaje`, and `data` fields
5. Document authentication requirements per endpoint
6. Validate changes with `redocly lint` before generating documentation

## Custom Template

The `custom-template.hbs` file is a Handlebars template that customizes the Redocly documentation output with:
- Talento Cloud logo in header
- Custom favicon
- Centered layout with branding

When creating documentation for a new module, use the root `custom-template.hbs` unless module-specific customization is needed.

## Useful Tools

- **VS Code Extension**: OpenAPI (Swagger) Editor by 42Crunch
- **API Transformer**: https://www.apimatic.io/transformer (for migrating from Postman to OpenAPI)

## References

- Redocly documentation: https://redocly.com/docs/cli/commands/build-docs
- Redoc GitHub: https://github.com/Redocly/redoc
