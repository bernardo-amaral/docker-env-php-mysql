Docker comandos �teis:
---

No Windows prefira utilizar o Powershell com privil�gios de Administrador (Tecla windows + X).

dever� subir o container, o par�metro -d rodar� em modo daemon (deve rodar sem necessidade do terminal aberto, e o terminal ficar� livre)

	docker-compose up -d 

Dever� parar a execu��o de um container

	docker stop CONTAINER_NAME
	
	Exemplo: docker stop docker-php

Deve remover os containers da lista de containers do Docker

	docker rm CONTAINER_NAME

	Exemplo: docker rm docker-php

Montar� todos os containers

	docker-compose build


Se necessitar acessar o terminal, -i � o par�metro para interativo e -t para rodar no terminal, no OSX ou Linux use /bin/bash inv�s de bash:

	docker exec -it CONTAINER_NAME bash

	Exemplo: docker exec -it docker-php bash


Se necessitar visualizar os logs, -f � o par�metro para seguir (similar ao -t do tail)
	
	docker logs -f CONTAINER_NAME
