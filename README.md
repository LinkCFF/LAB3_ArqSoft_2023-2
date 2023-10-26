# LAB3_ArqSoft_2023-2

docker run --name db_client -d --link swarch2023ii_db:db -p 8081:80 phpmyadmin

Esta es la rama para el Laboratorio 3

localhost:5000/graphiql

# $${\scriptsize \color{red} \texttt{Alterar código ya que el host.docker.internal no funciona en CodeSpaces}}$$	


Para montar todo:
    en swarch2023ii_db:
        docker build -t swarch2023ii_db .
        docker run -d -t -i -p 3306:3306 --name swarch2023ii_db swarch2023ii_db
        docker run --name db_client -d --link swarch2023ii_db:db -p 8081:80 phpmyadmin
    se puede ver en : http://localhost:8081
    en swarch2023ii_ms:
        docker build -t swarch2023ii_ms .
        docker run -p 4000:4000 -e DB_HOST=X -e DB_PORT=3306 -e DB_USER=Y -e DB_PASSWORD=Z -e DB_NAME=swarch2023ii_db -e URL=0.0.0.0:4000 swarch2023ii_ms
        "aqui dos opciones para X":
            host.docker.internal (no sirve en codespaces)
            IP del contenedor (swarch2023ii_db)
        docker run -p 4000:4000 -e DB_HOST=172.17.0.2 -e DB_PORT=3306 -e DB_USER=swarch2023ii -e DB_PASSWORD=2023 -e DB_NAME=swarch2023ii_db -e URL=0.0.0.0:4000 swarch2023ii_ms
        Esto es el ejemplo de body:
            {
                "name": "Categoría Swarch",
                "description": "Categoría de ejemplo para la asignatura Arquitectura de Software 2023-II"
            }

        