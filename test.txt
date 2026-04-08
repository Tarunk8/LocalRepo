Question No 1

Task -
Create a new ClusterRole named deployment-clusterrole, which only allows to create the following resource types:
✑ Deployment
✑ Stateful Set
✑ DaemonSet
Create a new ServiceAccount named cicd-token in the existing namespace app-team1.
Bind the new ClusterRole deployment-clusterrole to the new ServiceAccount cicd-token, limited to the namespace app-team1.


Ans : 
Step 1. >>>kubectl create clusterrole deployment-clusterrole --verb=create --resource=Deployment,StatefulSet,DaemonSet
Step 2. >>>kubectl creat sa cicd-token -n app-team1
Step 3. >>>kubectl create clusterrolebinding deploy-b --clusterrole=deployment-clusterrole --serviceaccount=app-team1:cicd-token



Question No 2:

Task -
Set the node named ek8s-node-0 as unavailable and reschedule all the pods running on it.

Ans:
Step 1: > kubectl drain node01 --ignore-daemonsets --delete-emptydir-data 
Step 2: > kubectl get node >>> to check the satatus


Question No. 3
Task: Given an existing Kubernetes cluster running version 1.23.1, upgrade all the Kubernetes control plane and node components on the master node only to version 1.23.2
You can also expected to upgrade kubelet and kubectl on the master node.
Be sure drain the master node before upgrading it and uncordon it after upgrading. Do not upgrade the worker nodes, etcd,the container manager, the CNI plugin, the DNS server and any other addons.

Answer:
Step 1.> ssh master01
Step 2.> kubectl drain master01 --ignore-daemonsets --delete-emptydir-data 
Step 3.> apt-get update
Step 4 .> apt-get install kubeadm=1.28.2-00 kubectl=1.28.2-00 kubelet=1.28.2-00
Step 5 .> kubeadm upgrade plan 
Step 6 > kubeadm upgrade apply v1.28.2 --etcd-upgrade=false
Step 7. > kubectl uncordon master01


Question No. 4

Task -
First, create a snapshot of the existing etcd instance running at https://127.0.0.1:2379, saving the snapshot to /var/lib/backup/etcd-snapshot.db.
Creating a snapshot for a given instance is expected to complete within seconds. If the operation appears to hang, there may be a problem with the command. Use CTRL + C to cancel the operation and try again.

Then restore the existing previous snapshot located at /var/lib/backup/etcd-snapshot-previous.db.
The following TLS certificates and keys are provided to connect to the server via etcdctl:
·         CA certificate: /opt/KUIN00601/ca.crt
·         Client certificate: /opt/KUIN00601/etcd-client.crt
·         Client key: /opt/KUIN00601/etcd-client.key
Ans:-
Step 1.> export ETCDCTL_API=3
Step 2.> mkdir -pv /srv/data/
Step 3 > ETCDCTL_API=3 etcdctl --endpoints=https:127.0.0.1:2379 --cacert=/opt/KUIN00601/ca.crt --cert=/opt/KUIN00601/etcd-client.crt --key=/opt/KUIN00601/etcd-client.key snapshot save /var/lib/backup/etcd-snapshot.db
Step 3.> systemctl stop etcd.service
Step 4.> sudo ETCDCTL_API=3 etcdctl snapshot restore /var/lib/backup/etcd-snapshot-previous.db
Step 5.> systemctl restart etcd


Question No. 5

