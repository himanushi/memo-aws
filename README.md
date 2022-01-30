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
