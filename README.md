# Oficina — API

Aplicação principal do sistema da oficina, executada em Kubernetes.

## Responsabilidades planejadas

- API FastAPI e regras de negócio;
- testes unitários e de integração;
- migrations Alembic;
- construção e publicação da imagem Docker;
- manifests Kubernetes específicos da aplicação;
- execução de migrations e rollout por ambiente;
- validação e autorização dos tokens JWT.

## Ambientes e branches

| Branch | Ambiente | Overlay de deploy |
|---|---|---|
| `staging` | Homologação | `deploy/overlays/staging` |
| `main` | Produção | `deploy/overlays/production` |

A branch `main` não deverá receber commits diretos; a promoção ocorrerá por Pull
Request após a validação em homologação.

## Dependências planejadas

- imagem publicada no ECR provisionado por `oficina-infra-kubernetes`;
- execução no EKS do ambiente correspondente;
- conexão com o RDS provisionado por `oficina-infra-database`;
- exposição externa exclusivamente pelo Kong.

## Limites deste repositório

Não pertencem a este repositório:

- criação do EKS, ECR ou rede;
- instalação e configuração global do Kong;
- criação do RDS;
- código da função serverless de autenticação.

## Estrutura inicial

```text
.
├── .github/workflows/
├── deploy/
│   ├── base/
│   └── overlays/
│       ├── staging/
│       └── production/
└── docs/
```

## Status

Estrutura inicial. Aplicação, manifests e CI/CD ainda não foram migrados.
