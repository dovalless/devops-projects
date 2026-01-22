# 🚀 Scalable Java Application on AWS Using Terraform

<div align="center">

**Enterprise-Grade Deployment Pipeline for Spring Boot Applications**

[![Terraform](https://img.shields.io/badge/Terraform-1.5%2B-7B42BC?style=for-the-badge&logo=terraform&logoColor=white)](https://www.terraform.io/)
[![AWS](https://img.shields.io/badge/AWS-Cloud-FF9900?style=for-the-badge&logo=amazonaws&logoColor=white)](https://aws.amazon.com/)
[![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.x-6DB33F?style=for-the-badge&logo=springboot&logoColor=white)](https://spring.io/projects/spring-boot)
[![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=for-the-badge&logo=jenkins&logoColor=white)](https://www.jenkins.io/)
[![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)](LICENSE)

[📋 Descripción](#-descripción-del-proyecto) • 
[🏗️ Arquitectura](#️-arquitectura) • 
[🛠️ Stack Tecnológico](#️-stack-tecnológico) • 
[⚙️ Instalación](#️-instalación-y-configuración) • 
[🚀 Despliegue](#️-flujo-de-despliegue) • 
[🔒 Seguridad](#️-consideraciones-de-seguridad) • 
[👨‍💻 Autor](#️-autor)

</div>

---

## 📋 Descripción del Proyecto

Este proyecto implementa una **plataforma de despliegue automatizada y escalable** para aplicaciones Java Spring Boot en AWS. Combina herramientas de infraestructura como código (Terraform), automatización de builds (Jenkins), gestión de configuración (Ansible) y empaquetado de imágenes (Packer) para crear un pipeline DevOps completo.

### 🎯 Objetivos Principales
- ✅ **Infraestructura como Código**: Gestionar toda la infraestructura AWS mediante Terraform
- ✅ **Despliegue Automatizado**: Pipeline CI/CD completo con Jenkins
- ✅ **Escalabilidad Automática**: Configuración de Auto Scaling Groups y Load Balancer
- ✅ **Alta Disponibilidad**: Arquitectura multi-AZ con RDS MySQL
- ✅ **Gestión Segura de Secretos**: Uso de AWS Secrets Manager para credenciales
- ✅ **Monitoreo Centralizado**: Logs de aplicación en CloudWatch

### 💼 Casos de Uso
- **Aplicaciones Web Empresariales**: Despliegue de aplicaciones Spring Boot en producción
- **Entornos de Desarrollo/Pruebas**: Provisionamiento automático de ambientes
- **Migración a la Nube**: Patrón para mover aplicaciones Java a AWS
- **Plataformas SaaS**: Arquitectura base para aplicaciones multi-tenant

---
## Scalable Java Application on AWS Using Terraform

![java-aws](https://user-images.githubusercontent.com/106984297/219648306-42c0d544-f6e6-423d-9802-9f3d5eca43e8.png)

## 🏗️ Arquitectura

### 📐 Diagrama de Arquitectura
```
┌─────────────────────────────────────────────────────────────┐
│                     Jenkins CI/CD Server                     │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐    │
│  │   Build  │  │   Test   │  │  Packer  │  │Terraform │    │
│  │  Java App│  │          │  │   AMI    │  │ Apply    │    │
│  └──────────┘  └──────────┘  └──────────┘  └──────────┘    │
└─────────────────────────┬────────────────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────────────┐
│                        AWS Cloud                            │
│                                                             │
│  ┌─────────────────┐      ┌────────────────────────────┐   │
│  │ Application     │      │    Auto Scaling Group      │   │
│  │ Load Balancer   │◄─────┤   ┌──────┐  ┌──────┐      │   │
│  │                 │      │   │ EC2  │  │ EC2  │      │   │
│  └─────────────────┘      │   │ AMI  │  │ AMI  │      │   │
│          │                │   └──────┘  └──────┘      │   │
│          │                └──────────────┬─────────────┘   │
│          ▼                               │                 │
│  ┌─────────────────┐                     ▼                 │
│  │   CloudWatch    │             ┌──────────────┐         │
│  │    Logs &       │             │   RDS MySQL  │         │
│  │   Monitoring    │             │   (Multi-AZ) │         │
│  └─────────────────┘             └──────────────┘         │
│          │                           │                     │
│          └───────────────────────────┘                     │
│                     AWS Secrets Manager                    │
└─────────────────────────────────────────────────────────────┘
```

### 🔄 Flujo de Trabajo del Pipeline
1. **Fase de Build**: Jenkins compila la aplicación Java Spring Boot
2. **Creación de AMI**: Packer + Ansible crean una AMI con la aplicación
3. **Provisionamiento**: Terraform despliega infraestructura en AWS
4. **Despliegue**: Auto Scaling Group lanza instancias con la AMI
5. **Configuración**: Ansible aplica configuración final
6. **Verificación**: Tests de integración y monitoreo

### 🌐 Componentes de Infraestructura
| Componente | Descripción | Tecnología |
|------------|-------------|------------|
| **Balanceador de Carga** | Distribuye tráfico a instancias EC2 | Application Load Balancer (L7) |
| **Cómputo Escalable** | Instancias de aplicación | Auto Scaling Group + EC2 |
| **Base de Datos** | Almacenamiento persistente | RDS MySQL (Multi-AZ) |
| **Gestión de Secretos** | Credenciales y configuraciones | AWS Secrets Manager |
| **Monitoreo** | Logs y métricas | Amazon CloudWatch |
| **Red** | Aislamiento y conectividad | VPC, Subnets, Security Groups |

---

## 🛠️ Stack Tecnológico

### 🔧 DevOps & Automatización
| Herramienta | Versión | Propósito | Documentación |
|-------------|---------|-----------|---------------|
| **Terraform** | ≥ 1.5 | Infraestructura como Código | [Terraform AWS Provider] |
| **Packer** | ≥ 1.9 | Creación de imágenes de máquina (AMI) | [HashiCorp Packer](https://www.packer.io/) |
| **Ansible** | ≥ 2.14 | Gestión de configuración y provisionamiento | [Red Hat Ansible](https://www.ansible.com/) |
| **Jenkins** | ≥ 2.4 | Automatización CI/CD | [Jenkins](https://www.jenkins.io/) |
| **Docker** | ≥ 24.0 | Contenerización (opcional) | [Docker](https://www.docker.com/) |

### ☁️ Servicios AWS
| Servicio | Tipo | Configuración Recomendada |
|----------|------|---------------------------|
| **EC2** | Cómputo | t3.medium (desarrollo), m5.large (producción) |
| **RDS MySQL** | Base de Datos | db.t3.medium, Multi-AZ, almacenamiento gp3 |
| **ALB** | Red | Application Load Balancer (HTTP/HTTPS) |
| **Secrets Manager** | Seguridad | Rotación automática cada 30 días |
| **CloudWatch** | Monitoreo | Log groups, métricas personalizadas |
| **Auto Scaling** | Escalabilidad | 2-10 instancias, políticas CPU-based |
| **VPC** | Red | 2 subnets públicas, 2 privadas por AZ |

### 📦 Aplicación Java
```yaml
Aplicación: Spring PetClinic (Demo)
Repositorio: https://github.com/spring-projects/spring-petclinic
Tecnologías:
  - Spring Boot 3.x
  - Spring Data JPA
  - Spring Security (opcional)
  - Thymeleaf
  - MySQL Driver
Perfil Activo: "mysql" (para RDS)
```

### 📁 Estructura del Proyecto
```
scalable-java-aws/
├── jenkins/                    # Configuración Jenkins
│   ├── Jenkinsfile            # Pipeline as Code
│   └── scripts/               # Scripts de build
├── packer/                    # Configuración Packer
│   ├── spring-petclinic.json  # Plantilla Packer
│   └── scripts/               # Scripts de provisionamiento
├── ansible/                   # Playbooks Ansible
│   ├── playbook.yml
│   ├── roles/
│   │   ├── java-app/
│   │   ├── cloudwatch-agent/
│   │   └── app-config/
│   └── inventories/
├── terraform/                 # Código Terraform
│   ├── modules/               # Módulos reutilizables
│   │   ├── vpc/
│   │   ├── rds/
│   │   ├── alb/
│   │   └── asg/
│   ├── environments/
│   │   ├── dev/
│   │   ├── staging/
│   │   └── prod/
│   ├── main.tf               # Configuración principal
│   ├── variables.tf          # Variables
│   ├── outputs.tf            # Outputs
│   └── terraform.tfvars      # Valores variables
├── application/              # Código fuente aplicación
│   └── spring-petclinic/
└── docs/                     # Documentación
```

---

## ⚙️ Instalación y Configuración

### ✅ Prerrequisitos

#### 1. Cuenta y Credenciales AWS
```bash
# Configurar AWS CLI
aws configure
# Ingresar:
# - AWS Access Key ID
# - AWS Secret Access Key
# - Región predeterminada (ej: us-east-1)
# - Formato de output (json)

# Verificar configuración
aws sts get-caller-identity
```

#### 2. Herramientas Locales
```bash
# Terraform
wget https://releases.hashicorp.com/terraform/1.5.0/terraform_1.5.0_linux_amd64.zip
unzip terraform_1.5.0_linux_amd64.zip
sudo mv terraform /usr/local/bin/

# Packer
wget https://releases.hashicorp.com/packer/1.9.0/packer_1.9.0_linux_amd64.zip
unzip packer_1.9.0_linux_amd64.zip
sudo mv packer /usr/local/bin/

# Ansible
sudo apt update
sudo apt install -y ansible

# Verificar instalaciones
terraform --version    # >= 1.5.0
packer --version       # >= 1.9.0
ansible --version      # >= 2.14.0
```

#### 3. Repositorio del Proyecto
```bash
# Clonar repositorio
git clone https://github.com/dovalless/scalable-java-aws.git
cd scalable-java-aws

# Clonar aplicación de ejemplo
git clone https://github.com/spring-projects/spring-petclinic.git application/
```

### 🔧 Configuración Inicial

#### 1. Configurar Variables de Entorno
```bash
# Crear archivo de configuración
cat > .env << EOF
AWS_REGION=us-east-1
AWS_PROFILE=default
APP_NAME=spring-petclinic
ENVIRONMENT=dev
DB_NAME=petclinic
VPC_CIDR=10.0.0.0/16
EOF

# Cargar variables
export $(cat .env | xargs)
```

#### 2. Configurar Backend de Terraform (S3)
```bash
# Crear bucket S3 para state file
aws s3api create-bucket \
  --bucket terraform-state-$(aws sts get-caller-identity --query Account --output text) \
  --region $AWS_REGION \
  --create-bucket-configuration LocationConstraint=$AWS_REGION

# Habilitar versioning
aws s3api put-bucket-versioning \
  --bucket terraform-state-$(aws sts get-caller-identity --query Account --output text) \
  --versioning-configuration Status=Enabled
```

#### 3. Configurar Jenkins (Opcional)
```bash
# Usar Docker para Jenkins
docker run -d \
  --name jenkins \
  -p 8080:8080 \
  -p 50000:50000 \
  -v jenkins_home:/var/jenkins_home \
  jenkins/jenkins:lts

# Obtener password inicial
docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword
```

### 🚀 Configuración Rápida con Script
```bash
#!/bin/bash
# setup.sh - Script de configuración automática

echo "🚀 Iniciando configuración del proyecto..."

# 1. Verificar herramientas
check_tool() {
    if ! command -v $1 &> /dev/null; then
        echo "❌ $1 no está instalado. Instalando..."
        $2
    else
        echo "✅ $1 está instalado"
    fi
}

check_tool "terraform" "install_terraform"
check_tool "packer" "install_packer"
check_tool "ansible" "sudo apt install -y ansible"

# 2. Configurar AWS
if [ ! -f ~/.aws/credentials ]; then
    echo "🔐 Configurando credenciales AWS..."
    aws configure
fi

# 3. Inicializar Terraform
echo "🏗️ Inicializando Terraform..."
cd terraform/environments/dev
terraform init -backend-config="backend.hcl"

echo "🎉 Configuración completada!"
```

---

## 🚀 Flujo de Despliegue

### 📦 Fase 1: Crear AMI con Packer y Ansible

#### 1.1 Configurar Plantilla Packer
```json
// packer/spring-petclinic.json
{
  "builders": [{
    "type": "amazon-ebs",
    "region": "{{user `aws_region`}}",
    "source_ami": "ami-0c55b159cbfafe1f0",
    "instance_type": "t2.micro",
    "ssh_username": "ec2-user",
    "ami_name": "spring-petclinic-{{timestamp}}",
    "tags": {
      "Name": "spring-petclinic",
      "Environment": "{{user `environment`}}"
    }
  }],
  "provisioners": [{
    "type": "ansible",
    "playbook_file": "../ansible/playbook.yml",
    "extra_arguments": [
      "--extra-vars", "app_version={{user `app_version`}}"
    ]
  }]
}
```

#### 1.2 Playbook Ansible para Configuración
```yaml
# ansible/playbook.yml
---
- hosts: all
  become: yes
  vars:
    app_user: springapp
    app_dir: /opt/spring-petclinic
    java_version: 11
    
  tasks:
    - name: Install Java
      apt:
        name: "openjdk-{{ java_version }}-jdk"
        state: present
        
    - name: Create application user
      user:
        name: "{{ app_user }}"
        system: yes
        create_home: yes
        
    - name: Create application directory
      file:
        path: "{{ app_dir }}"
        state: directory
        owner: "{{ app_user }}"
        mode: '0755'
        
    - name: Copy application JAR
      copy:
        src: "../application/target/spring-petclinic-{{ app_version }}.jar"
        dest: "{{ app_dir }}/spring-petclinic.jar"
        owner: "{{ app_user }}"
        
    - name: Install CloudWatch agent
      amazon.aws.cloudwatch_agent:
        state: present
        config_file: ../ansible/files/cloudwatch-config.json
        
    - name: Configure systemd service
      template:
        src: templates/spring-petclinic.service.j2
        dest: /etc/systemd/system/spring-petclinic.service
        
    - name: Enable and start service
      systemd:
        name: spring-petclinic
        enabled: yes
        state: started
        daemon_reload: yes
```

#### 1.3 Ejecutar Packer
```bash
cd packer

# Validar plantilla
packer validate spring-petclinic.json

# Construir AMI
packer build \
  -var 'aws_region=us-east-1' \
  -var 'environment=dev' \
  -var 'app_version=2.7.0' \
  spring-petclinic.json

# Output esperado
# ==> amazon-ebs: AMI: ami-0123456789abcdef0
```

### 🏗️ Fase 2: Provisionar Infraestructura con Terraform

#### 2.1 Configuración Principal Terraform
```hcl
# terraform/main.tf
terraform {
  required_version = ">= 1.5.0"
  
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 5.0"
    }
  }
  
  backend "s3" {
    bucket = "terraform-state-123456789012"
    key    = "spring-petclinic/terraform.tfstate"
    region = "us-east-1"
  }
}

provider "aws" {
  region = var.aws_region
}

# Módulo VPC
module "vpc" {
  source = "./modules/vpc"
  
  name                 = var.vpc_name
  cidr                 = var.vpc_cidr
  azs                  = var.availability_zones
  private_subnets      = var.private_subnet_cidrs
  public_subnets       = var.public_subnet_cidrs
  enable_nat_gateway   = true
  single_nat_gateway   = var.environment == "dev" ? true : false
}

# Módulo RDS
module "rds" {
  source = "./modules/rds"
  
  identifier     = "${var.app_name}-db-${var.environment}"
  engine         = "mysql"
  engine_version = "8.0"
  instance_class = var.db_instance_class
  allocated_storage = 20
  
  db_name  = var.db_name
  username = var.db_username
  
  vpc_security_group_ids = [module.vpc.db_security_group_id]
  subnet_ids             = module.vpc.database_subnets
  
  # Secretos en Secrets Manager
  manage_master_user_password = true
  master_user_secret_kms_key_id = aws_kms_key.secrets.arn
}

# Módulo Application Load Balancer
module "alb" {
  source = "./modules/alb"
  
  name               = "${var.app_name}-alb-${var.environment}"
  internal           = false
  load_balancer_type = "application"
  
  vpc_id          = module.vpc.vpc_id
  subnets         = module.vpc.public_subnets
  security_groups = [module.vpc.alb_security_group_id]
  
  target_groups = [
    {
      name             = "${var.app_name}-tg"
      backend_protocol = "HTTP"
      backend_port     = 8080
      target_type      = "instance"
    }
  ]
  
  http_tcp_listeners = [
    {
      port               = 80
      protocol           = "HTTP"
      target_group_index = 0
    }
  ]
}

# Módulo Auto Scaling Group
module "asg" {
  source = "./modules/asg"
  
  name                 = "${var.app_name}-asg-${var.environment}"
  vpc_zone_identifier  = module.vpc.private_subnets
  target_group_arns    = module.alb.target_group_arns
  
  # Launch Template
  launch_template_name = "${var.app_name}-lt-${var.environment}"
  ami_id               = var.ami_id  # AMI creada por Packer
  instance_type        = var.instance_type
  
  # Auto Scaling Policies
  min_size         = var.asg_min_size
  max_size         = var.asg_max_size
  desired_capacity = var.asg_desired_capacity
  
  # CloudWatch Alarms para escalado
  scaling_policies = {
    cpu-high = {
      policy_type = "TargetTrackingScaling"
      target_value = 70.0
      predefined_metric_type = "ASGAverageCPUUtilization"
    }
  }
}

# Secrets Manager para credenciales RDS
resource "aws_secretsmanager_secret" "rds_credentials" {
  name = "${var.app_name}-rds-credentials-${var.environment}"
  
  description = "Credenciales RDS para ${var.app_name}"
  kms_key_id  = aws_kms_key.secrets.arn
  
  recovery_window_in_days = 0  # Eliminación inmediata (solo desarrollo)
}

resource "aws_secretsmanager_secret_version" "rds_credentials" {
  secret_id = aws_secretsmanager_secret.rds_credentials.id
  
  secret_string = jsonencode({
    username = module.rds.db_instance_username
    password = module.rds.db_instance_password
    engine   = "mysql"
    host     = module.rds.db_instance_address
    port     = module.rds.db_instance_port
    dbname   = module.rds.db_instance_name
  })
}

# Configurar rotación automática de secretos
resource "aws_secretsmanager_secret_rotation" "rds_rotation" {
  secret_id           = aws_secretsmanager_secret.rds_credentials.id
  rotation_lambda_arn = aws_lambda_function.rotation.arn
  
  rotation_rules {
    automatically_after_days = 30  # Rotar cada 30 días
  }
}
```

#### 2.2 Variables de Configuración
```hcl
# terraform/variables.tf
variable "aws_region" {
  description = "Región AWS para despliegue"
  type        = string
  default     = "us-east-1"
}

variable "environment" {
  description = "Entorno de despliegue (dev, staging, prod)"
  type        = string
  default     = "dev"
  
  validation {
    condition     = contains(["dev", "staging", "prod"], var.environment)
    error_message = "Environment debe ser: dev, staging, o prod."
  }
}

variable "app_name" {
  description = "Nombre de la aplicación"
  type        = string
  default     = "spring-petclinic"
}

variable "vpc_cidr" {
  description = "CIDR block para VPC"
  type        = string
  default     = "10.0.0.0/16"
}

variable "db_instance_class" {
  description = "Clase de instancia RDS"
  type        = string
  default     = "db.t3.micro"
}

variable "ami_id" {
  description = "ID de la AMI creada por Packer"
  type        = string
}

variable "asg_min_size" {
  description = "Número mínimo de instancias en ASG"
  type        = number
  default     = 2
}

variable "asg_max_size" {
  description = "Número máximo de instancias en ASG"
  type        = number
  default     = 10
}

variable "asg_desired_capacity" {
  description = "Capacidad deseada en ASG"
  type        = number
  default     = 2
}
```

#### 2.3 Ejecutar Terraform
```bash
cd terraform/environments/dev

# Inicializar
terraform init

# Planificar
terraform plan -var="ami_id=ami-0123456789abcdef0"

# Aplicar
terraform apply -var="ami_id=ami-0123456789abcdef0" -auto-approve

# Verificar outputs
terraform output

# Outputs esperados:
# alb_dns_name = "spring-petclinic-alb-dev-1234567890.us-east-1.elb.amazonaws.com"
# rds_endpoint = "spring-petclinic-db-dev.abcdefghijkl.us-east-1.rds.amazonaws.com:3306"
```

### 🔄 Fase 3: Pipeline Jenkins CI/CD

#### 3.1 Jenkinsfile para Pipeline
```groovy
// jenkins/Jenkinsfile
pipeline {
    agent any
    
    environment {
        AWS_REGION = 'us-east-1'
        APP_NAME = 'spring-petclinic'
        ENVIRONMENT = 'dev'
        PACKER_AMI_VAR_FILE = 'packer/vars.json'
    }
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Build Java Application') {
            steps {
                dir('application') {
                    sh 'mvn clean package -DskipTests'
                }
            }
        }
        
        stage('Unit Tests') {
            steps {
                dir('application') {
                    sh 'mvn test'
                }
            }
            
            post {
                always {
                    junit 'application/target/surefire-reports/*.xml'
                }
            }
        }
        
        stage('Build AMI with Packer') {
            steps {
                script {
                    def amiId = sh(
                        script: """
                        cd packer
                        packer build -var-file=${PACKER_AMI_VAR_FILE} spring-petclinic.json | \
                        grep 'AMI:' | awk '{print \$2}'
                        """,
                        returnStdout: true
                    ).trim()
                    
                    env.AMI_ID = amiId
                    echo "AMI creada: ${amiId}"
                }
            }
        }
        
        stage('Deploy with Terraform') {
            steps {
                dir('terraform/environments/dev') {
                    sh """
                    terraform init -backend-config="backend.hcl"
                    terraform apply -var="ami_id=${env.AMI_ID}" -auto-approve
                    """
                }
            }
        }
        
        stage('Integration Tests') {
            steps {
                script {
                    def albDns = sh(
                        script: """
                        cd terraform/environments/dev
                        terraform output -raw alb_dns_name
                        """,
                        returnStdout: true
                    ).trim()
                    
                    sh """
                    curl -f http://${albDns}:8080/actuator/health
                    curl -f http://${albDns}:8080/
                    """
                }
            }
        }
    }
    
    post {
        success {
            echo 'Pipeline completado exitosamente!'
            slackSend(
                color: 'good',
                message: "✅ ${env.JOB_NAME} #${env.BUILD_NUMBER} desplegado exitosamente"
            )
        }
        failure {
            echo 'Pipeline falló!'
            slackSend(
                color: 'danger',
                message: "❌ ${env.JOB_NAME} #${env.BUILD_NUMBER} falló"
            )
        }
    }
}
```

### ✅ Fase 4: Verificación y Monitoreo

#### 4.1 Verificar Aplicación
```bash
# Obtener DNS del Load Balancer
ALB_DNS=$(cd terraform/environments/dev && terraform output -raw alb_dns_name)

# Verificar salud de la aplicación
curl -f "http://${ALB_DNS}:8080/actuator/health"
# Respuesta esperada: {"status":"UP"}

# Acceder a la aplicación
curl "http://${ALB_DNS}:8080/"
# Debe mostrar la página principal de Spring PetClinic

# Verificar conexión a base de datos
curl "http://${ALB_DNS}:8080/actuator/metrics"
# Buscar métricas relacionadas con conexiones JDBC
```

#### 4.2 Verificar Logs en CloudWatch
```bash
# Nombre del log group
LOG_GROUP="/aws/ec2/spring-petclinic"

# Ver logs recientes (AWS CLI)
aws logs filter-log-events \
  --log-group-name "$LOG_GROUP" \
  --start-time $(date -d '1 hour ago' +%s) \
  --filter-pattern "ERROR"

# Métricas CloudWatch personalizadas
aws cloudwatch get-metric-statistics \
  --namespace "SpringPetClinic" \
  --metric-name "ApplicationRequests" \
  --start-time $(date -d '1 hour ago' +%s) \
  --end-time $(date +%s) \
  --period 300 \
  --statistics "Sum" "Average" "Maximum"
```

#### 4.3 Probar Escalado Automático
```bash
# Generar carga para probar Auto Scaling
for i in {1..1000}; do
  curl -s "http://${ALB_DNS}:8080/" > /dev/null &
done

# Monitorear escalado
aws autoscaling describe-auto-scaling-groups \
  --auto-scaling-group-names "spring-petclinic-asg-dev" \
  --query "AutoScalingGroups[0].Instances" \
  --output table

# Ver métricas de CPU
aws cloudwatch get-metric-statistics \
  --namespace "AWS/EC2" \
  --metric-name "CPUUtilization" \
  --dimensions Name=AutoScalingGroupName,Value=spring-petclinic-asg-dev \
  --start-time $(date -d '5 minutes ago' +%s) \
  --end-time $(date +%s) \
  --period 60 \
  --statistics "Average"
```

---

## 🔒 Consideraciones de Seguridad

### 🔐 Gestión de Secretos con AWS Secrets Manager
```hcl
# terraform/security.tf
resource "aws_kms_key" "secrets" {
  description             = "KMS key para encriptar secrets"
  deletion_window_in_days = 7
  enable_key_rotation     = true
  
  tags = {
    Name        = "${var.app_name}-secrets-key"
    Environment = var.environment
  }
}

resource "aws_secretsmanager_secret_policy" "rds_policy" {
  secret_arn = aws_secretsmanager_secret.rds_credentials.arn
  
  policy = jsonencode({
    Version = "2012-10-17"
    Statement = [
      {
        Effect = "Allow"
        Principal = {
          AWS = "arn:aws:iam::${data.aws_caller_identity.current.account_id}:role/ec2-instance-role"
        }
        Action = [
          "secretsmanager:GetSecretValue",
          "secretsmanager:DescribeSecret"
        ]
        Resource = "*"
        Condition = {
          StringEquals = {
            "secretsmanager:ResourceTag/Environment" = var.environment
          }
        }
      }
    ]
  })
}

# Rotación automática de secretos
resource "aws_lambda_function" "rotation" {
  filename      = "lambda/rotation.zip"
  function_name = "${var.app_name}-rotation-${var.environment}"
  role          = aws_iam_role.rotation_lambda.arn
  handler       = "index.handler"
  runtime       = "python3.9"
  
  vpc_config {
    subnet_ids         = module.vpc.private_subnets
    security_group_ids = [module.vpc.lambda_security_group_id]
  }
  
  environment {
    variables = {
      SECRETS_MANAGER_ENDPOINT = "https://secretsmanager.${var.aws_region}.amazonaws.com"
    }
  }
}
```

### 🛡️ Configuración de Seguridad por Capas
| Capa | Configuración | Buenas Prácticas |
|------|---------------|------------------|
| **Red (VPC)** | Subnets públicas/privadas, NAT Gateway, VPC Endpoints | Aislar capas de aplicación en subnets separadas |
| **Security Groups** | Reglas de entrada/salida mínimas necesarias | Principio de mínimo privilegio |
| **IAM Roles** | Políticas específicas para EC2, Lambda, RDS | No usar credenciales root |
| **Encriptación** | KMS para secrets, EBS encryption, SSL/TLS | Encriptación en tránsito y reposo |
| **Monitoreo** | CloudWatch Logs, AWS Config, GuardDuty | Detección de anomalías |

### 🔄 Rotación de Credenciales
```hcl
# terraform/secrets-rotation.tf
resource "aws_secretsmanager_secret_rotation" "rds" {
  secret_id = aws_secretsmanager_secret.rds_credentials.id
  
  rotation_lambda_arn = aws_lambda_function.rotation.arn
  
  rotation_rules {
    automatically_after_days = 30  # Rotación automática cada 30 días
    
    # Configuración para rotación de RDS
    duration = "2h"    # Ventana de mantenimiento
    schedule_expression = "cron(0 2 ? * SAT *)"  # Sábados a las 2 AM
  }
}

# Troubleshooting de rotación
resource "aws_cloudwatch_log_group" "rotation_logs" {
  name              = "/aws/lambda/${aws_lambda_function.rotation.function_name}"
  retention_in_days = 30
  
  tags = {
    Environment = var.environment
    Application = var.app_name
  }
}
```

### 🚨 Solución de Problemas Comunes

#### Problema: Rotación de Secrets Fallida
```bash
# Verificar logs de CloudWatch
aws logs filter-log-events \
  --log-group-name "/aws/lambda/${aws_lambda_function.rotation.function_name}" \
  --filter-pattern "ERROR" \
  --start-time $(date -d '24 hours ago' +%s)

# Comprobar estado de rotación
aws secretsmanager describe-secret \
  --secret-id "${aws_secretsmanager_secret.rds_credentials.id}"

# Forzar rotación manual
aws secretsmanager rotate-secret \
  --secret-id "${aws_secretsmanager_secret.rds_credentials.id}" \
  --rotation-lambda-arn "${aws_lambda_function.rotation.arn}"
```

#### Problema: Conexión a RDS Fallida
```bash
# Verificar configuración de red
aws ec2 describe-security-groups \
  --group-ids $(aws rds describe-db-instances \
    --db-instance-identifier "spring-petclinic-db-dev" \
    --query "DBInstances[0].VpcSecurityGroups[0].VpcSecurityGroupId" \
    --output text)

# Probar conectividad
aws rds describe-db-instances \
  --db-instance-identifier "spring-petclinic-db-dev" \
  --query "DBInstances[0].Endpoint.Address"

# Obtectar credenciales actuales
aws secretsmanager get-secret-value \
  --secret-id "${aws_secretsmanager_secret.rds_credentials.id}" \
  --version-stage "AWSCURRENT" \
  --query "SecretString" \
  --output text | jq .
```

---

## 📊 Monitoreo y Mantenimiento

### 📈 Dashboards de CloudWatch
```json
{
  "widgets": [
    {
      "type": "metric",
      "properties": {
        "metrics": [
          ["AWS/ApplicationELB", "RequestCount", { "stat": "Sum", "label": "Requests" }],
          ["AWS/ApplicationELB", "TargetResponseTime", { "stat": "Average", "label": "Avg Response Time" }]
        ],
        "period": 300,
        "stat": "Average",
        "region": "us-east-1",
        "title": "Load Balancer Metrics"
      }
    },
    {
      "type": "metric",
      "properties": {
        "metrics": [
          ["AWS/EC2", "CPUUtilization", "AutoScalingGroupName", "spring-petclinic-asg-dev"],
          [".", "NetworkIn", ".", "."],
          [".", "NetworkOut", ".", "."]
        ],
        "view": "timeSeries",
        "stacked": false,
        "region": "us-east-1",
        "title": "EC2 Instance Metrics"
      }
    },
    {
      "type": "log",
      "properties": {
        "query": "SOURCE '/aws/ec2/spring-petclinic' | filter @message like /ERROR/",
        "region": "us-east-1",
        "title": "Application Error Logs",
        "view": "table"
      }
    }
  ]
}
```

### 🔔 Alarmas y Notificaciones
```hcl
# terraform/monitoring.tf
resource "aws_cloudwatch_metric_alarm" "high_cpu" {
  alarm_name          = "${var.app_name}-high-cpu-${var.environment}"
  comparison_operator = "GreaterThanThreshold"
  evaluation_periods  = 2
  metric_name        = "CPUUtilization"
  namespace          = "AWS/EC2"
  period             = 300
  statistic          = "Average"
  threshold          = 80
  alarm_description  = "CPU utilization above 80%"
  alarm_actions      = [aws_sns_topic.alerts.arn]
  
  dimensions = {
    AutoScalingGroupName = module.asg.autoscaling_group_name
  }
}

resource "aws_cloudwatch_metric_alarm" "application_errors" {
  alarm_name          = "${var.app_name}-application-errors-${var.environment}"
  comparison_operator = "GreaterThanThreshold"
  evaluation_periods  = 1
  metric_name        = "ErrorCount"
  namespace          = "SpringPetClinic"
  period             = 300
  statistic          = "Sum"
  threshold          = 10
  alarm_description  = "More than 10 application errors in 5 minutes"
  alarm_actions      = [aws_sns_topic.alerts.arn]
}

resource "aws_sns_topic" "alerts" {
  name = "${var.app_name}-alerts-${var.environment}"
  
  tags = {
    Environment = var.environment
    Application = var.app_name
  }
}

resource "aws_sns_topic_subscription" "email" {
  topic_arn = aws_sns_topic.alerts.arn
  protocol  = "email"
  endpoint  = var.alert_email
}
```

### 🧹 Limpieza y Mantenimiento
```bash
#!/bin/bash
# cleanup.sh - Script para limpieza de recursos

echo "🧹 Limpiando recursos..."

# 1. Destruir infraestructura Terraform
cd terraform/environments/dev
terraform destroy -auto-approve

# 2. Eliminar AMIs antiguas
aws ec2 describe-images \
  --owners self \
  --filters "Name=name,Values=spring-petclinic-*" \
  --query "Images[?CreationDate<='$(date -d '7 days ago' +%Y-%m-%d)'].ImageId" \
  --output text | xargs -I {} aws ec2 deregister-image --image-id {}

# 3. Limpiar Snapshots de EBS
aws ec2 describe-snapshots \
  --owner-ids self \
  --filters "Name=description,Values=*spring-petclinic*" \
  --query "Snapshots[?StartTime<='$(date -d '7 days ago' +%Y-%m-%d)'].SnapshotId" \
  --output text | xargs -I {} aws ec2 delete-snapshot --snapshot-id {}

# 4. Limpiar CloudWatch Log Groups
aws logs describe-log-groups \
  --log-group-name-prefix "/aws/" \
  --query "logGroups[?contains(logGroupName,'spring-petclinic')].logGroupName" \
  --output text | xargs -I {} aws logs delete-log-group --log-group-name {}

echo "✅ Limpieza completada!"
```

---

## 👨‍💻 Autor

<div align="center">

**Darwin Manuel Ovalles Cesar**

<p align="center">
<a href="https://www.linkedin.com/in/darwin-manuel-ovalles-cesar-dev" target="_blank">
<img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/linked-in-alt.svg" alt="LinkedIn - Darwin Ovalles" height="40" width="50" />
</a>
<a href="https://github.com/dovalless" target="_blank">
<img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/github.svg" alt="GitHub - Darwin Ovalles" height="40" width="50" />
</a>
</p>

💼 **LinkedIn**: [darwin-manuel-ovalles-cesar-dev](https://www.linkedin.com/in/darwin-manuel-ovalles-cesar-dev/)  
🌐 **GitHub**: [@dovalless](https://github.com/dovalless)  
📧 **Contacto**: Disponible a través de LinkedIn  
🎓 **Certificaciones**: AWS Solutions Architect, Terraform Associate, Jenkins Engineer  

*"Este proyecto representa la convergencia de desarrollo de aplicaciones modernas y operaciones de infraestructura en la nube. Demuestra cómo las prácticas DevOps y la infraestructura como código pueden crear sistemas escalables, resilientes y mantenibles."*

**#AWS #Terraform #DevOps #SpringBoot #Java #InfrastructureAsCode #CloudComputing**

</div>

---

## 📄 Licencia

Este proyecto está bajo la Licencia MIT. Consulta el archivo [LICENSE](LICENSE) para más detalles.

```
MIT License
Copyright (c) 2024 Darwin Manuel Ovalles Cesar

Permiso concedido, libre de cargo, a cualquier persona que obtenga una copia
de este software y los archivos de documentación asociados (el "Software"), 
para tratar en el Software sin restricción, incluyendo sin limitación los derechos
de usar, copiar, modificar, fusionar, publicar, distribuir, sublicenciar y/o vender
copias del Software, y permitir a las personas a quienes se les proporcione el Software
hacer lo mismo, sujeto a las siguientes condiciones:

El aviso de copyright anterior y este aviso de permiso se incluirán en todas
las copias o partes sustanciales del Software.
```

---

## 🙏 Agradecimientos

- **HashiCorp** - Por Terraform y Packer
- **Amazon Web Services** - Por la infraestructura en la nube
- **Spring Team** - Por el framework Spring Boot
- **Comunidad DevOps** - Por compartir conocimiento y mejores prácticas

<div align="center">

### ⭐ Si este proyecto te resulta útil, considera darle una estrella en GitHub ⭐

### 🚀 ¡Próximo paso: Implementar Blue/Green Deployments con AWS CodeDeploy! 🚀

**Desarrollado con 💙 y ☕ por Darwin Ovalles**

---
*Proyecto de Infraestructura como Código - DevOps Pipeline*  
*Última actualización: Enero 2024 | Terraform 1.5 | AWS Provider 5.0 | Spring Boot 3.1*

</div>
```
