# aws-secure-ec2-setup
Experiência de lab, levantando e configurando uma estrutura EC2, permitindo o acesso pela porta 20 (SSH)

# Provisionamento de Instância EC2 Segura em VPC Customizada na AWS

Este projeto documenta a criação e configuração de uma infraestrutura básica na nuvem AWS, aplicando boas práticas de isolamento de rede e controle de acesso para um servidor Linux.

## Arquitetura da Solução

O ambiente foi estruturado na região **us-east-1 (Norte da Virgínia)** seguindo a seguinte hierarquia de recursos:

* **Amazon VPC:** Rede virtual privada isolada para hospedar os recursos do projeto.
* **Sub-rede Pública (Public Subnet):** Segmento de rede configurado com rota para a internet.
* **Internet Gateway (IGW):** Componente anexado à borda da VPC para permitir a comunicação entre a instância e a internet.
* **Security Group (Grupo de Segurança):** Firewall virtual atuando no nível da instância, configurado com regras restritivas para permitir apenas tráfego legítimo.
* **Amazon EC2 (`t2.micro`):** Máquina virtual executando **Amazon Linux 2023**, dimensionada dentro do nível gratuito (Free Tier).

## Fluxo de Acesso e Segurança

1. O administrador inicia uma conexão remota via protocolo **SSH (Porta 22)** utilizando um par de chaves criptográficas (`.pem`).
2. O tráfego entra na rede através do **Internet Gateway (IGW)** e é direcionado para a **Sub-rede Pública**.
3. O **Security Group** valida a origem da requisição (IP autorizado) antes de liberar o acesso ao sistema operacional **Amazon Linux 2023**.

## Habilidades e Conceitos Aplicados

* Criação e segmentação de redes virtuais na nuvem (VPC e Subnets).
* Roteamento de tráfego externo via Internet Gateway.
* Configuração de regras de entrada e saída em Security Groups (princípio do menor privilégio).
* Provisionamento e administração básica de servidores Linux via terminal/SSH.

## Próximos Passos (Evolução do Projeto)

* [ ] Adicionar uma sub-rede privada para isolar um banco de dados (Amazon RDS).
* [ ] Automatizar o provisionamento dessa infraestrutura utilizando Terraform ou AWS CloudFormation.
* [ ] Configurar monitoramento básico de métricas com Amazon CloudWatch.
