# Etapa 1: Construir la aplicación Angular
FROM node:latest AS build

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .
RUN npm run build --prod

# Etapa 2: Configurar Nginx y servir la aplicación
FROM nginx:latest

COPY --from=build /app/dist/prueba /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
