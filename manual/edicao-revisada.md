# AWS Guardrails

Cloud Security Engineering Handbook | Arquitetura e laboratórios defensivos

Pablo Sousa Ribeiro | 2026 | Edição revisada

## 1. Fundamentos e responsabilidade compartilhada

### Fundamentação técnica

A AWS fornece infraestrutura e serviços; o cliente permanece responsável pelas decisões de acesso, configuração e tratamento de dados que lhe cabem. As responsabilidades variam entre EC2, bancos gerenciados e armazenamento de objetos. Defina escopo antes de escolher controles.

### Laboratório de arquitetura

Cenário: empresa fictícia com portal e arquivos internos. Objetivo: elaborar matriz de responsabilidade para EC2, RDS e S3, incluindo atualização, identidades, criptografia e backup.

### Entregáveis e critérios

Entregáveis: matriz AWS/cliente, proprietário interno e evidência esperada. Avalie cada responsabilidade com a documentação [1]. Nenhum recurso é provisionado.

## 2. Regiões, disponibilidade e arquitetura

### Fundamentação técnica

Regiões são agrupamentos geográficos de infraestrutura; zonas de disponibilidade permitem distribuir dependências. Escolher região considera latência, residência de dados, disponibilidade de serviços e custo. Redundância depende do desenho da aplicação.

### Laboratório de arquitetura

Proponha duas zonas para uma aplicação fictícia. Documente componentes, dependências, objetivos RTO/RPO e como uma falha de zona afeta o serviço.

### Entregáveis e critérios

Entregáveis: diagrama e tabela de dependências. Critério: nenhuma alegação de disponibilidade sem considerar a camada de dados e recuperação.

## 3. IAM e separação de funções

### Fundamentação técnica

IAM administra identidades e permissões. Papéis oferecem credenciais temporárias; políticas descrevem permissões e condições. O princípio de menor privilégio deve relacionar operação, recurso e finalidade. Revisões periódicas evitam acúmulo de acesso.

### Laboratório de arquitetura

Construa papéis conceituais de desenvolvedor, leitor de auditoria e administrador de plataforma. Liste operações de negócio autorizadas, proprietário, prazo e aprovação. Analise separação de funções.

### Entregáveis e critérios

Entregáveis: matriz de acesso e registro de revisão. Critério: cada permissão tem justificativa, e alterações privilegiadas exigem controle.

## 4. Identity Center, organizações e governança

### Fundamentação técnica

IAM Identity Center integra o acesso de pessoas a contas e aplicações. AWS Organizations consolida gestão de contas; unidades organizacionais agrupam contas segundo políticas. Control Tower oferece estrutura para governança de ambientes, conforme capacidades e configuração.

### Laboratório de arquitetura

Modele contas de desenvolvimento, produção e segurança. Defina responsabilidades e processo de entrada de contas. Documente controles organizacionais como limites de governança, distintos de permissões concedidas.

### Entregáveis e critérios

Entregáveis: árvore de contas, matriz de responsáveis e procedimento de exceções. Critério: ambiente de produção tem governança e evidência de revisão independente.

## 5. VPC e segmentação

### Fundamentação técnica

Uma VPC modela limites de rede e sub-redes. Rotas definem caminhos; security groups controlam tráfego associado a interfaces; ACLs de rede fornecem controle em sub-redes. O desenho deve explicitar somente comunicações exigidas pela aplicação.

### Laboratório de arquitetura

Projete três camadas: entrada autorizada, aplicação e dados privados. Registre fluxos de negócio, justificativas e dependências; planeje registros de fluxo com retenção.

### Entregáveis e critérios

Entregáveis: diagrama lógico e matriz de comunicação. Critério: acesso a dados não é fornecido diretamente a visitantes. Não criar rede pública ou serviços reais.

## 6. EC2 e proteção de compute

### Fundamentação técnica

EC2 oferece instâncias cujo sistema convidado e software são administrados pelo cliente. Inventário, atualizações, identidades de workloads, configuração de referência e registro de mudanças são componentes do controle.

### Laboratório de arquitetura

