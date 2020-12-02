FROM consul:1.9
COPY ./consul-kv-docker.json /usr/src/consul/
WORKDIR /usr/src/consul
ENV CONSUL_HTTP_ADDR=consul:8500
ENTRYPOINT until consul kv import @consul-kv-docker.json; do echo "Waiting for Consul"; sleep 2; done
