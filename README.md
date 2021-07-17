<h1 align="center">Helm Template of Memo Project</h1>

<div align="center">

![Workflow](https://github.com/jiwonCha/memo-project-helm/actions/workflows/helm-package-push.yaml/badge.svg)
[![Status](https://img.shields.io/badge/status-active-success.svg)]()
[![GitHub Issues](https://img.shields.io/github/issues/jiwonCha/memo-project-helm.svg)](https://github.com/jiwonCha/The-Documentation-Compendium/issues)
[![GitHub Pull Requests](https://img.shields.io/github/issues-pr/jiwonCha/memo-project-helm.svg)](https://github.com/jiwonCha/memo-project-helm/issues)

</div>

---

## 📝 Table of Contents

- [About](#about)
- [Deployment](#deployment)
- [Usage](#usage)
- [Authors](#authors)
- [Github Action](#action)

## 🧐 About <a name = "about"></a>

It is helm template repository for memo-project 

## 🚀 Deployment <a name = "deployment"></a>

Curertnly, the artifacts of memo-project(helm, docker image) in the EC2 ECR.

You can `helm install` like belows.

```bash
export HELM_EXPERIMENTAL_OCI=1

NAME="memo-service"

aws ecr get-login-password --region ap-northeast-1 | helm registry login --username AWS --password-stdin 174420192082.dkr.ecr.ap-northeast-1.amazonaws.com/helm-artifact-repository
helm chart pull 174420192082.dkr.ecr.ap-northeast-1.amazonaws.com/helm-artifact-repository:memo-service
helm chart export 174420192082.dkr.ecr.ap-northeast-1.amazonaws.com/helm-artifact-repository:memo-service ./charts
helm install $NAME ./memo-service --namespace ns-memo-service
```

## 🎈 Usage <a name="usage"></a>

In browser, typing the address `http://ec2-18-181-110-180.ap-northeast-1.compute.amazonaws.com:30965/memo-service/memos`.



Memo Service is deployed in Amazon EC2 Node. You can access Memo service with this link - [Memo Service](http://ec2-18-181-110-180.ap-northeast-1.compute.amazonaws.com:30965/memo-service/memos)

## ✍️ Authors <a name = "authors"></a>

- [@jiwonCha](https://github.com/jiwonCha) - Write Helm Template

## 🔧 GitHub Action <a name = "action">

This code manage with github action workflow.

If is invoked PR or Commits in `main` branch, making helm artifacats and pushing them to EC2 ECR