# memo-aws

# アーキテクチャ図
<img width="742" alt="スクリーンショット 2022-02-16 23 25 28" src="https://user-images.githubusercontent.com/27812830/154284766-fe81abd7-3d2d-471a-b582-7ffab87cce59.png">

## 初期にやった方がいいこと
* 請求アラートの設定
  * https://www.udemy.com/course/aws-and-infra/learn/lecture/14874400
* IAM で作業用ユーザーを作成
  * root ユーザーだとなんでもできてしまうのでやめとく
  * https://www.udemy.com/course/aws-and-infra/learn/lecture/14874402
* CloudTrail で操作ログを取る
  * S3 にログを取る。CloudTrail自体の料金は無料。
  * https://www.udemy.com/course/aws-and-infra/learn/lecture/14874404
  * 注意: CloudTrail で S3 を使用すると即無料枠がなくなるほどAPIを実行する 
    * 参考: [AWSを使い始めて2日目に無料枠限度アラームがきた話](https://qiita.com/Ki2neudon/items/aefaa9edb435b4945c3a)

## 手順
* VPCを作成
  * https://www.udemy.com/course/aws-and-infra/learn/lecture/15046674#notes
* サブネットを作成する
  * https://www.udemy.com/course/aws-and-infra/learn/lecture/15046678#notes
* インターネットゲートウェイを作成、VPCをアタッチする
  * https://www.udemy.com/course/aws-and-infra/learn/lecture/15046680#notes
* ルートテーブルを VPC を紐づけて作成する
  * https://www.udemy.com/course/aws-and-infra/learn/lecture/15046680#notes
* ルートテーブルのサブネットの関連付けタブでパブリックサブネットを関連付ける
* ルートテーブルのルートタブでインターネットゲートウェイを関連付ける
* EC2インスタンスを VPC と紐づけて作成する
* EC2インスタンスを作成するとき pem ファイルも作成する
* pem ファイルの権限変更
  * `chmod 600 aws-ssh.pem`
* ssh で EC2 インスタンスにログイン
  * `ssh -i aws-ssh.pem ec2-user@<EC2 のパブリック IPv4 アドレス>`
* インバウンドルールで HTTPS を追加
* この時点でパブリックIPで web 表示してみる。表示できない場合は上記のいずれかが間違っている。
* Elastic IP で IP 固定
* Route 53 でドメイン設定

### RDS
* サブネットを作成
* セキュリティグループを作成
  * インバウンドルールに MYSQL/Aurora を設定して、ソースに app のセキュリティグループを設定
* RDS サブネットグループ作成
* パラメータグループを作成
* オプショングループ作成

## EC2環境構築
* `sudo yum update -y`
* 

## サービス
* VPC
  * 仮想ネットワーク構築
* サブネット
  * VPCを細かく区切ったネットワーク
* 

## 用語
* リージョン
  * AWS提供地域のこと
* アベイラビリティゾーン
  * リージョンに複数存在する物理的に離れているデータセンター。災害などに対応するためのもの。
