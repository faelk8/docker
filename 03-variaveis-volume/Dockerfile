# Da imagem do node
FROM node:14

# Diretório de trabalho
WORKDIR /app-node

# Tempo de criação
ARG PORT_BUILD=6000

# Dentro do cotainer
ENV PORT=${PORT_BUILD}

# Definindo a porta
EXPOSE ${PORT_BUILD}

# Copie os arquivos da diretório atual
COPY . .

# Faça a instalação
RUN npm isntall

# Inicie a aplicação
ENTRYPOINT npm start