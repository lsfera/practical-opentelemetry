# Opentelemetry Experiment with .NET Core 3.x

[![OpenTelemetry Badge](https://img.shields.io/badge/OpenTelemetry-enabled-blue.svg)](http://opentelemetry.io)

This is a demo to show how to use OpenTelemetry for tracing on multiple services with multi-protocols on .NET Core 3.x

# Demo scenario

1. Web API (REST) - http://localhost:5000
2. WeatherService (gRPC) - http://localhost:5002
3. ProductService (REST) - http://localhost:5001
4. MeteoriteService (gRPC) - http://localhost:5003

![](assets/high-level-architecture-demo.png)

### Step 1:

```
$ docker-compose up
```

### Step 2:

Then run 3 projects above with Visual Studio or Visual Code

### Step 3: Run `Web API` with url as below

[http://localhost:<port>/WeatherForecast](http://localhost:<port>/WeatherForecast)

## Jaeger UI

REST -> gRPC -> REST

[http://localhost:16686](http://localhost:16686/)

![](assets/tracing01_jaeger.png)

## Zipkin UI

REST -> gRPC -> REST

[http://localhost:9412](http://localhost:9412/)

![](assets/tracing01_zipkin.png)

Trace from SampleWeb to MeteoriteService and to Remote URL at https://data.nasa.gov/resource/y77d-th95.json

![](assets/tracing02_zipkin.png)

Trace with error on the consumer side

![](assets/tracing03_zipkin.png)

## Prometheus - Grafana

Healthcheck with Prometheus

![](assets/prom_01.png)

Monotoring .NET resource with Grafana

![](assets/grafana_01.png)

## Loki - Grafana

[http://localhost:3000](http://localhost:3000/)

Type `{app="sample-web", level="information"} \d{1,9}ms` on `Log labels`

![](assets/loki-grafana-logs.png)

## Seq UI

[http://localhost:5340](http://localhost:5340/)

![](assets/logging01.png)
