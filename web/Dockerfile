FROM nginx:alpine
# Astra bindings (acc5cb9): ASTRA_PATH_API addresses the backend; the nginx
# entrypoint materializes it as window.API_BASE for the static page.
ARG ASTRA_PATH_API=""
COPY index.html /usr/share/nginx/html/index.html
COPY nginx.conf /etc/nginx/conf.d/default.conf
RUN mkdir -p /docker-entrypoint.d && printf '#!/bin/sh\necho "window.API_BASE = \\"${ASTRA_PATH_API}\\";" > /usr/share/nginx/html/config.js\n' > /docker-entrypoint.d/40-api-base.sh && chmod +x /docker-entrypoint.d/40-api-base.sh
ENV ASTRA_PATH_API=${ASTRA_PATH_API}
EXPOSE 80
