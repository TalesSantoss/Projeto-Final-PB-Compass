# Projeto-Final-PB-Compass
## Integrantes:
Tales Santos de Souza

Kevin Alencar Costa
# Objetivo
Criar diagramas que representem uma migração "lift-and-shift" de uma arquitetura "On-Premise" para a cloud AWS e realizar a modernização da mesma utilizando Kubernetes:
# Situação Atual:
"Nós somos da empresa "Fast Engineering S/A" e gostaríamos de uma solução dos senhores(as), que fazem parte da empresa terceira "TI SOLUÇÕES INCRÍVEIS".
Nosso eCommerce está crescendo e a solução atual não está atendendo mais a alta demanda de acessos e compras que estamos tendo.
Atualmente usamos:
* Banco de Dados MySQL: 500 GB, 10 GB RAM, 3 Core CPU.
* Servidor de Aplicação (React): 5 GB, 2 GB RAM, 1 Core CPU.
* Backend com 3 APIs e NGINX: 5 GB, 4 GB RAM, 2 Core CPU.
![image](https://github.com/user-attachments/assets/b6dd2030-d478-467f-96e3-9d6c277638a3)
Queremos modernizar esse sistema para a AWS, precisamos seguir as melhores práticas arquitetura em Cloud AWS, a nova arquitetura deve seguir as seguintes diretrizes:
* Ambiente Kubernetes;
* Banco de dados gerenciado (Paas e Multi AZ);
* Backup de dados;
* Sistema para persistência de objetos (imagens, vídeos etc.);
* Segurança;
Porém antes da migração acontecer para a nova estrutura, precisamos fazer uma migração "lift-and-shift" ou "as-is", o mais rápido possível, só depois que iremos promover a modificação para a nova estrutura em Kubernetes"
#Desenvolvimento
## Primeira Etapa(Lift-and-Shift):
Para realizar a migração, realizaremos os seguintes passos;
1. Criar uma VPC na AWS com uma subrede pública e com duas subredes privadas;
2. Criar um Banco RDS na subrede privada;
3. Utilizar o AWS DMS(Databse Migration Service) para migrar o banco de dados Mysql para um banco de dados RDS;
4. Usar AWS MGN(Application Migration Service) para fazer a migração dos servidores da aplicação para instâncias EC2 de mesma capacidade e com EBS(Elastic Block Storage)por meio de replication agents;
5. Utilizar o route 53 para disponibilizar um endereço DNS atrelado ao frontend;
6. Utilizar o IAM para gerenciar permissões;
7. Utilizar o cloudwatch para verificar a integridade da arquitetura;
8. Utilizar o AWS Secrets Manager para Armazenar dados sensíveis;
* Qual o diagrama da infraestrutura na AWS?
![image](https://github.com/user-attachments/assets/8e0867d7-7a6a-4dcc-814a-80a75c043356)
<p align="center">Diagrama da Primeira Etapa</p>

* Qual o custo da infraestrutura na AWS (AWS Calculator)?
1. Amazon RDS: 167,01 USD(Primeiras 12 horas para passar os dados), 658,12 USD(Mês inteiro)
2. EC2(FrontEnd) com EBS: 0,37 USD(Primeiras 12 horas), 21,29 USD(Mês inteiro)
3. EC2(Backend) com EBS: 0,49 USD(Primeiras 12 horas), 29,03 USD(Mês inteiro)
4. MGN:0,00 USD
5. DMS:120,70 USD
6. Route 53: 75,50 USD
7. Custo da migração(12 horas):364,07 USD (https://calculator.aws/#/estimate?id=5fa05984894895b8833e9c443f3858cf8a381a96)

![image](https://github.com/user-attachments/assets/aca50526-6734-47e0-8e50-265979385779)
<p align="center">Custo da migração(12 horas)</p>
9. Custo do mês inteiro:904,64 USD (https://calculator.aws/#/estimate?id=e83b7c8eabd281482647bea31d7d4c1203ff75be)

![image](https://github.com/user-attachments/assets/7bc7c499-00e8-40d2-a37a-b76fa691a6cb) 
<p align="center">Custo do mês inteiro</p>

## Segunda Etapa(Modernização/Kubernetes:
* Quais atividades são necessárias para a modernização?
1. Utilizar Git e GitLab para atomatizar o processo de desenvolvimento para o time de devs;
2. Utilizar o CloudFormation para criar um cluster EKS(Elastic Kubernetes Service) por meio de código com pods para cada instância EC2 com imagens dockers puxadas do  ECR(Elastic Container Registry);
3. Utilizar grupos de auto scaling para  criar novos pods de backend baseados em métricas do cloudwatch;
4. Utilizar Load Balancer para acessar a zona com melhor disponibilidade;
5. Utilizar Cloudfront para disponibilizar estáticos globalmente;
6. Utilizar AWS WAF para proteger a arquitetura de acessos suspeitos;
* Qual o diagrama da infraestrutura na AWS?
* ![image](https://github.com/user-attachments/assets/f4476b4e-dcf1-4820-bb99-015cb2639f75)
  <p align="center">Diagrama da Segunda Etapa</p>
  

* Qual o custo da infraestrutura na AWS (AWS Calculator)?
1. Amazon EKS:73,00 USD
2. AWS CloudFormation:26,10 USD
3. AWS Clodfront:44,22 USD
4. Amazon Elastic Container Registry: 3,00 USD
5. RDS:1974,36 USD
6. Elastic Load Balancer:133,23 USD
7. Route 53:75,50 USD
8. AWS WAF:300,00 USD
9. Custo total:2629,41 USD
![image](https://github.com/user-attachments/assets/03ae6ed2-57f9-48aa-9a22-604c0e8faee6)
<p align="center">Custo total</p>