Task
Create a new NetworkPolicy called allow-port-from-namespace in the existing namespace my-app.      (allow-port-from-namespace search in 
Make sure the new NetworkPolicy allows Pods in namespace echo to connect to Pods in amespace my-app on port 9000.
Further ensure the new NetworkPolicy:
>>Disallow access to Pods that are not listening on port 9000
>>Access not from Pods in namespace echo is not allowed


Answer:
Step 1.> kubectl label ns echo project=echo
Step2 2.>  vi network.policy.yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-port-from-namespace
  namespace: my-app # The namespace being accessed
spec:
  podSelector: {}
  policyTypes:
    - Ingress # Policy affects incoming traffic
  ingress:
    - from: # The source of the allowed traffic
        - namespaceSelector:
            matchLabels:
              project: echo # The label of the visitor's namespace label
      ports:
        - protocol: TCP
          port: 9000 # The port exposed by the visitor

Step 3. > kubectl create -f network.policy.yaml 

Question No.6 

Task -
Reconfigure the existing deployment front-end and add a port specification named http exposing port 80/tcp of the existing container nginx.   (Search in "Deployment")
Create a new service named front-end-svc exposing the container port http.
Configure the new service to also expose the individual Pods via a NodePort on the nodes on which they are scheduled. (search "nodeport")

Ans:
Step 1.> kubectl edit deplyments fron-end and add the below details in it
         imagePullPolicy: Always
            name: nginx
               ports:
                  - containerPort: 80
                    name: http  and save the file
Step 2.>  kubectl expose deployment front-end --name=front-end-svc --port=80 --target-port=http --type=NodePort

Step 3> vim servcie.yaml
apiVersion: v1
kind: Service
metadata:
  name: front-end-svc    
spec:
  type: NodePort        
  selector:
    app: nginx            
  ports:
    - port: 80          
      targetPort: http 
Step 4>> kubectl create -f service.yaml 
Step 5> kubectl get svc front-end-svc

Question No. 7

Task-:
Create a new nginx lngress resource as follows:    (search in "ingress") (ingress classname: nginx......need to remove) (for practice create a namespace "iing-internal) and try
·         Name: pong
·         Namespace: ing-internal
·         Expose the service hello on the path /hello using service port 5678

Answer:-
Step 1>> vi ingress.yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: pong
  namespace: ing-internal
  annotations:
    nginx.ingress.kubernetes.io/rewrite-target: /
spec:
  ingressClassName: nginx
  rules:
  - http:
      paths:
      - path: /helllo
        pathType: Prefix
        backend:
          service:
            name: hello
            port:
              number: 5678
Step 2> kubectl create -f ingress.yaml


Question No.8 

Task-
Expand the number of copies of Pods managed by the loadbalancer's deployment to six.

Answer:-
Step 1.> kubectl scale deployment loadbalancer --replicas=6


Question No. 9

Task
Create a Pod named nginx-kusc00401, the mirror address is nginx, and schedule it on the node with the disk=spinning label.  ( search in "node selector")
	
Answer:-
Step 1.> kubectl label nodes cka-node01 disk=spinning	
Step 2.> vim nodeselector.yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-kusc00401            
spec:
  containers:
  - name: nginx                    
    image: nginx
    imagePullPolicy: IfNotPresent
  nodeSelector:
    disk: spinning                
Step 3.> kubectl create -f nodeslector.yaml


Question No.10
Task
Check how many nodes in the cluster are in the Ready state (excluding nodes marked with Taint: NoSchedule), and then write the number to /opt/KUSCO0402/kusc00402.txt.
Answer:-
step 1.> kubectl describe nodes cka-master1 cka-node1 | grep "Taint" | grep "NoSchedule" | wc -l > /opt/KUSCO0402/kusc00402.txt


Question no. 11

Task:  Create a Pod named kucc1. This Pod contains 4 containers, namely nginx, redis, consul

Answer:-
kubectl run kucc1 -image=nginx --dry-run=client -o yaml > pod.yaml
After that add the containers in container section name 

Step 2.> kubectl creat -f pod.yaml


Question No.12
Task

Create a pv named app-config, size 2Gi, and access permission ReadWriteMany. The type of Volume is hostPath, and the path is /srv/app-config  (search in persistent volume)

Answer:
Step 1>>  Creat a yaml file for 
apiVersion: v1
kind: PersistentVolume
metadata:
  name: app-config
spec:
  capacity:
    storage: 2Gi
  accessModes:
    - ReadWriteMany
  hostPath:
    path: "/srv/app-config"

Step 2. > kubectl creat -f peristant.yaml
Step 3. > kubectl get pv app-config-----to check the status of persistant volume running


Question No.13    (we can c pvc under the persistent volume)
Task -
Create a new PersistentVolumeClaim:
✑ Name: pv-volume
✑ Class: csi-hostpath-sc
✑ Capacity: 10Mi
Create a new Pod which mounts the PersistentVolumeClaim as a volume:
✑ Name: web-server
✑ Image: nginx
✑ Mount path: /usr/share/nginx/html
Configure the new Pod to have ReadWriteOnce access on the volume.
Finally, using kubectl edit or kubectl patch expand the PersistentVolumeClaim to a capacity of 70Mi and record that change.

Answer:--


Question No 14
Monitor the logs of the pod named foobar and filter for lines with unable-access-website information, which will then be written to /opt/KUTR00101/foobar.

Answer:-
kubectl logs foobar | grep -i "unable-access-website" > /opt/KUTR00101/foobar


Question No. 15

Context -
An existing Pod needs to be integrated into the Kubernetes built-in logging architecture (e.g. kubectl logs). Adding a streaming sidecar container is a good and common way to accomplish this requirement.

Task -
Add a sidecar container named sidecar, using the busybox image, to the existing Pod big-corp-app. The new sidecar container has to run the following command:
Use a Volume, mounted at /var/log, to make the log file big-corp-app.log available to the sidecar container.

Question No.16

Task -
From the pod label name=overloaded-cpu, find pods running high CPU workloads and write the name of the pod consuming most CPU to the file /opt/
KUTR00401/KUTR00401.txt (which already exists).

kubectl top pods -n name=overloaded-cpu --sort-by=cpu 
echo "high cpu" >  /opt/
KUTR00401/KUTR00401.txt


Question No.17

Task -
A Kubernetes worker node, named wk8s-node-0 is in state NotReady.
Investigate why this is the case, and perform any appropriate steps to bring the node to a Ready state, ensuring that any changes are made permanent.


Answer:--
kubectl get nodes>>>>> check the node which is not working
kubectl describe node (non-working node)>>> check the reason for not working 
ssh non-working node>>>>>>>>going to the node and aply the fixes for kubelet
systemctl start kubelet
systemctl enable kubelet
systemctl status kubelet

kubectl exec -it <pod-name>  -- /bin/bash     (to login the pod use command)
kubectl exec -it <pod-name> -c <container-name> -- /bin/bash   (to check the container runnnning inside pod)
.....................................
= config map can be create a environment variable as well



