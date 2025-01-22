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
1. Criar uma VPC para conter a arquitetura na cloud
2. Criar um banco de dados RDS Mysql que supra a demanda e que faça backups automáticos
3. Migrar o Banco de dados on-premise para a cloud usando DMS para o banco RDS
4. Utilizar um Bucket S3 para guardar estáticos dos servidor de backend
5. Utilizar Amazon CloudFront para disponibilizar a aplicação web para usuários com baixa latência

* Quais as ferramentas vão ser utilizadas?
1. Virtual Private Cloud(VPC)
2. Database Migration Service(DMS);
3. Relational Database Service(RDS)
4. Simple Storage Service(S3);
5. Elastic Cloud Compute(EC2);
6. mysqldump v6.5.4;
7. Amazon CloudFront;
8. Elastic Load Balancer(ELB);
9. Application Migration Service

* Qual o diagrama da infraestrutura na AWS?

* Como serão garantidos os requisitos de Segurança?
1. Colocar os servidores de RDS e EC2 em sub-redes e grupos de segurança adequados

* Como será realizado o processo de Backup?
1. Com o uso do mysqldump para reproduzir o conteudo do banco de dados original
2. No RDS ativar a opção de utilizar backups automáticos

* Qual o custo da infraestrutura na AWS (AWS Calculator)?

## Segunda Etapa(Modernização/Kubernetes:
* Quais atividades são necessárias para a migração?
* Quais as ferramentas vão ser utilizadas?
* Qual o diagrama da infraestrutura na AWS?
* Como serão garantidos os requisitos de Segurança?
* Como será realizado o processo de Backup?
* Qual o custo da infraestrutura na AWS (AWS Calculator)?
