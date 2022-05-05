Pre-Requisite:
- Create a Linux container / Linux server were we can run openssl commands.
yum -y install openssl vi

- Connect the linux box with existing K8s setup.

Kubectl Installation:

curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl

Step 1: Create a new private key  and CSR
openssl genrsa -out demo.key 2048
openssl req -new -key demo.key -out demo.csr -subj "/CN=demo"

Step 2: Encode the csr
cat demo.csr | base64 | tr -d '\n'

Step 3: Generate the Kubernetes Signing Request
apiVersion: certificates.k8s.io/v1
kind: CertificateSigningRequest
metadata:
  name: demo-csr
spec:
  groups:
  - system:authenticated
  request: $(cat demo.csr | base64 | tr -d '\n')
  signerName: kubernetes.io/kube-apiserver-client
  usages:
  - digital signature
  - key encipherment
  - client auth

Step 4: Apply the Signing Requests:
kubectl apply -f signingrequest.yaml

Step 5: Approve the csr
kubectl certificate approve demo-csr

Step 6: Download the Certificate from csr
kubectl get csr demo-csr -o jsonpath='{.status.certificate}' | base64 -d > demo.crt

Step 7: Create a new context
kubectl config set-credentials demo --client-certificate=demo.crt --client-key=demo.key

Step 8: Set new Context
kubectl config set-context demo-context --cluster cluster_name --user=demo

Step 9: Use Context to Verify
kubectl --context=demo-context get pods