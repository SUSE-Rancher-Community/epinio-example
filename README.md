# Epinio Example

NOTE: due to a current bug doing this example on Windows using WSL2 will not work.

## Prerequisites

These are all the components needed to start this challenge. Epinio is also needed but we will be installing that in the next section.

### Core

1. [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl)
2. [git client](https://git-scm.com/downloads/guis)
3. [helm](https://helm.sh/docs/intro/install/)
4. [Docker](https://www.docker.com/)
5. [k3d](https://k3d.io/)

## Install

One of the first things we need to do is to install the Epinio CLI. This will be our way of interacting with Epinio on our cluster.

Download the Epinio binary:

Linux:

```bash
curl -o epinio -L https://github.com/epinio/epinio/releases/download/v0.0.20/epinio-linux-amd64
```

Mac:

```bash
curl -o epinio -L https://github.com/epinio/epinio/releases/download/v0.0.20/epinio-darwin-amd64
```

Make the binary executable

```bash
chmod +x epinio
```

Move the binary to your PATH

```bash
sudo mv ./epinio /usr/local/bin/epinio
```

## Deploying

Create your k3d cluster:

```bash
k3d cluster create epinio -p '80:80@server[0]' -p '443:443@server[0]' 
```

Install Epinio on your cluster:

```bash
epinio install --system-domain=127.0.0.1.omg.howdoi.website
```

Now let's clone a sample app:

```bash
git clone https://github.com/epinio/epinio.git
```

Change directories:

```bash
cd epinio/assets/
```

Push an app using Epinio:

```bash
epinio push sample sample-app
```

List all your apps with the list command:

```bash
epinio apps list
```

## Conclusions

This was a quick getting started guide to Epinio. Learn more about the [commands](https://github.com/epinio/epinio/blob/main/docs/user/references/cli/epinio.md).

## Challenge

See if you can push your app via Epinio. Let us know in community how well it worked.
