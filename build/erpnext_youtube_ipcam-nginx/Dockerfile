FROM node:14-buster-slim

COPY build/erpnext_youtube_ipcam-nginx/install_app.sh /install_app

RUN /install_app erpnext_youtube_ipcam https://github.com/dlivio/erpnext_youtube_ipcam

FROM frappe/erpnext-nginx:edge

COPY --from=0 /home/frappe/frappe-bench/sites/ /var/www/html/
COPY --from=0 /rsync /rsync
RUN echo -n "erpnext_youtube_ipcam" >> /var/www/html/apps.txt

VOLUME [ "/assets" ]

ENTRYPOINT ["/docker-entrypoint.sh"]
CMD ["nginx", "-g", "daemon off;"]
