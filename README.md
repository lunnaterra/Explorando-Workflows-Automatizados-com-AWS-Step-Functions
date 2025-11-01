# AWS Step Functions - Projeto de Automação

## Descrição do Projeto
Este projeto tem como objetivo consolidar o aprendizado em **AWS Step Functions**, criando workflows automatizados que integram múltiplos serviços da AWS.  
O workflow simula um processo de **processamento de dados** com funções Lambda, utilizando decisões, paralelismo e armazenamento em S3.

**Serviços AWS utilizados:**
- AWS Step Functions
- AWS Lambda
- Amazon S3
- AWS CloudWatch (logs e monitoramento)

---

---

## Passo a Passo do Workflow

1. **Evento Inicial:**  
   Upload de arquivo no bucket S3 ou acionamento manual via console/CLI.
   
2. **Execução das Tarefas (Lambda):**  
   - Função Lambda 1: Validação de dados  
   - Função Lambda 2: Transformação ou enriquecimento dos dados  
   - Função Lambda 3: Armazenamento ou envio para destino final

3. **Condições e Decisões:**  
   - Estados de **Choice** para verificar erros ou valores específicos  
   - Estados de **Wait** para aguardar processamento externo

4. **Finalização:**  
   - Armazenamento do resultado em outro bucket S3  
   - Notificação via CloudWatch ou SNS (opcional)

---

## Arquivos Principais

- `step_function_definitions/workflow.json`  
  Contém a definição da Step Function em **JSON**, incluindo estados, transições e integração com Lambda.

- `scripts/lambda_*.py`  
  Scripts das funções Lambda executadas no workflow. Cada função é modular e tem logs para rastreabilidade.

---

## Insights e Aprendizados

- Aprendi a criar workflows **modulares e reutilizáveis** usando Step Functions e Lambda.
- Experimentei estados de **Choice** e **Parallel**, entendendo como controlar fluxos complexos.
- Observação: Sempre configurar **timeout e tratamento de erros** nas funções Lambda para evitar falhas na execução.
- Boas práticas aplicadas:
  - Separação de funções Lambda por responsabilidade
  - Logs detalhados no CloudWatch
  - Uso de S3 como armazenamento intermediário e persistência de dados

---

## Como Executar/Testar

### Pré-requisitos
- Conta AWS com permissões para Lambda, S3 e Step Functions
- AWS CLI configurado (`aws configure`)
- Node.js ou Python instalado, caso utilize Lambda localmente

### Passo a Passo
1. Criar buckets S3 para input e output.
2. Implantar funções Lambda utilizando console ou AWS CLI.
3. Criar Step Function importando o arquivo JSON `workflow.json`.
4. Executar o workflow manualmente ou configurar trigger de S3.
5. Monitorar logs no CloudWatch para verificar execução.


---

## Conclusão

Este projeto consolidou o aprendizado em **automatização de workflows na AWS**, integrando Step Functions, Lambda e S3.  
O repositório serve como referência prática para implementação de processos automatizados e documentação técnica em ambientes de nuvem.

---


