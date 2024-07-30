To get the <base64-encoded-docker-config>, you can run the following command with your registry credentials:
echo -n '{"auths":{"<your-registry-server>":{"username":"<your-username>","password":"<your-password>","email":"<your-email>"}}}' | base64

Apply the Secret: Apply the YAML file to your cluster.
oc apply -f image-pull-secret.yaml

Step 3: Link the Secret to the Service Account
Link the Secret: Link the newly created secret to the service account
oc secrets link my-operator-sa my-registry-secret --for=pull -n <namespace>

Step 4:
Create the Operator Deployment
oc apply -f operator-deployment.yaml

Step 5: Verify the Deployment
Check the Pods: Ensure the operator pod is running and using the correct service account and image pull secret.

oc get pods -n <namespace>
Describe the Pod: Check the details of the pod to verify the configuration.

oc describe pod <operator-pod-name> -n <namespace>

Check Logs: Ensure the operator is functioning correctly by checking the pod logs.

oc logs <operator-pod-name> -n <namespace>
