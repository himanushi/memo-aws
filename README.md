# memo-aws

## 初期にやった方がいいこと
* 請求アラートの設定
  * https://www.udemy.com/course/aws-and-infra/learn/lecture/14874400
* IAM で作業用ユーザーを作成
  * root ユーザーだとなんでもできてしまうのでやめとく
  * https://www.udemy.com/course/aws-and-infra/learn/lecture/14874402
* CloudTrail で操作ログを取る
  * S3 にログを取る。CloudTrail自体の料金は無料。
  * https://www.udemy.com/course/aws-and-infra/learn/lecture/14874404

## 手順
* VPC、サブネットを作成する
* インターネットゲートウェイを作成、VPCをアタッチする
* ルートテーブルを VPC を紐づけて作成する
* ルートテーブルのサブネットの関連付けタブでパブリックサブネットを関連付ける
* ルートテーブルのルートタブでインターネットゲートウェイを関連付ける
* EC2インスタンスを VPC と紐づけて作成する
* EC2インスタンスを作成するとき pem ファイルも作成する
* pem ファイルの権限変更
  * `chmod 600 aws-ssh.pem`
* ssh で EC2 インスタンスに入る
  * `ssh -i aws-ssh.pem ec2-user@<EC2 のプライベート IPv4 アドレス>`

## サービス
* VPC
  * 仮想ネットワーク構築
* サブネット
  * VPCを細かく区切ったネットワーク

## 用語
* リージョン
  * AWS提供地域のこと
* アベイラビリティゾーン
  * リージョンに複数存在する物理的に離れているデータセンター。災害などに対応するためのもの。
