# kubernetes-echo

This demonstrates a simple k8s service and there is a bug that we are encountering.  See http://stackoverflow.com/questions/34732597/kubernetes-pod-cant-connect-through-service-to-self-only-to-other-pod-contai

To use this, do the following.

1. create your kubernetes network
2. build the image: ./build.sh
3. upload the image: ./upload.sh
5. create the controller & service
  i. kubectl create -f echo.controller.yaml
  ii. kubectl create -f echo.service.yaml
4. get the service ip
  i. kubectl get svc | grep echo-server-1
4. ssh to a pod
  i. get a list of your pods via: kubectl get po
  ii. ssh in with: kubectl exec -it {podname} /bin/bash
5. connect to the service repeatedly until you hang
  i. nc {service_ip} 8080


