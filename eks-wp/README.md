link de donde se saco el ejemplo:
https://aws.amazon.com/blogs/storage/running-wordpress-on-amazon-eks-with-amazon-efs-intelligent-tiering/

despues de la creación del cluster efs, para configurar los drives de EFS y tener las credenciales de EKS:

helm repo add aws-efs-csi-driver https://kubernetes-sigs.github.io/aws-efs-csi-driver/

kubectl apply -f private-ecr-driver.yaml

aws eks update-kubeconfig --region us-east-1 --name myeks

no se utilizan los archivos mysql-deployment.yaml propuesto en la página de referencia, y se utiliza 01mysql-deployment.yaml depurado de varias fuentes.

crear wp:
kubectl apply -k ./

monitorear:
kubectl get pods --watch
kubectl get all -o wide

conectarse a un pod:

kubectl exec -it <podname> /bin/bask

borrar wp:
kubectl delete -k ./