Prepare baseline para uma instância fictícia de aplicação: sistema suportado, atualização, permissões, criptografia de armazenamento, registros e recuperação. Defina validação antes e depois de mudanças.

### Entregáveis e critérios

Entregáveis: checklist de baseline e plano de manutenção. Critério: cada controle tem responsável e evidência; mudanças têm janela e plano de retorno.

## 7. Proteção de armazenamento S3

### Fundamentação técnica

Amazon S3 armazena objetos. Proteção demanda classificação, controle de acesso, configurações de bloqueio público, criptografia e políticas de retenção. Versionamento auxilia recuperação de alterações, mas não substitui estratégia de backup.

### Laboratório de arquitetura

Revise o template private-storage.yaml do repositório. Identifique quatro propriedades de bloqueio público, criptografia padrão, versionamento e propriedade de objetos. Defina requisitos de acesso e recuperação de um documento sintético.

### Entregáveis e critérios

Entregáveis: template anotado e matriz de controles. Critério: os controles declarados são identificáveis; implantação e conformidade permanecem não verificadas.

## 8. KMS e Secrets Manager

### Fundamentação técnica

KMS auxilia gestão de chaves criptográficas; Secrets Manager auxilia armazenamento e administração de segredos. Dados, chaves e credenciais possuem ciclos de vida distintos. Políticas e registros devem limitar acesso e orientar recuperação.

### Laboratório de arquitetura

Modele uma aplicação fictícia com dados restritos e uma credencial de serviço. Registre quem utiliza, administra e audita chaves e segredos, como são substituídos e como recuperação é autorizada.

### Entregáveis e critérios

Entregáveis: classificação, matriz de acesso e plano de rotação aprovado. Não use segredos reais e não inclua credenciais em documentação.

## 9. CloudTrail e CloudWatch

### Fundamentação técnica

CloudTrail registra atividades relevantes conforme escopo de eventos; CloudWatch fornece métricas, logs e alarmes. A configuração deve considerar tipos de eventos, região, custos, retenção e proteção do acesso. Eventos administrativos e métricas de saúde têm funções diferentes.

### Laboratório de arquitetura

Use examples/audit-events.jsonl como conjunto artificial. Prepare uma cronologia de revisão de armazenamento, backup e acesso. Defina quais eventos precisam de acompanhamento e qual equipe deve recebê-los.

### Entregáveis e critérios

Entregáveis: relatório de triagem, plano de retenção e matriz de alertas. Critério: eventos sintéticos não são apresentados como dados coletados da AWS.

## 10. AWS Config e governança de configuração

### Fundamentação técnica

AWS Config registra e avalia configurações de recursos conforme escopo. Regras e evidências apoiam revisão de conformidade, mas um resultado isolado não prova segurança. Custos e cobertura precisam ser planejados.

### Laboratório de arquitetura

Defina controles de referência para armazenamento privado, criptografia, tags de dono e rastreabilidade. Prepare revisão manual de um modelo fictício e registre exceções.

### Entregáveis e critérios

Entregáveis: matriz de configuração, requisito e evidência. Critério: cada exceção tem prazo e proprietário. Não executar descoberta de ambientes externos.

## 11. GuardDuty, Security Hub e Inspector

### Fundamentação técnica

GuardDuty produz achados de segurança a partir das fontes suportadas; Security Hub agrega e organiza achados e controles conforme configuração; Inspector auxilia gestão de exposições e vulnerabilidades em recursos suportados. Os resultados precisam de contextualização e priorização.

### Laboratório de arquitetura

Prepare três achados fictícios: atualização pendente, revisão de configuração atrasada e backup sem evidência de recuperação. Classifique impacto operacional, responsável e prazo.

### Entregáveis e critérios

Entregáveis: quadro de triagem e evidência de fechamento proposta. Critério: o relatório distingue achado, confirmação, correção e validação. Não gerar ataques para produzir alertas.

## 12. Proteção de aplicações e WAF

### Fundamentação técnica

