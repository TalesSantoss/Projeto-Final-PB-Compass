# Projeto-Final-PB-Compass
# Situação Atual:
* Banco de Dados MySQL: 500 GB, 10 GB RAM, 3 Core CPU.
* Servidor de Aplicação (React): 5 GB, 2 GB RAM, 1 Core CPU.
* Backend com 3 APIs e NGINX: 5 GB, 4 GB RAM, 2 Core CPU.
![image](https://github.com/user-attachments/assets/b6dd2030-d478-467f-96e3-9d6c277638a3)

# Objetivos:
* Ambiente Kubernetes;
* Banco de dados gerenciado (Paas e Multi AZ);
* Backup de dados;
* Sistema para persistência de objetos (imagens, vídeos etc.);
* Segurança;

# Perguntas a serem respondidas na apresentação

## Primeira Etapa(As-is):
* Quais atividades são necessárias para a migração?
1. Criar uma conta IAM com as permissões necessárias
2. Criar uma VPC com subredes e grupos de seguranças adequados na região us-east-1(Norte da Vírginia)
3. Criar um banco de dados RDS MySQL com a mesma capacidade ou superior do original(db.m5.xlarge)
4. Criar um backup local de cada servidor on-premise
5. Utilizar o DMS para analizar o banco de dados e fazer a migração para o RDS
6. Instalar replication agents nos servidores de frontend e backend e com o MGN replica-los em instâncias de mesma capacidade nas subredes adequadas(t2.small e t4g.medium respectivamente)
7. Criar medidas de monitoramento nas Instãncias EC2 e RDS
   
* Quais as ferramentas vão ser utilizadas?
1. Virtual Private Cloud(VPC)
2. Database Migration Service(DMS);
3. Relational Database Service(RDS)
4. Application Migration Service
5. Elastic Cloud Compute(EC2);
6. Elastic Block Storage
7. AWS Identity and Acess Manager (IAM)
8. Amazon CloudWatch
9. AWS Secrets Manager

* Qual o diagrama da infraestrutura na AWS?
![image](https://github.com/user-attachments/assets/61db4954-9e2a-4f6e-ac58-befddd0d4636)

* Como serão garantidos os requisitos de Segurança?
1. Colocar os servidores de RDS e EC2 em sub-redes e grupos de segurança adequados
2. Utilizar o Secrets Manager para armazenar dados sensíveis
3. Utilizar o CLoudWatch para verificar o funcionamento da estrutura

* Como será realizado o processo de Backup?
1. Com o uso de um backup local antes da migração
2. O uso de backups automáticos no banco de dados
3. O uso de snapshots para instâncias EC2

* Qual o custo da infraestrutura na AWS (AWS Calculator)?
1. Amazon RDS: 167,01 USD(Primeiras 12 horas para passar os dados), 658,12 USD(Mês inteiro)
2. EC2(FrontEnd) com EBS: 0,37 USD(Primeiras 12 horas), 21,29 USD(Mês inteiro)
3. EC2(Backend) com EBS: 0,49 USD(Primeiras 12 horas), 29,03 USD(Mês inteiro)
4. MGN:0,00 USD
5. DMS:120,70 USD
6. Custo da migração(12 horas):288,57 USD (https://calculator.aws/#/estimate?id=99d48df01f751281a647ef2138aa55af1095592a)
7. Custo do mês inteiro:829,14 USD (https://calculator.aws/#/estimate?id=eaf0b4890ec3fd82d8b75f98e26a6fe9cf51f86c)
## Segunda Etapa(Modernização/Kubernetes:
* Quais atividades são necessárias para a migração?
* Quais as ferramentas vão ser utilizadas?
* Qual o diagrama da infraestrutura na AWS?
* Como serão garantidos os requisitos de Segurança?
* Como será realizado o processo de Backup?
* Qual o custo da infraestrutura na AWS (AWS Calculator)?
