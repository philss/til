# Basics about Kubernetes

What I learned so far was only the basics about Kubernetes.

Pods are equivalent to the container description surround by it's "dependencies".
They are not available to the external world until required by Services.
Services are descriptions about how to make that pod available.

There is another important concept that is Deployment, which makes a new version available.

## Tools

Mostly we will use `kubectl`, and if we are using Google's plataform, we need to manage things
with the `gcloud` tool.

In my case, I'm using the Google infrastructure, and I had to login with `gcloud` and enable
APIs requested by Google when creating my first **cluster**.

## Pods

Pods are the **Logical application**. It is like a contained application with a private network,
and one IP address. You can, for example, pack your Web app and an Nginx in the same Pod.

### Creating pods

Pods can be created with the `kubectl create` command passing the pod configuration with the `-f`
flag.

```
$ kubectl create -f pods/my-pod.yml
```

To check the pods running, you can try `kubectl get pods`.


## Other things

You can manage configuration and secrets using Kubernetes.
There is a good explanation about secrets [here](https://kubernetes.io/docs/concepts/configuration/secret/).
