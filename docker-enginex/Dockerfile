# baixa a última versão
# FROM nginx:latest

# # set o diretório
# WORKDIR /app

# # faz as instações necessárias
# RUN apt-get update && \
#     apt-get install vim -y

# # copia a pasta html para o caminho
# COPY html/ /usr/share/nginx/html

# comando para construção 
# docker build -t rafael/nginx-vim:latest .    
# docker run --rm -d -p 8080:80 rafael/nginx-vim
    
# baixa a última versão
FROM nginx:latest

COPY html /usr/share/nginx/html

ENTRYPOINT [ "/docker-entrypoint.sh" ]
CMD [ "nginx" ,"-g", "daemon off;" ]

# comando para construção 
# docker build -t rafael/nginx-vim . 
# docker run --rm -d -p 8080:80 rafael/nginx-vim