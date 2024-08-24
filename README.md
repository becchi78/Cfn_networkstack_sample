# Cfn_network_sample

Cfn のネステッドスタックとクロススタック参照のサンプル（network）

## 準備

templates/にある vpc.yaml と subnet.yaml はあらかじめ S3 の cfn-nested-sample に置いておく。

```bash
aws s3 cp ./templates/vpc.yaml s3://cfn-nested-sample/network/
aws s3 cp ./templates/subnet.yaml s3://cfn-nested-sample/network/
```

## デプロイ

```bash
aws cloudformation create-stack \
  --stack-name NetworkStack \
  --template-body file://root-template.yaml \
  --parameters file://param/parameters.json \
  --capabilities CAPABILITY_IAM
```

## 削除

```bash
aws cloudformation delete-stack --stack-name NetworkStack
```
