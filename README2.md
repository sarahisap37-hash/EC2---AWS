#  Implantação de Aplicação Java (Tomcat) no AWS Elastic Beanstalk

Este guia prático descreve as etapas para configurar, implantar e monitorar uma aplicação Java utilizando o **AWS Elastic Beanstalk**, um serviço de PaaS (Plataforma como Serviço) que facilita o gerenciamento de infraestrutura.

---


## 🛠️ Passo a Passo

### 1. Acesso ao Ambiente
1. No **Console AWS**, pesquise e selecione **Elastic Beanstalk**.
2. Na tabela de **Ambientes**, localize sua aplicação e verifique se a coluna *Integridade* exibe o status **Ok**.
3. Clique no nome do ambiente para acessar o **Painel de Controle**.
4. Clique na **URL do domínio** (ex: `meu-app.elasticbeanstalk.com`).
   > **Nota:** Inicialmente, um erro `404 Not Found` será exibido. Isso é normal, pois o servidor está ativo, mas sem código hospedado.

### 2. Upload e Implantação
1. **Obter o código:** Baixe o arquivo de amostra [tomcat.zip](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/samples/tomcat.zip).
2. **Upload:** No painel do Elastic Beanstalk, clique no botão **Fazer upload e implantar**.
3. **Execução:** Selecione o arquivo `tomcat.zip` do seu computador e clique em **Implantar**.
4. **Validação:** Aguarde de 1 a 2 minutos. Quando o status retornar para "Ok", atualize a URL do domínio para ver a aplicação em funcionamento.

### 3. Configuração e Monitoramento
* **Infraestrutura:** No menu lateral, acesse **Configuração**. Aqui você pode gerenciar instâncias EC2, grupos de segurança e regras de escalabilidade.
* **Persistência:** Em **Redes, bancos de dados e etiquetas**, é possível anexar um banco de dados RDS ao ambiente.
* **Saúde do Sistema:** Na aba **Monitoramento**, visualize gráficos em tempo real sobre latência, tráfego e uso de CPU.

---

##  Recursos Provisionados
Ao concluir este guia, a AWS terá criado automaticamente:
* **Instâncias EC2:** Servidores onde o Tomcat está rodando.
* **Elastic Load Balancer:** Para distribuir o tráfego de rede.
* **Auto Scaling Group:** Para ajustar o número de instâncias entre 2 e 6 conforme a carga.
* **Security Group:** Com a porta 80 aberta para acesso público.

---
