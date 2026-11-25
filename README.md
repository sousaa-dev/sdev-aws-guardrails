# SDEV · AWS Guardrails

![AWS](https://img.shields.io/badge/AWS-Security-FF9900?logo=amazonwebservices) ![Scope](https://img.shields.io/badge/Scope-Defensive%20Labs-12345A)

## 🇺🇸 English

An AWS defensive architecture study portfolio. Ten guided labs cover governance, access control, storage protection, network design, auditing, recovery and cost planning. Includes a CloudFormation storage baseline, synthetic evidence and an architecture review template.

## 🇧🇷 Português

Portfólio de laboratórios voltados à arquitetura defensiva em nuvem AWS. O trabalho inclui planejamento de controles, revisão técnica de configuração, documentação de evidências e avaliação de riscos. Os cenários são ilustrativos, sem afirmar implantação ou certificação real.

**[Baixar manual de laboratórios (PDF, 19 páginas)](pdf/aws-guardrails-labs.pdf)**

## Trilha de laboratórios

| Lab | Tema | Guia |
|---|---|---|
| 1 | Governança e responsabilidade compartilhada | [Abrir](labs/01.md) |
| 2 | IAM e acesso mínimo | [Abrir](labs/02.md) |
| 3 | Proteção de armazenamento S3 | [Abrir](labs/03.md) |
| 4 | Proteção de dados e chaves | [Abrir](labs/04.md) |
| 5 | Segmentação de rede | [Abrir](labs/05.md) |
| 6 | Auditoria e observabilidade | [Abrir](labs/06.md) |
| 7 | Recuperação e continuidade | [Abrir](labs/07.md) |
| 8 | Resposta e postura de segurança | [Abrir](labs/08.md) |
| 9 | Controle de custos e encerramento | [Abrir](labs/09.md) |
| 10 | Projeto integrador | [Abrir](labs/10.md) |

## Artefatos técnicos

- [CloudFormation: baseline S3](infrastructure/private-storage.yaml): bloqueio público, criptografia e versionamento.
- [Arquitetura lógica](architecture/overview.md): limites e fluxo de dados conceitual.
- [Eventos fictícios](examples/audit-events.jsonl): dados para triagem e revisão.
- [Matriz de evidências](checklists/control-evidence.csv): critérios, responsáveis e status.
- [Ficha de laboratório](templates/lab-report.md): registro de decisões e resultados.

## Execução e validação

Leia o guia, revise o template e preencha a matriz de evidências. Não há implantação automática: qualquer uso em AWS real exige conta autorizada, revisão de custos e aprovação das alterações. CloudFormation é apresentado como infraestrutura declarativa de referência. Os guias não contêm credenciais nem dependem de contas reais.

## Arquitetura e critérios

Os controles devem possuir proprietário, finalidade, evidência e periodicidade. A conclusão de um laboratório depende da revisão dos artefatos e não significa que controles foram implantados em uma organização.

## Referências

- [AWS Well-Architected Security Pillar](https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/)
- [AWS CloudFormation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html)

## Project history / Histórico do projeto

Previously maintained in another personal account, the project was revised and migrated to consolidate my professional portfolio.

Anteriormente mantido em outra conta pessoal, o projeto foi revisado e migrado para consolidar meu portfólio profissional.

Pablo Sousa Ribeiro · [GitHub](https://github.com/sousaa-dev)

## Edição acadêmica revisada (2026)

- [Manual completo em PDF](pdf/aws-guardrails-labs.pdf) — 19 páginas, 16 capítulos, capa, sumário e referências.
- [Versão editável em Markdown](manual/edicao-revisada.md)

1. Fundamentos e responsabilidade compartilhada
2. Regiões, disponibilidade e arquitetura
3. IAM e separação de funções
4. Identity Center, organizações e governança
5. VPC e segmentação
6. EC2 e proteção de compute
7. Proteção de armazenamento S3
8. KMS e Secrets Manager
9. CloudTrail e CloudWatch
10. AWS Config e governança de configuração
11. GuardDuty, Security Hub e Inspector
12. Proteção de aplicações e WAF
13. AWS Backup e continuidade
14. CloudFormation e infraestrutura como código
15. Custos, orçamento e encerramento
16. Resposta a incidentes e arquitetura integradora

Os cenários e atividades são propostas educacionais; não constituem evidência de implantação real.
