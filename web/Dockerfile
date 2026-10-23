FROM nginx:alpine
# Astra bindings (acc5cb9): the platform injects ASTRA_PATH_API as a build arg
# for the image build; nginx materializes it at container start via the
# entrypoint so the static page reads window.API_BASE.
ARG ASTRA_PATH_API=""
COPY index.html /usr/share/nginx/html/index.html
RUN mkdir -p /docker-entrypoint.d && printf '#!/bin/sh\necho "window.API_BASE = \\"${ASTRA_PATH_API}\\";" > /usr/share/nginx/html/config.js\n' > /docker-entrypoint.d/40-api-base.sh && chmod +x /docker-entrypoint.d/40-api-base.sh
ENV ASTRA_PATH_API=${ASTRA_PATH_API}
EXPOSE 80
