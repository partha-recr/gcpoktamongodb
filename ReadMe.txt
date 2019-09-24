Create Cluster with 5+ nodes with enable Istio

kubectl create clusterrolebinding cluster-admin-binding --clusterrole=cluster-admin --user=$(gcloud config get-value core/account)

git clone https://github.com/partha-recr/gcpoktamongodb.git
git pull origin

kubectl apply -f deployment-mongo.yml
gradlew clean build

docker build -t kayak-app:1.0 .
docker tag kayak-app:1.0 gcr.io/project1-245414/kayak-app:1.0
docker push gcr.io/project1-245414/kayak-app:1.0

kubectl apply -f deployment.yml
kubectl apply -f istio-gateway.yml