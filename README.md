# Kubernetes Guestbook Final Project

This repository contains the final project work for the IBM course on containers, Kubernetes, and OpenShift.  
The project builds and deploys a Guestbook application, applies horizontal pod autoscaling, and demonstrates rolling updates and rollbacks.

## Project Structure

- `v1/guestbook/Dockerfile` - Multi-stage Docker build for the Guestbook app
- `v1/guestbook/main.go` - Application backend
- `v1/guestbook/public/` - Frontend assets
- `v1/guestbook/deployment.yml` - Kubernetes deployment manifest
- `v1/guestbook/hpa.yml` - Horizontal Pod Autoscaler manifest

## Lab Workflow

1. Clone source and move to `v1/guestbook`.
2. Build and push image `guestbook:v1`.
3. Apply `deployment.yml`.
4. Run `kubectl port-forward deployment.apps/guestbook 3000:3000` and verify app.
5. Apply horizontal scaling using `hpa.yml` and verify with `kubectl get hpa`.
6. Update title/header in `public/index.html` to `Guestbook - v2`.
7. Build and push `guestbook:v2`, then update deployment image.
8. Update CPU values in `deployment.yml`:
   - limits: `cpu: 5m`
   - requests: `cpu: 2m`
9. Apply changes, verify rollout history, and rollback to revision 1.

## Useful Commands

```bash
kubectl apply -f deployment.yml
kubectl get pods
kubectl port-forward deployment.apps/guestbook 3000:3000
kubectl apply -f hpa.yml
kubectl get hpa
kubectl rollout history deployment/guestbook
kubectl rollout undo deployment/guestbook --to-revision=1
kubectl get rs
```

## Submission Evidence Filenames

For graded submissions, save outputs/screenshots using the expected names from the lab, such as:

- `Dockerfile` output capture
- `crimages`
- `deployment`
- `upguestbook`
- `rev`
- `rs`
