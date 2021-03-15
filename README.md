# ACM-policies
ACM Policies Kustomization

acm-policies
Kustomizable Policies and Channel/Subscription objects for Advanced Cluster Management. This project covers use cases commonly found in consulting engagements and are provided to make configuration and enforcement adhere to Red Hat Consulting's best practices.

There are also product focused policies found in the upstream project (Open Cluster Management) called policy-collection. The product team will periodically check here for useful policies.

Creating new Policies
For each use case,

Create a unique usecase folder under policies/
Create a README.md file under the folder to explain the actions and purpose of the collection of policies.
Create a base folder for base files: policies, placement rules, and bindings.
Create an overlay folder with at least 1 overlay example on how to kustomize it.
Create subscription(s) for the overlay examples.
acm-policies
├── channel
│   ├── 01_namespace.yml
│   └── 02_channel.yml
├── policies
│   └── example
|       ├── USECASE.md
│       ├── base
│       │   ├── bindings.yml
│       │   ├── kustomization.yml
│       │   ├── placementrule.yml
│       │   └── policy-namespace-custom.yml
│       ├── overlays
│       │   ├── pets
│       │   │   ├── kustomization.yml
│       │   │   └── namespaces.yml
│       │   └── plants
│       │       ├── kustomization.yml
│       │       └── namespaces.yml
│       └── subscriptions
│           ├── sub-example-base.yml
│           ├── sub-example-pets.yml
│           └── sub-example-plants.yml
└── README.md

Using Policies in ACM
Fork the project and update the channel and namespace yml to leverage your new endpoint.
Create an overlay in the same manner as the example overlay.
Create patches that tailor the policy to your environment.
Create a subscription using the new overlay.
Apply the channel and namespace to the hub cluster.
$ oc apply -f channel/
Apply the subscription to the hub cluster.
$ oc apply -f subscriptions/my-subscription.yml
