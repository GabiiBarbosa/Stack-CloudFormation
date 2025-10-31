# AWS CloudFormation — Stack

Este laboratório tem como objetivo **implementar sua primeira Stack utilizando o AWS CloudFormation**, automatizando a criação de uma instância **Amazon EC2** configurada como **servidor web Apache**.

O CloudFormation permite que você defina e provisione recursos da AWS de forma automatizada, através de templates escritos em **YAML** ou **JSON**.

---

## Recursos Criados

O template utilizado neste laboratório cria os seguintes recursos:

1. **Instância EC2**
   - Região: `us-east-1a`
   - Tipo: `t2.micro` (elegível para o Free Tier)
   - AMI: `ami-0ed9277fb7eb570c9`
   - Tag: `Name = Webserver`
   - Script de inicialização (`UserData`) que instala e inicia o servidor Apache automaticamente.

2. **Grupo de Segurança (Security Group)**
   - Nome lógico: `GrupoSeguranca`
   - Descrição: “Acesso Liberado Porta 80”
   - Permite tráfego de entrada (Inbound) na porta **80/TCP** de qualquer origem (`0.0.0.0/0`).

---

## Passos para Execução

1. **Acesse o Console AWS**
   - Vá para [https://console.aws.amazon.com/](https://console.aws.amazon.com/)

2. **Abra o serviço CloudFormation**
   - Pesquise por “CloudFormation” no console.

3. **Crie uma nova Stack**
   - Clique em **Create stack** → **With new resources (standard)**.
   - Escolha **Upload a template file** e envie o arquivo `.yaml`.

4. **Configure a Stack**
   - Dê um nome à Stack, por exemplo: `StackWebserver`.
   - Clique em **Next** até a etapa final e confirme.

5. **Acompanhe a criação**
   - Espere até o status ficar como `CREATE_COMPLETE`.

6. **Teste o servidor web**
   - No console EC2, copie o **IP público** da instância.
   - Acesse pelo navegador:  
     ```
     http://<ip-publico>
     ```
   - Você verá a mensagem:
     ```
     OLA AWS FOUNDATIONS do <hostname>
     ```

---

## Resultados Esperados

Após a execução bem-sucedida:
- Uma instância EC2 rodando Apache estará disponível.
- O Security Group permitirá o acesso HTTP pela porta 80.
- A página web padrão exibirá o nome do host da instância.

---

## Limpeza de Recursos

Para evitar custos:
1. No console CloudFormation, selecione sua Stack.
2. Clique em **Delete**.
3. Aguarde a exclusão completa dos recursos.

---

## 👩‍💻 Autor(a)
**Gabrielle Barbosa**  
Trabalho prático — Fundamentos AWS / CloudFormation
