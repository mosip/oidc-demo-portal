FROM node:16.13.2-alpine as build

ARG SOURCE
ARG COMMIT_HASH
ARG COMMIT_ID
ARG BUILD_TIME
LABEL source=${SOURCE}
LABEL commit_hash=${COMMIT_HASH}
LABEL commit_id=${COMMIT_ID}
LABEL build_time=${BUILD_TIME}

# can be passed during Docker build as build time environment for github branch to pickup configuration from.
ARG container_user=mosip

# can be passed during Docker build as build time environment for github branch to pickup configuration from.
ARG container_user_group=mosip

# can be passed during Docker build as build time environment for github branch to pickup configuration from.
ARG container_user_uid=1001

# can be passed during Docker build as build time environment for github branch to pickup configuration from.
ARG container_user_gid=1001

ARG idp_api_url
ARG idp_aud_url
ARG private_key

ENV work_dir=/app

WORKDIR ${work_dir}

RUN addgroup -g ${container_user_gid} ${container_user} && \
    adduser ${container_user} -G ${container_user} -u ${container_user_uid} --disabled-password

#Copy the app
COPY . ./
ENV PORT=8888
ENV IDP_BASE_URL=${idp_api_url}
ENV IDP_AUD_URL=${idp_aud_url}
ENV PRIVATE_KEY=${private_key}

# change permissions of file inside working dir
RUN chown -R ${container_user}:${container_user} ${work_dir}

# select container user for all tasks
USER ${container_user}

EXPOSE ${PORT}

RUN npm install
CMD ["node", "./app.js"]