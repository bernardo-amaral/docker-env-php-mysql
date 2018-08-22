Docker comandos úteis:
---

No Windows prefira utilizar o Powershell com privilégios de Administrador (Tecla windows + X).

deverá subir o container, o parâmetro -d rodará em modo daemon (deve rodar sem necessidade do terminal aberto, e o terminal ficará livre)

	docker-compose up -d 

Deverá parar a execução de um container

	docker stop CONTAINER_NAME
	
	Exemplo: docker stop eproc-php

Deve remover os containers da lista de containers do Docker

	docker rm CONTAINER_NAME

	Exemplo: docker rm eproc-php

Montará todos os containers

	docker-compose build


Se necessitar acessar o terminal, -i é o parâmetro para interativo e -t para rodar no terminal, no OSX ou Linux use /bin/bash invés de bash:

	docker exec -it CONTAINER_NAME bash

	Exemplo: docker exec -it eproc-php bash


Se necessitar visualizar os logs, -f é o parãmetro para seguir (similar ao -t do tail)
	
	docker logs -f CONTAINER_NAME
