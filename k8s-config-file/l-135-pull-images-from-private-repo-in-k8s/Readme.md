##### print full docker login command for aws ecr

    aws ecr get-login

##### login in docker private repo

    docker login -u AWS -p {password} https://aws-ecr-link
    take {password} from ~ aws ecr get-login-password
    or
    aws ecr get-login-password --region ap-south-1 | docker login --username AWS --password-stdin 399434923446.dkr.ecr.ap-south-1.amazonaws.com

##### generated file
    cat .docker/config.json
    cat .docker/config.json | base64

##### create docker login secret from config.json file

    kubectl create secret generic my-registry-key \
    --from-file=.dockerconfigjson=.docker/config.json \
    --type=kubernetes.io/dockerconfigjson

    kubectl create secret generic my-registry-key --from-file=.dockerconfigjson=.docker/config.json --type=kubernetes.io/dockerconfigjson

    kubect get secret

##### create docker login secret with login credentials

    kubectl create secret docker-registry my-registry-key \
    --docker-server=https://private-repo \
    --docker-username=user \
    --docker-password=pwd

    kubectl create secret docker-registry my-registry-key --docker-server=https://private-repo --docker-username=user --docker-password=pwd

##### access minikube console

    minikube ssh

##### copy config.json file from Minikube to my host

    scp -i $(minikube ssh-key) docker@$(minikube ip):.docker/config.json .docker/config.json
