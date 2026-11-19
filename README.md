# ecommerce-aws
# Arquitetura de E-commerce na AWS (IaC)

Projeto de infraestrutura na AWS para uma plataforma de e-commerce com dois microsserviços (catálogo de produtos e processamento de pedidos) e fluxo assíncrono com mensageria e processamento serverless[cite: 2, 3, 4, 5].

## Estrutura de Pastas
- `services/catalogo/`: código do microsserviço de catálogo de produtos e seu `Dockerfile`[cite: 3, 5].
- `services/pedidos/`: código do microsserviço de processamento de pedidos e seu `Dockerfile`[cite: 3, 5].
- `lambda/processar-pedido/`: função Lambda acionada pela fila SQS para processar pedidos e registrar logs no CloudWatch[cite: 5].
- `infra/`: arquivos `.tf` do Terraform organizados por responsabilidade (`variables.tf`, `vpc.tf`, `security.tf`, `compute_alb.tf`, `storage_db.tf`, `messaging_lambda.tf`, `outputs.tf`)[cite: 4, 5, 6].

## Variáveis (`infra/variables.tf`)
As variáveis de entrada do projeto serão declaradas e documentadas em `infra/variables.tf` (sem valores sensíveis hardcoded), tais como:
- `aws_region`: região da AWS onde os recursos serão criados.
- `project_name`: nome/prefixo base para identificar os recursos do projeto.
- `environment`: ambiente de execução (ex.: `dev` ou `prod`).