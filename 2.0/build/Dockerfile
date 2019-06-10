FROM ubuntu:18.04

RUN apt-get update \
  && apt-get install --no-install-recommends -y curl locales sudo lsb-release software-properties-common \
  && add-apt-repository universe -y \
  && apt-get update

RUN localedef -i en_US -f UTF-8 en_US.UTF-8
RUN groupadd -r -g 2000 zulip; useradd -r -u 2000 -g 2000 -m -c "app account" -d /home/zulip -s /bin/bash zulip
RUN echo 'zulip ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers
RUN ln -nsf /srv/zulip ~/zulip
RUN echo 'export LC_ALL="en_US.UTF-8" LANG="en_US.UTF-8" LANGUAGE="en_US.UTF-8"' >> ~zulip/.bashrc
WORKDIR /srv/zulip
RUN chown -R zulip:zulip /srv/zulip
RUN curl -OL https://www.zulip.org/dist/releases/zulip-server-latest.tar.gz
RUN tar -xf zulip-server-latest.tar.gz
RUN /srv/zulip/zulip-server-2.0.3/scripts/setup/install --self-signed-cert --email=anton.d@optimum-web.com --hostname=f1banac1.tk