AWS WAF aplica regras de filtragem a recursos compatíveis. Controles de aplicação, autorização, validação, observabilidade e proteção de dados continuam necessários. Regras precisam ser monitoradas para evitar impactos indevidos em solicitações legítimas.

### Laboratório de arquitetura

Modele um portal que recebe formulários. Documente requisitos de disponibilidade, autenticação, autorização e volume esperado. Planeje revisão de métricas e aprovação de alterações de regras.

### Entregáveis e critérios

Entregáveis: matriz de controles por camada, responsáveis e critérios de disponibilidade. Não simular cargas ofensivas.

## 13. AWS Backup e continuidade

### Fundamentação técnica

Serviços de backup e versionamento podem contribuir para recuperação; a cobertura depende de serviço, configuração e escopo. Objetivos RPO e RTO orientam retenção, frequência e ensaio. Evidência de recuperação deve refletir teste realizado.

### Laboratório de arquitetura

Planeje recuperação de arquivos sintéticos, registrando dependências, versão esperada e verificação de integridade, sem criar recursos reais. Defina a equipe responsável por autorizar restauração.

### Entregáveis e critérios

Entregáveis: plano de recuperação e ficha de ensaio. Critério: estado de cada validação é explícito, sem inventar resultados.

## 14. CloudFormation e infraestrutura como código

### Fundamentação técnica

Modelos declarativos descrevem recursos e propriedades. Versionamento facilita revisão, comparação e rastreabilidade. Mudanças devem ser avaliadas por pares antes de executar; recursos persistentes precisam de gestão de custos e ciclo de vida.

### Laboratório de arquitetura

Analise o modelo YAML existente. Explique propriedades, entradas e saídas, dependências, retenção e condições de entrega. Produza checklist para revisão estática e planejamento de alterações.

### Entregáveis e critérios

Entregáveis: revisão anotada e lista de riscos residuais. Critério: o material não cria recursos automaticamente e não afirma que o modelo foi implantado.

## 15. Custos, orçamento e encerramento

### Fundamentação técnica

Serviços podem cobrar por armazenamento, solicitações, tráfego, processamento e registros. O custo depende de região e uso. Orçamentos e alertas ajudam a acompanhar consumo, mas não são garantia de limite rígido.

### Laboratório de arquitetura

Crie inventário dos recursos planejados, unidade de cobrança a pesquisar, responsável e política de retenção. Defina procedimento autorizado de encerramento e verificação de custos persistentes.

### Entregáveis e critérios

Entregáveis: planilha de planejamento com valores a confirmar na calculadora oficial, critérios de encerramento e revisão. Não declarar preços atuais sem consulta.

## 16. Resposta a incidentes e arquitetura integradora

### Fundamentação técnica

Segurança em nuvem combina governança, identidade, infraestrutura, dados, monitoramento e recuperação. O Well-Architected Security Pillar orienta revisão desses controles ao longo do ciclo de vida. Resposta requer responsáveis, contexto, evidências e recuperação autorizada.

### Laboratório de arquitetura

Integre contas, papéis, rede privada, armazenamento, auditoria e continuidade. Simule um atraso de backup em registros fictícios; registre impacto, decisões, critérios de recuperação e plano de melhoria.

### Entregáveis e critérios

Entregáveis: diagrama, matriz de riscos, evidências propostas, relatório de incidente e plano de 90 dias. Critério: cada controle tem dono e evidência verificável [2].

## Referências bibliográficas

- [1] AMAZON WEB SERVICES. The shared responsibility model for security. https://docs.aws.amazon.com/wellarchitected/latest/framework/sec-shared-responsibility.html
- [2] AMAZON WEB SERVICES. Security Pillar. https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/
- [3] AMAZON WEB SERVICES. IAM User Guide. https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html
- [4] AMAZON WEB SERVICES. Amazon S3 User Guide. https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html
- [5] AMAZON WEB SERVICES. CloudFormation User Guide. https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html
- [6] AMAZON WEB SERVICES. Documentation portal. https://docs.aws.amazon.com/
- [7] AMAZON WEB SERVICES. AWS Pricing Calculator. https://calculator.aws/