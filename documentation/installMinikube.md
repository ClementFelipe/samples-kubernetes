Requirement before following guide: macOS with [homebrew](https://brew.sh/) and docker

# Install and use minikube with Hyperkit driver

This is a series of simple steps to be able to set up a local `kubernetes` cluster and use it via [kubectl](https://kubernetes.io/docs/reference/kubectl/kubectl/).

## 1 - Install docker-machine-hyperkit-driver

This installs a driver to be used by `docker-machine` called [hyperkit](https://github.com/moby/hyperkit) to run the virtual machine used by minikube.

Just type the following command on your terminal:
```bash
brew install docker-machine-driver-hyperkit
```

When the install finishes, brew will prompt you to run 2 commands, do it.

## 2 - Install minikube

This is the tool used for `kubernetes` local development, which means it creates a `kubernetes` cluster with one **node** and one **master**.

```bash
brew cask install minikube
```

## 3 - Run minikube with hyperkit driver

This step will create a virtual machine with docker machine using the previously installed `hyperkit` driver and set up a context called `minikube` for `kubectl` to use:

```bash
minikube start --vm-driver=hyperkit
```

## 4 - Install kubectl

[kubectl](https://kubernetes.io/docs/reference/kubectl/kubectl/) is the command-line tool for communicating with a `kubernetes` master cluster manager API; every command typed is transformed into a REST API request and sent to the cluster.

Command to install:
```bash
brew install kubernetes-cli
```

## 5 - Connect to minikube cluster

In this step, `kubectl` context is switched to interact with `minikube`:

```bash
kubectl config use-context minikube
```

## 6 - Test connection to cluster

Run the minikube dashboard and enjoy :)

```bash
minikube dashboard
```