# Construindo a imagem docker
docker build -t eduardocortez3/conversao-temperatura:v1 .
docker build -t eduardocortez3/conversao-temperatura:latest .

# Executando a imagem localmente
docker container run -d -p 8080:8080 eduardocortez3/conversao-temperatura:v1

# Subindo a imagem para o registry Docker
docker login
docker push eduardocortez3/conversao-temperatura:v1
docker push eduardocortez3/conversao-temperatura:latest
