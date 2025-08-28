# RELATORIO DE IMPLEMENTACAO DE SERVICOS AWS

Data: 20 de Agosto de 2025
Empresa: Abstrego Industries
Reponsavel: Pedro Henrique Vital Guimarães

## Introdução
Este relatório apresenta o processo de implementação de serviços de otimização de custos na nuvem AWS para a empresa Abstrego Industries, realizado por Pedro Henrique Vital Guimarães. O objetivo do projeto foi elencar e implementar 3 serviços ou funcionalidades da AWS com a finalidade de realizar uma diminuição de custos imediatos e fornecer maior visibilidade sobre os gastos operacionais em nuvem.

## Descrição do Projeto
O projeto de implementação de ferramentas foi dividido em 3 etapas, cada uma com seus objetivos específicos. A seguir, serão descritas as etapas do projeto:

Etapa 1:
- Nome da ferramenta: AWS Cost Explorer
- Foco da ferramenta: Análise e Visibilidade de Custos.
- Descrição de caso de uso: Antes da implementação, a empresa tinha uma visão geral da fatura mensal da AWS, mas sem detalhes sobre quais serviços ou projetos eram os maiores responsáveis pelos custos. Através da ativação e configuração do AWS Cost Explorer, passamos a visualizar graficamente os gastos diários e mensais, filtrando por serviço (EC2, S3, RDS, etc.), por região e por tags de alocação de custo. Identificamos que 40% dos nossos custos estavam concentrados em instâncias EC2 de desenvolvimento que ficavam ligadas 24/7, mesmo fora do horário de expediente. Esta análise foi crucial para justificar e planejar as próximas etapas de otimização.

Etapa 2:
- Nome da ferramenta: AWS Instance Scheduler
- Foco da ferramenta: Automação para Ligar/Desligar Recursos (EC2 e RDS).
- Descrição de caso de uso: Com base nos dados do Cost Explorer, foi implementada a solução "AWS Instance Scheduler". Configuramos tags específicas (ex: Schedule=office-hours) nas instâncias de desenvolvimento e homologação. Em seguida, configuramos um agendamento para que todas as instâncias com essa tag sejam automaticamente desligadas às 19h e ligadas novamente às 8h durante a semana, permanecendo desligadas nos fins de semana. Essa ação simples tem uma projeção de economia de até 65% nos custos dessas instâncias específicas, gerando um impacto financeiro imediato e significativo sem afetar a produtividade da equipe.

Etapa 3:
- Nome da ferramenta: Políticas de Ciclo de Vida do Amazon S3 (S3 Lifecycle Policies)
- Foco da ferramenta: Otimização de Custos de Armazenamento de Dados.
- Descrição de caso de uso: A análise de custos também revelou um gasto considerável com o armazenamento de logs e backups antigos no Amazon S3, todos na classe de armazenamento padrão (Standard), que é a mais cara. Foi criada uma política de ciclo de vida aplicada aos buckets de logs e backups. A nova regra move automaticamente os objetos para classes de armazenamento mais baratas conforme eles envelhecem:
    - Após 30 dias, os dados são movidos para S3 Standard-Infrequent Access.
    - Após 90 dias, são movidos para S3 Glacier Instant Retrieval.
    - Após 365 dias, são movidos para S3 Glacier Deep Archive para arquivamento de longo prazo. Essa automação reduzirá os custos de armazenamento de dados mais antigos em até 90%, mantendo a conformidade e a capacidade de recuperação quando necessário.

## Conclusão
A implementação dessas três frentes na Abstrego Industries tem como esperado não apenas uma redução de custos imediata e recorrente, mas também a criação de uma cultura de governança e visibilidade financeira sobre os recursos em nuvem. A automação implementada garantirá que as economias sejam consistentes, enquanto o Cost Explorer nos capacitará a identificar novas oportunidades de otimização continuamente. Recomenda-se a continuidade da utilização e monitoramento dessas ferramentas, bem como a análise futura de outras estratégias, como a adoção de AWS Savings Plans para cargas de trabalho previsíveis.

## Anexos

- Relatório de custos exportado do AWS Cost Explorer (antes e depois).
- Documentação da configuração do AWS Instance Scheduler.
- Print da configuração da Política de Ciclo de Vida do S3.
- Planilha com projeção detalhada da economia mensal.

Assinatura do Responsavel pelo Projeto:

Pedro Henrique Vital Guimarães