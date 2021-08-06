docker build -t henbi/multi-client:latest -t henbi/multi-client:$SHA -f ./client/Dockerfile ./client
docker build -t henbi/multi-server:latest -t henbi/multi-server:$SHA -f ./server/Dockerfile ./server
docker build -t henbi/multi-worker:latest -t henbi/multi-worker:$SHA -f ./worker/Dockerfile ./worker

docker push henbi/multi-client:latest
docker push henbi/multi-server:latest
docker push henbi/multi-worker:latest

docker push henbi/multi-client:$SHA
docker push henbi/multi-server:$SHA
docker push henbi/multi-worker:$SHA

kubectl apply -f k8s
kubectl set image deployments/server-deployment server=henbi/multi-server$SHA
kubectl set image deployments/client-deployment client=henbi/multi-client$SHA
kubectl set image deployments/worker-deployment worker=henbi/multi-worker$SHA
