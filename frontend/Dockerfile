FROM node:18-alpine

WORKDIR /app

COPY package*.json ./
# Use legacy-peer-deps to bypass version conflicts
RUN npm install --legacy-peer-deps

COPY . .

EXPOSE 5173

CMD ["npm", "run", "dev", "--", "--host"]