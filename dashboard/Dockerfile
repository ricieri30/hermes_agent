FROM node:20-alpine

WORKDIR /app

# Copia o package.json e instala dependências
COPY package.json ./
RUN npm install

# Copia o restante do código
COPY . .

# Expõe a porta 3000
EXPOSE 3000

# Inicia o servidor
CMD ["npm", "start"]
