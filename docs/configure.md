# Configure

Let's see how to configure a service. We can use the service from the [previous](public.md) step.

## Environment variables

The service in [helloworld](../helloworld) folder looks for an environment variable `TARGET` to print out but it's not set. Let's set that variable in Cloud Run:

```bash
gcloud beta run services update helloworld-public \
  --platform managed \
  --update-env-vars TARGET=v1
```

Now, the service reads the environment variable:

```bash
curl https://helloworld-public-paelpl5x6a-ew.a.run.app

Hello v1!
```

## CPU

By default, 1 CPU is allocated for each container instance. This cannot be changed for managed Cloud Run but can be changed on Cloud Run on Anthos.

## Memory

By default, the service gets 256Mi of memory. Let's set it to maximum 2Gi:

```bash
gcloud beta run services update helloworld-public \
  --platform managed \
  --memory 2Gi
```

## Concurrency

By default, each container gets 80 requests. Let's half that to 40:

```bash
gcloud beta run services update helloworld-public \
  --platform managed \
  --concurrency 40
```

## Request timeout

By default, the request timeout is 300 seconds. Let's set it to maximum 900 seconds:

```bash
gcloud beta run services update helloworld-public \
  --platform managed \
  --timeout 900
```

## Autoscaling

By default, Cloud Run autoscales to 1000 containers. Let's set it to maximum 500:

```bash
gcloud beta run services update helloworld-public \
  --platform managed \
  --max-instances 500
```

## What's Next?

[Private service](private.md)