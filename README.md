# How to create Argocd Environment and kubernetes env
## kubectl の設定
### 1. 現在のコンテキストを確認
```bash
kubectl config current-context
```

### 2. 設定したいコンテキストを設定
```bash
kubectl config use-context test
```

## argoCD環境の準備
### 1. namespaceを作成
```bash
kubectl create namespace argocd
```
### 2. Argocdコンテナを立ち上げる
```bash
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```
#### リファレンス
https://argo-cd.readthedocs.io/en/stable/

## kubernetes 環境構築
### 1. /argocd ディレクトリに配下にある設定ファイルを元にコンテナ起動
```bash
kubectl apply -f hoge.yaml
```
### 2. サービス起動状態確認
```bash
minikube service hoge-service --url
```
### 3. ターミナルに表示されたURLにアクセスしてサービスにアクセスできることを確認
　
## minikubeのingress有効化
### 1. 現在の設定を確認
```bash
minikube addons list
```
### 2. ingressを有効にする
```bash
minikube addons enable ingress
```

### 3. minikubeのLBを起動
```bash
minikube tunnel
```
## local環境のドメイン設定を変更
### 1. /etc/hostsに以下設定を追加
```bash
127.0.0.1 hoge-serbice-domain
```