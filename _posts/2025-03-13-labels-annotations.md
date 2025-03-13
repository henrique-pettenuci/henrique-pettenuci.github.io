---
layout: post
title:  "Annotations vs Labels in Kubernetes: Understand the Differences"
date:   2025-03-13 12:30:00 +0000
categories: kubernetes
tags: labels
---

Kubernetes is a powerful container orchestration tool that offers many ways to organize and manage resources. Two such methods are through labels and annotations. They may seem similar at first sight, but each serves a very distinct purpose. I will explore these differences and show practical examples of how labels can be used, as well as demonstrate how some tools and operators use annotations to read configurations to help in cluster operation and maintenance.

### What are Labels?

Labels are key/value pairs that act as “tags” for Kubernetes objects. They allow you to:

- **Identify and group objects**: For example, you can mark the pods that are part of the same service with `app: my-app` or indicate that they represent a specific function with `type: backend`.
- **Simplify resource organization**: Labels help structure configurations so that other objects, such as Services, can reference them easily and efficiently.

**Example of using Labels in a Pod**:
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: web-app
  labels:
    app: web-app
    type: backend
spec:
  containers:
  - name: web
    image: nginx:latest
```

#### Examples of Finding Objects with the Same Label

One of the great advantages of using labels is the ease of locating and grouping related objects within the cluster. Here are some practical examples of how to find different types of objects that share the same label:

- **Find all Pods with a specific label**: `kubectl get pods -l app=web-app`
- **Find associated ReplicaSets**: `kubectl get replicasets -l app=web-app`
- **Combine Different Object Types**: `kubectl get all -l app=web-app`

#### Using Labels in Services

A Service uses labels to associate traffic with the correct pods. In the Service manifest, a selector is defined that corresponds to the labels of the pods that should receive the traffic.

**Example of a Service using Labels**:
```yaml
apiVersion: v1
kind: Service
metadata:
  name: web-service
  labels:
    app: web-app
spec:
  selector:
    app: web-app
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
```
In this example, the Kubernetes Service `web-service` uses the selector `app: web-app` to identify all pods that have that label. This approach of reusing the same label in different objects helps ensure that all components related to the same application are integrated cohesively.

---
### What are Annotations?

Annotations are also key/value pairs but differ from labels in that they are not used for identifying or selecting objects. They serve to:

- **Store unstructured metadata**: Additional information that does not need to be used for grouping, such as descriptions, links to documentation, or technical details.
- **Facilitate integration with tools and operators**: Many tools use annotations to configure specific behaviors or extract information from a resource.

#### Practical Examples of Annotations

1. **Prometheus Operator**: The Prometheus Operator uses annotations to identify which pods should be monitored. By adding the annotation `prometheus.io/scrape: "true"`, you indicate that the pod’s endpoint should be collected by Prometheus. While `prometheus.io/port: "80"` specifies the port where metrics can be found.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: web-app
  labels:
    app: web-app
    type: backend
  annotations:
    prometheus.io/scrape: "true"
    prometheus.io/port: "80"
spec:
  containers:
  - name: web
    image: nginx:latest
```

2. **Cert-Manager**: Cert-manager is a tool that automates the issuance and renewal of TLS certificates and also uses annotations. For example, you can annotate an Ingress to indicate that it should be managed by cert-manager, which will then issue a certificate. The annotation `cert-manager.io/cluster-issuer: "letsencrypt-prod"` tells cert-manager that it should issue a TLS certificate for the Ingress using the configured cluster issuer. This allows cert-manager to automatically validate and issue certificates.

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: web-ingress
  annotations:
    cert-manager.io/cluster-issuer: "letsencrypt-prod"
    nginx.ingress.kubernetes.io/ssl-redirect: "true"
spec:
  rules:
  - host: "my-app.example.com"
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: web-service
            port:
              number: 80
  tls:
  - hosts:
    - "my-app.example.com"
    secretName: my-app-tls
```

---

### Conclusion

Both labels and annotations are essential for organizing and operating resources in Kubernetes, but each serves a specific role:

- **Labels** are crucial for identifying and grouping objects, allowing components such as Services to seamlessly integrate the correct pods. In addition, it is easy to find different types of objects (Pods, Deployments, ReplicaSets, etc.) that share the same label, which greatly simplifies management and visualization of your environment.
- **Annotations** enrich resources with additional metadata, allowing tools and operators (like the Prometheus Operator and cert-manager) to extract crucial information for automation, monitoring, and configuration.

Understanding these differences and how to use each one can help keep your cluster organized, facilitate automated operations, and improve the overall management of your applications.

For more detailed documentation, please check: 
[Labels](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/)
[Annotations](https://kubernetes.io/docs/concepts/overview/working-with-objects/annotations/)