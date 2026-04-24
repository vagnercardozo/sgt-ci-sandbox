# sgt-ci-sandbox

Sandbox para validar configurações de CI/CD no GitHub usando PHP + Pest.

## Regras de CI configuradas

1. **Tests (`.github/workflows/tests.yml`)** — executa o Pest em todo PR mirando `develop`.
2. **Enforce source branch (`.github/workflows/enforce-source-branch.yml`)** — falha o PR se ele mirar `staging` ou `production` e não vier de `develop`.

## Fluxo esperado

```
feature/* ──► develop ──► staging ──► production
```

- Qualquer branch pode abrir PR para `develop` (testes rodam).
- Somente `develop` pode abrir PR para `staging`.
- Somente `develop` pode abrir PR para `production`.

## Rodando os testes localmente

```bash
composer install
vendor/bin/pest
```
