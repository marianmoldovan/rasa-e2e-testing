# rasa-e2e-testing

Crear un nuevo proyecto

docker run -v $(pwd):/app rasa/rasa:1.10.3-full init --no-prompt

hablar con el asistent
docker run -it -v $(pwd):/app rasa/rasa:1.10.3-full shell

training a model

docker run -v $(pwd):/app rasa/rasa:1.10.3-full train --domain domain.yml --data data --out models

docker run -it -v $(pwd):/app rasa/rasa:1.10.3-full test
