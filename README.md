#  Laboratório AWS EC2 – Guia Completo

Este README documenta o passo a passo realizado no laboratório de Amazon EC2, incluindo criação, monitoramento, acesso, redimensionamento e exploração de limites de uma instância.

---

##  Tarefa 1: Iniciar a instância do Amazon EC2

1. Acesse o console da AWS:

   * Serviços → Computação → EC2
   * Região: **Norte da Virgínia (us-east-1)**

2. Clique em **Executar instância**

### Configurações:

* **Nome:** Web Server
* **AMI:** Amazon Linux 2023
* **Tipo:** t2.micro
* **Par de chaves:** vockey

### Rede:

* VPC: Lab VPC
* Sub-rede: PublicSubnet1
* Criar grupo de segurança:

  * Nome: Web Server security group
  * Remover regra padrão de entrada

### Armazenamento:

* Manter padrão (8 GiB)

### Avançado:

* Ativar **proteção contra encerramento**

### Script (Dados do usuário):

```bash
#!/bin/bash
dnf install -y httpd
systemctl enable httpd
systemctl start httpd
echo '<html><h1>Hello From Your Web Server!</h1></html>' > /var/www/html/index.html
```

3. Clique em **Executar instância**
4. Aguarde até:

   * Estado: *Em execução*
   * Status: *2/2 verificações aprovadas*

---

##  Tarefa 2: Monitorar a instância

* Aba **Verificações de status** → checar integridade
* Aba **Monitoramento** → métricas (CloudWatch)
* Ações:

  * Obter log do sistema
  * Obter captura de tela da instância

---

##  Tarefa 3: Acessar o servidor web

1. Copiar o **IPv4 público**
2. Abrir no navegador → inicialmente não funciona 

### Correção:

* Ir em **Grupos de segurança**
* Editar regras de entrada:

  * Tipo: HTTP
  * Origem: Anywhere-IPv4

3. Atualizar página → ✅
   Mensagem exibida:


---

##  Tarefa 4: Redimensionar a instância

### Parar a instância:

* Estado da instância → Interromper

### Alterações:

* Tipo: **t2.micro → t2.small**
* Ativar proteção contra interrupção

### Volume:

* De **8 GiB → 10 GiB**

### Reiniciar:

* Iniciar instância novamente

---

##  Tarefa 5: Explorar limites do EC2

1. Acessar **Service Quotas**
2. Buscar por EC2
3. Ver limites como:

   * Running On-Demand instances

 Observação: é possível solicitar aumento de limites.

---

##  Tarefa 6: Testar proteção contra interrupção

1. Tentar parar a instância → erro 
2. Desativar proteção:

   * Ações → Configurações → Proteção contra interrupção
3. Salvar e tentar novamente → sucesso ✅

---
