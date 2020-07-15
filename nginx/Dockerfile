FROM nginx:latest

# ユーザーを作成
ARG USER_UID=1000
RUN useradd -m -s /bin/bash -u ${USER_UID} docker

# php設定の置換
COPY conf.d/default.conf /etc/nginx/conf.d/default.conf
COPY nginx.conf /etc/nginx/nginx.conf

RUN chgrp -R root /var/cache/nginx /var/run /var/log/nginx && \
    chmod -R 770 /var/cache/nginx /var/run /var/log/nginx


CMD ["nginx", "-g", "daemon off;"]
