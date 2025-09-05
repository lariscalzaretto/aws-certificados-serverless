# 📜 Arquitetura Serverless para Emissão de Certificados na AWS

Este projeto foi desenvolvido como parte do **Bootcamp Santander Code Girls 2025** para demonstrar uma arquitetura **serverless** na **AWS**.  
O objetivo é criar um fluxo que automatiza a emissão de certificados a partir de uma lista de alunos, utilizando diversos serviços integrados.

---

## 🎯 **Objetivo**
O sistema permite que o usuário envie uma lista de alunos em **JSON** ou **CSV**, e a aplicação gera automaticamente os certificados em **PDF**, disponibilizando links temporários para download.

---

## 🏗 **Arquitetura da Solução**
<img width="2708" height="2500" alt="image" src="https://github.com/user-attachments/assets/429aef06-bd04-4459-b61c-fce724af83fe" />


> **Fluxo geral:**
1. **Cliente / Operadora** → Envia um arquivo JSON/CSV com os dados dos alunos.
2. **Amazon Cognito** → Faz a autenticação e gera o token de acesso.
3. **Amazon API Gateway** → Recebe a requisição e envia para a Lambda inicial.
4. **AWS Lambda (start-job)** → Valida os dados, fatia a lista e envia para a fila.
5. **Amazon SQS** → Garante o processamento assíncrono dos certificados.
6. **AWS Lambda (render-worker)** → Gera os certificados PDF usando os templates.
7. **Amazon S3** → Armazena os templates e os certificados emitidos.
8. **Amazon DynamoDB** → Registra o status de cada certificado.
9. **Amazon CloudWatch** → Monitora logs e métricas do processo.
10. **Entrega** → Links temporários (**pre-signed URLs**) para download dos certificados.

---

## 🛠 **Serviços AWS Utilizados**
- **Amazon Cognito** → Autenticação e autorização.
- **Amazon API Gateway** → Exposição da API REST.
- **AWS Lambda** → Funções serverless para processamento.
- **Amazon SQS** → Fila para processamento em lote.
- **Amazon S3** → Armazenamento dos templates e PDFs.
- **Amazon DynamoDB** → Registro de status dos certificados.
- **Amazon CloudWatch** → Logs e monitoramento.

---

## 📄 **Sobre o Diagrama**
O diagrama foi criado para ilustrar como os serviços da AWS se conectam de forma **segura**, **escalável** e **automatizada**.  
Ele representa o fluxo completo, desde o envio da lista de alunos até a emissão e disponibilização dos certificados.

---

## ✍️ **Autora**
**Larissa Guilhermina Scalzaretto**  
🔗 [LinkedIn](https://www.linkedin.com/in/larissa-guilhermina)

