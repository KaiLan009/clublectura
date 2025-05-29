# Etapa 1: Construcción de la app con Vite
FROM node:18 as builder

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .
RUN npm run build

# Etapa 2: Servir con Nginx
FROM nginx:alpine

# Copia los archivos construidos a Nginx
COPY --from=builder /app/dist /usr/share/nginx/html

# Copia configuración de Nginx para manejar rutas SPA (React)
COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
