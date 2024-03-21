# This project is to explore the capabilities of autoscaling for VK or JRM of JIRIAF

## Testing Upscaling and Downscaling of Pods for VK using HPA of Kubernetes
This document describes the process of testing the upscaling and downscaling of pods for VK using the Horizontal Pod Autoscaler (HPA) of Kubernetes.

### Setup
The test setup involves a HTTP load balancer implemented in Go (`load_balancer.go`). This load balancer redirects HTTP requests to multiple HTTP servers, each implemented in Go (`server.go`).

The deployment of Kubernetes is defined by this HTTP server. This means that the number of replicas or pods creates several HTTP servers. The scaling of these pods is managed by the HPA.

### Load Generation
The load of HTTP requests is generated by the `hey` application, which is invoked by the bash script `add-load.sh`.

### Test Results
The results of the test demonstrate that the HPA works for VK, including the upscaling and downscaling of pods. When the load increases, the HPA increases the number of pods to handle the load (upscaling). When the load decreases, the HPA reduces the number of pods (downscaling) after five mins from the last operation.