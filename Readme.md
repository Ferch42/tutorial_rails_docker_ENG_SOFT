# Instruções para criar a imagem do docker do ambiente de desenvolvimento

## Primeiro passo 
Instale o docker, git e docker-compose em seu computador

Links: 
https://www.docker.com/get-started

https://git-scm.com/

## Segundo passo 
Abra o terminal e clone o respostório em alguma pasta local

````
git clone https://github.com/Ferch42/tutorial_rails_docker_ENG_SOFT.git
````

## Terceiro passo 
Entre no repositorio clonado e crie o esqueleto do projeto rails

````
docker-compose run web rails new . --force --no-deps 
````

## Quarto passo 
Adicione as seguintes gemas no arquivo Gemfile (não o Gemfile.lock)

````
docker-compose build
````

Construa a imagem do container docker

````
docker-compose build
````

## Quinto passo 
Inicie a execução do container

````
docker-compose up
````
## Observação
Para executar comandos específicos dentro do container, execute o seguinte comando: 

````
docker-compose exec web comando
````

Por exemplo:

````
docker-compose exec web rake routes
````
