Single Orderer, Single Peer for one organisation - Hyperledger Fabric Network on minikube/kubernetes.

Most of the k8 Specific files are okay to understand. All resources are created in 'org1' namespace except the persistent volume which is across cluster.

Only challenge was how to make chaincode container talk to peer node.

Kubernetes is aware of all containers except chaincode container as it was started by the peer on instantiation and not by K8s. So chaincode container and peer container were not able to talk to each other.

To work around this, I had add this docker daemon.json to /etc/docker/ folder. and reload and restart the docker daemon service.
