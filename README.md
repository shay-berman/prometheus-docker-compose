# prometheus-docker-compose
This is just a short POC for setting up prometheus as remote_read with 2 prometheus instances below that scrap redis app.
Since there is issue with remote_read I share it here in order to consult with prometheus slack channel.

Start `prometheus1\2` that scrap `redis1\2` via `redis-exporter1\2` container. And also **prometheus-read** that do `remote_read` from **prometheus1\2**.
```bash
cd compose-test
docker-compose up -d
```
- Open browser [prometheus1](http://localhost:9091/) and try to query `redis_up` metric.
- Open browser [prometheus2](http://localhost:9092/) and try to query `redis_up` metric.
- Open browser [prometheus-read](http://localhost:9090/) and try to query `redis_up` metric. if works then remote_read works.
- Open browser [grafana](http://localhost:3000/) which define with prometheus-read as datasource. Try to query `redis_up` metric - if works then remote_read works. 

But for some reason the prometheus-read does not see the metrics from prometheus1 nor prometheus2.
