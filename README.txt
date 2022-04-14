





# Create IAM Service Account for Cluster Auto Scaler

eksctl create iamserviceaccount \
  --cluster=demo \
  --namespace=kube-system \
  --name=cluster-autoscaler \
  --attach-policy-arn=arn:aws:iam::546362229912:policy/AmazonEKSClusterAutoscalerPolicy \
  --override-existing-serviceaccounts \
  --approve



# Install K8s Metric Server
kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml

# Configure Pod Autoscaling

kubectl autoscale deployment DEPLOYMENT --min=MIN_NUMBER_PODS --max=MAX_NUMBER_PODS --cpu-percent=CPU_PERCENT -n NAMESPACE