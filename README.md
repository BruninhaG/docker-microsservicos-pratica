# 🐳 Docker: Microsserviços em Ação

Este projeto é um **Desafio Prático** que demonstra a implementação de uma arquitetura baseada em **Microsserviços** utilizando **Containers Docker**.  
O objetivo principal é ilustrar, na prática, como o Docker abstrai ambientes, garante portabilidade e otimiza a entrega de software em cenários reais de produção.

---

## 🎯 Objetivo do Projeto

- **Entendimento de Containers:** Aplicar o Docker para isolar ambientes e dependências de forma eficiente.  
- **Microsserviços:** Construir uma arquitetura composta por múltiplas aplicações independentes e integradas.  
- **Orquestração Local e em Cluster:** Utilizar **Docker Compose** e **Docker Swarm** para gerenciar serviços em diferentes contextos.  
- **Boas Práticas:** Seguir diretrizes de mercado para criação de imagens, comunicação entre serviços e persistência de dados.

---

## ⚙️ Arquitetura e Tecnologias

A solução é composta por múltiplos **microsserviços** que se comunicam para executar uma funcionalidade completa, com **proxy reverso**, **banco de dados persistente** e **cluster Docker Swarm**.

### 🧩 Stack de Tecnologia

| Camada | Tecnologia | Descrição |
| :------ | :---------- | :---------- |
| **Containerização** | Docker | Criação e execução de containers isolados |
| **Orquestração** | Docker Compose / Docker Swarm | Definição, orquestração e distribuição de serviços |
| **Banco de Dados** | MySQL | Banco relacional conteinerizado e persistente |
| **Proxy Reverso** | Nginx | Gerenciamento de rotas entre os microsserviços |
| **Sistema Operacional Base** | Linux | Base utilizada nas imagens |
| **Volumes** | Docker Volumes | Persistência e replicação de dados entre containers |

---

## 🏗️ Estrutura de Microsserviços

| Serviço | Descrição | Imagem Base | Porta (Local) |
| :--- | :--- | :--- | :--- |
| **nginx-proxy** | Proxy reverso responsável pelo roteamento das requisições | nginx:alpine | 80 |
| **app-service** | Serviço principal da aplicação (ex: API) | node:18-alpine | 8080 |
| **db-mysql** | Banco de dados MySQL com persistência em volume | mysql:8.0 | 3306 |

> 💡 Os serviços foram configurados com volumes dedicados, permitindo replicação e persistência mesmo após a remoção dos containers.

---

## ⚡ Recursos Implementados

### 🐝 Cluster Swarm
O projeto não se limita ao Docker Compose — foi criado e testado um **Cluster Docker Swarm**, que permite:
- Distribuir microsserviços entre múltiplos nós;
- Gerenciar réplicas automaticamente;
- Escalar serviços com o comando `docker service scale`.

### 🐬 MySQL Conteinerizado
Uma instância do **MySQL** foi configurada e conteinerizada para persistência dos dados da aplicação.  
Os dados são armazenados através de **volumes nomeados**, garantindo que nada seja perdido em reinicializações ou rebuilds.

### 🌐 Nginx Proxy Reverso
O **Nginx** atua como **proxy reverso**, redirecionando o tráfego para os serviços corretos e mantendo o isolamento entre as aplicações.

### 💾 Volumes e Persistência
Os **volumes Docker** foram utilizados para gerenciar a persistência e replicação de dados, garantindo integridade entre containers e nós no cluster.

---

## 🚀 Pré-requisitos e Execução

Para rodar este projeto, você precisará ter o **Docker** instalado e configurado em sua máquina.

### 📦 Pré-requisitos

- **Docker Engine:** Versão recente.  
- **Docker Compose:** Necessário para subir a arquitetura localmente.  
- **Docker Swarm:** Para execução e testes em cluster.  
- Conhecimentos básicos de **Linux** e **CLI**.

---

### ▶️ Passos para Inicializar

1. **Clonar o Repositório**
   ```bash
   git clone https://github.com/seu-usuario/nome-do-seu-repositorio.git
   cd nome-do-seu-repositorio

2. **Construir e Iniciar os Containers**
   O arquivo docker-compose.yml está configurado para construir as imagens e iniciar todos os serviços:
     ```bash
     docker-compose up --build -d

3. **Verificar o Status**
   ```bash
   docker ps

4. **Acessar a Aplicação*8
Acesse o serviço principal em:
👉 http://localhost:8080

---
### 🌀 Executar no Docker Swarm (Modo Cluster): 

1. **Inicializar o Swarm**
    ```bash
    docker swarm init

2. **Implantar o Stack**
     ```bash
     docker stack deploy -c docker-compose.yml microservices-stack

3. **Verificar os Serviços**
   ```bash
   docker service ls

4. **Remover o Stack**
   ```bash
   docker stack rm microservices-stack

---

### 🧹 Limpeza (Shutdown)

Para remover containers, volumes e redes criados pelo Compose:

---
### 📚 Conceitos Envolvidos
- Isolamento de ambiente com containers.
- Orquestração com Compose e Swarm.
- Persistência e replicação de dados com volumes
- Comunicação entre microsserviços.
- Proxy reverso com Ngix.
- Banco de dados conteinerizado (MySQL)
---
### 💡 Conclusão

Este projeto consolida conceitos essenciais de DevOps e Arquitetura de Microsserviços, utilizando o ecossistema Docker para criar uma solução moderna, escalável e pronta para ambientes de produção.

---

## 👩‍💻 Autora
Feito com 💛 por Bruna Guimarães

---
## 🌟 Apoie o projeto
Se você gostou, não esqueça de deixar uma ⭐ no repositório!
Isso ajuda muito o projeto a crescer e me incentiva a continuar criando. 🙌
