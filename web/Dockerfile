FROM node:18 AS base
CMD [ "bash" ]

FROM base AS build
COPY . /workspace
ARG REACT_APP_API_SERVER
WORKDIR /workspace
RUN npm ci && npm run build

FROM nginx:latest AS production
COPY --from=build /workspace/build /var/www
COPY nginx.conf /etc/nginx/conf.d/default.conf