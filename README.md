# ebpf-test

```
docker-compose up -d
```

-----------------------------------

#### Individual commands (Just for reference)

Otel collector -- 0.45.0
```
docker run -it -v <PATH_TO_CONFIG_FOLDER>:/etc/democonfig -p 4318:4318 otel/opentelemetry-collector:0.45.0 --config=/etc/democonfig/otel-config-test.yaml
```

eBPF Test
```
docker run -it --rm   --env EBPF_NET_INTAKE_HOST="127.0.0.1"   --env EBPF_NET_INTAKE_PORT="4318"   --env EBPF_NET_INTAKE_ENCODER="otlp_log" --privileged --pid host --network host --volume /var/run/docker.sock:/var/run/docker.sock --volume /sys/fs/cgroup:/hostfs/sys/fs/cgroup --volume /etc:/hostfs/etc --volume /var/cache:/hostfs/cache --volume /usr/src:/hostfs/usr/src   --volume /lib/modules:/hostfs/lib/modules   ghcr.io/middleware-labs/kernel-collector     --log-console
```

