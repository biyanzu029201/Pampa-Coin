FROM debian:jessie
MAINTAINER pavik - https://github.com/pavik

ENV PAMPA_VERSION=1.0.3 \
 PAMPA_USER=pampa

ENV PAMPA_URL=https://github.com/PampaCoin/PampaCoin/releases/download/v$PAMPA_VERSION/pampa-$PAMPA_VERSION-x86_64-linux-gnu.tar.gz \
 PAMPA_CONF=/home/$PAMPA_USER/.PampaCoin/PampaCoin.conf \
 PAMPA_CONF_URL=https://raw.githubusercontent.com/PampaCoin/PampaCoin/master/PampaCoin.conf

RUN apt-get -qq update && \
apt-get install -yq wget ca-certificates pwgen && \
rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* && \
wget $PAMPA_URL -O /tmp/pampa.tar.gz && \
mkdir -p /opt && \
cd /opt && \
tar xvzf /tmp/pampa.tar.gz && \
rm /tmp/pampa.tar.gz && \
ln -sf pampa-$PAMPA_VERSION pampa && \
ln -sf /opt/pampa/bin/pampad /usr/local/bin/pampad && \
ln -sf /opt/pampa/bin/pampa-cli /usr/local/bin/pampa-cli && \
ln -sf /opt/pampa/bin/pampa-tx /usr/local/bin/pampa-tx && \
adduser --uid 1000 --system ${PAMPA_USER} && \
mkdir -p /home/${PAMPA_USER}/.PampaCoin/ && \
chown -R ${PAMPA_USER} /home/${PAMPA_USER} && \
echo "success: $PAMPA_CONF"

USER pampa
RUN wget $PAMPA_CONF_URL -O $PAMPA_CONF && \
    sed -i -e 's/\*your$username\*/pampa/g' ${PAMPA_CONF} && \
    sed -i -e 's/\*your$password\*/'`pwgen 32 1`'/g' ${PAMPA_CONF} && \
    echo "Success"

EXPOSE 51572
VOLUME ["/home/pampa/.PampaCoin"]
WORKDIR /home/pampa

ENTRYPOINT ["/usr/local/bin/pampad"]