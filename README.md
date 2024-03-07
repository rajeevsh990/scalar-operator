# scaler-operator
This operator will scale your deployment within a certain period of time. Input needed are: 

StartTime, EndTime and Replicas

## Instructions to run the program
1. Start setup: 
>> operator-sdk init --plugins go.kubebuilder.io/v4 --domain rajeevsh990.online --owner "Rajeev Sharma" --repo github.com/rajeevsh990/scaler-operator 
// update CONTROLLER_TOOLS_VERSION ?= v0.14.0 in Makefile
>> operator-sdk create api --group api --version v1beta1 --kind Scaler 

2. Prepare code base
- prepare input struct (as defined by the custom object) in api/v1beta1/scaler_typtes.go
- prepare a sample in config/samples/api_v1beta1_scaler.yaml 
- prepare the controller login in internal/controller/scaler_controller.go

3. prepare your cluster with the prepared files 
- minikube start and have a cluster ready 
- create a namesapce scaler and deploy nginx pod 
- apply the customResourceDefinition to your cluster from file: config/crd/bases/api....yaml
- apply the sample custom object to the cluster from file: config/sample/api_v1beta1_scaler.yaml

4. Run operator
>> make run 

## below are generic details

## Description
// TODO(user): An in-depth paragraph about your project and overview of use

## Getting Started

### Prerequisites
- go version v1.20.0+
- docker version 17.03+.
- kubectl version v1.11.3+.
- Access to a Kubernetes v1.11.3+ cluster.

### To Deploy on the cluster
**Build and push your image to the location specified by `IMG`:**

```sh
make docker-build docker-push IMG=<some-registry>/scaler-operator:tag
```

**NOTE:** This image ought to be published in the personal registry you specified. 
And it is required to have access to pull the image from the working environment. 
Make sure you have the proper permission to the registry if the above commands don’t work.

**Install the CRDs into the cluster:**

```sh
make install
```

**Deploy the Manager to the cluster with the image specified by `IMG`:**

```sh
make deploy IMG=<some-registry>/scaler-operator:tag
```

> **NOTE**: If you encounter RBAC errors, you may need to grant yourself cluster-admin 
privileges or be logged in as admin.

**Create instances of your solution**
You can apply the samples (examples) from the config/sample:

```sh
kubectl apply -k config/samples/
```

>**NOTE**: Ensure that the samples has default values to test it out.

### To Uninstall
**Delete the instances (CRs) from the cluster:**

```sh
kubectl delete -k config/samples/
```

**Delete the APIs(CRDs) from the cluster:**

```sh
make uninstall
```

**UnDeploy the controller from the cluster:**

```sh
make undeploy
```

## Contributing
// TODO(user): Add detailed information on how you would like others to contribute to this project

**NOTE:** Run `make help` for more information on all potential `make` targets

More information can be found via the [Kubebuilder Documentation](https://book.kubebuilder.io/introduction.html)

## License

Copyright 2024 Rajeev Sharma.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

