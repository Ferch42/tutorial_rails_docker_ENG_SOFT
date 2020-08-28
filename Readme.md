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
Adicione as seguintes gemas no arquivo Gemfile (não o Gemfile.lock), dentro do grupo :development, :test

````
group :development, :test do
  ...
  gem 'rspec-rails', '~> 4.0.1'
  gem 'jasmine'
  gem 'coveralls', require: false  
  gem 'cucumber-rails', require: false
  # database_cleaner is not mandatory, but highly recommended
  gem 'database_cleaner'
  ...
end
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

## Sexto passo 
Execute os comandos (em outro terminal, ou seja, não feche o terminal que está rodando o programa do docker)

````
docker-compose exec web rails generate rspec:install
docker-compose exec web rails generate cucumber:install
````

## Sétimo passo 
Para validar se tudo foi executado corretamente, teste os seguintes comandos:

````
docker-compose exec web rake spec
docker-compose exec web rake cucumber
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

## POSSÍVEIS ERROS 
É possível que o git mude as quebras de linha de Linux para Windows, o que ocasionará um erro ao seguir o tutorial. Neste caso, certifique-se de que TODOS os arquivos utilizados utilizem a terminação de linha LF em vez de CRLF.

# Para dúvidas

Por favor, em caso de dúvidas postar no fórum online do e-disciplinas
