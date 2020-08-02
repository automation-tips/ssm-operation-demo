# ssm-operation-demo

SSMAutomation を使用してインスタンスの自動起動・停止を設定する CFn のテンプレート。

## パラメータ

| パラメータ名   | 型     | 設定例                                     | 詳細                                                                            |
| -------------- | ------ | ------------------------------------------ | ------------------------------------------------------------------------------- |
| Ec2InstanceIds | String | Ec2InstanceIds='"i-hogehoge","i-fugafuga"' | 自動起動・停止対象のインスタンス ID を`,`区切りで指定                           |
| CronStart      | String | CronStart="0 1 \* _ ? _"                   | インスタンスを起動する時間を指定<br />※ 日本の現地時間で指定する場合は + 9 時間 |
| CronStop       | String | CronStop="0 10 \* _ ? _"                   | インスタンスを停止する時間を指定<br />※ 日本の現地時間で指定する場合は + 9 時間 |

## 実行コマンド

```console
# CFnスタック作成
aws cloudformation deploy --template-file main.yml --stack-name ec2-ssm-stack --parameter-overrides Ec2InstanceIds='"i-hogehoge","i-fugafuga"' CronStart="0 1 * * ? *" CronStop="0 10 * * ? *" --capabilities CAPABILITY_NAMED_IAM

# CFn削除
aws cloudformation delete-stack --stack-name ec2-ssm-stack
```
