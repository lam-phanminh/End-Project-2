1. Link github repo: https://github.com/lam-phanminh/End-Project-2

2. To run Jenkinsfile. I set up a node docker. 
   
    ![](./Pictures/docker-cloud.png)
    ![](./Pictures/config-cloud-1.png)
    ![](./Pictures/config-cloud-2.png)

3. Set up credentials: 

   ![](./Pictures/Credentials.png)

4. Create job multi branch: 
   
   ![](./Pictures/job-1.png) 
   ![](./Pictures/job-2.png) 
   ![](./Pictures/job-3.png) 
   ![](./Pictures/job-main.png) 

5. Console output: 
   - Stage: ``Build ``
  
   ![](./Pictures/stage-build.png) 

   - Stage: `` Build Docker Image `` 
  
    ![](./Pictures/stage-build-image.png)

   - Stage: `` Push Docker Image`` 

    ![](./Pictures/stage-push.png)
    ![](./Pictures/stage-push-done.png)

   - Stage: `` CanaryDeploy`` 

    ![](./Pictures/stage-canary-deploy.png)
    ![](./Pictures/stage-canary-deploy-done.png)

   - Stage: `` DeployToProduction``

    ![](./Pictures/stage-deploy-production.png)
    ![](./Pictures/stage-deploy-production-done.png)   

6. Images pushed to dockerhub: 
   
    ![](./Pictures/docker-hub-2.png)

7. Deployments: 

    ![](./Pictures/deployments.png) 

8. Services: 

    ![](./Pictures/svcs.png)

9. Pods: 
    
    ![](./Pictures/pods.png) 

10. Install metric-server: ``kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml``

    ![](./Pictures/deployment-metric-server.png)
    ![](./Pictures/metric-server.png)

11. ``kubectl top pod`` 

    ![](./Pictures/top-pod.png)

12. Config HPA to deployments: 

    ![](./Pictures/config-hpa-1.png) 
    ![](./Pictures/config-hpa-2.png) 

13. ``kubectl describe hpa hpa-train-schedule-deployment-canary ``

    ![](./Pictures/hpa-1.png)
    
14. ``kubectl describe hpa kubectl describe hpa hpa-train-schedule-kube``

    ![](./Pictures/hpa-2.png)

15. `` kubectl get hpa ``

    ![](./Pictures/hpa.png)

16. Deploy ``Prometheus - Grafana`` by ``helm`` 
- Run commands: 
    + ``kubectl create namespace monitoring`` 
    + ``helm repo add prometheus-community https://prometheus-community.github.io/helm-charts``
    + ``helm repo update`` 
    + ``helm install prometheus-grafana-stack prometheus-community/kube-prometheus-stack --namespace monitoring``

   ![](./Pictures/after-deploy.png) 

- NodePort Prometheus and Grafana. 
  
- Access Prometheus: 
  
   ![](./Pictures/prometheus.png)

- Access Grafana, login and import dashboard ID ``1860``

   ![](./Pictures/grafana.png)