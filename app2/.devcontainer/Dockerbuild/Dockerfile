FROM node:18.15.0-bullseye


RUN set -ex \
&& apt-get update -y \
&& apt-get upgrade -y \
&& npm install -g @quasar/cli \
# Clean up the lists work
&& rm -rf /var/lib/apt/lists/*