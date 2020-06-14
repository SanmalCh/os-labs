FROM debian
ADD debian.list /etc/apt/sources.list.d/
RUN apt-get update && apt-get -y upgrade && apt -y install nginx && apt-get clean && \
    cd /var/www/ && rm -rf ./* && \
    mkdir -p sanmalchaizat.com/img && \
    chmod -R 754 /var/www/sanmalchaizat.com/ && \
    useradd sanmal && groupadd chaizat && usermod -aG chaizat sanmal && \
    chown -R sanmal:chaizat /var/www/sanmalchaizat.com/ && \
    sed -i 's/\/var\/www\/html/\/var\/www\/sanmalchaizat.com/g' /etc/nginx/sites-enabled/default && \
    sed -i 's/user www-data/user sanmal/g' /etc/nginx/nginx.conf
ADD index.html /var/www/sanmalchaizat.com/
ADD img.jpg /var/www/sanmalchaizat.com/img/
CMD ["nginx", "-g", "daemon off;"]
