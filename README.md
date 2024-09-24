# Cfn_networkstack_sample

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

## Output

| キー      | 説明                        | エクスポート名         |
| --------- | --------------------------- | ---------------------- |
| SubnetId1 | The ID of the first Subnet  | NetworkStack-SubnetId1 |
| SubnetId2 | The ID of the second Subnet | NetworkStack-SubnetId2 |
| SubnetId3 | The ID of the third Subnet  | NetworkStack-SubnetId3 |
| VpcId     | The ID of the VPC           | NetworkStack-VpcId     |
