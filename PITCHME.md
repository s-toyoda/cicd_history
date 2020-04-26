# 継続的インテグレーションってなに？

---

### 目次

- いわゆる開発の流れおさらい
- CI/CDとはなんぞや
- AWSではどんな感じか？

---

## いわゆる開発の流れおさらい

---

## 10年以上前のWEBサービス会社のサービスリリースを例に説明します

---

### 要件から設計書ができます

アーキテクトからコーダ向けの設計書が来ます。
※マーケティングなどが分析した市場動向から新機能の要件が降りて来るみたいな感じです
![設計書](https://1.bp.blogspot.com/-NThogaToW7c/Xbo7E1rzVJI/AAAAAAABVyY/XPEsejVWiQkyDDHCprIiZD4ZbD9bkwXrQCNcBGAsYHQ/s1600/document_sekkeisyo.png)

---

### 分担を決めます

![分担](https://2.bp.blogspot.com/-08jWQssqg_U/V5ND5RxqiuI/AAAAAAAA8fQ/aauvTJO2JYQoZrq-PEWkwimXA9gOHh2lgCLcB/s800/computer_hacker_white_syuudan.png)

---

### コーディングします

![コーディング](https://2.bp.blogspot.com/-WKhyux3zjI8/XASwaSwkEGI/AAAAAAABQZ4/5csR5XWpXNoxbA-cvkPm-SdeSeab1lkNACLcBGAs/s800/computer_programming_woman.png)

---

### レビューします

レビュー会議なるものを実施します ※しない開発組織もあります。
![レビュー](https://1.bp.blogspot.com/-tonUHy9fDEk/XnLn7EL4lvI/AAAAAAABX0k/HvgZidpGmQc7-Qe7LDsp00TfWltpuwkSwCNcBGAsYHQ/s1600/computer_mob_programming.png)

---

### できたコードをコード管理者に渡します

![渡す](https://1.bp.blogspot.com/-_kT-8xlbW08/V2vYKQv2_lI/AAAAAAAA78E/RBEwIoQAdKMXycaWL4HVb_Z1LFD7MSr5ACLcB/s800/kumiawase_business.png)

---

### コード管理者がうまいこと複数の成果物を統合します

※変更規模がでかいとかなり時間がかかります
![コーディング](https://2.bp.blogspot.com/-WKhyux3zjI8/XASwaSwkEGI/AAAAAAABQZ4/5csR5XWpXNoxbA-cvkPm-SdeSeab1lkNACLcBGAs/s800/computer_programming_woman.png)

---

### コード管理者からテスト部門へ引き渡されます

![渡す](https://1.bp.blogspot.com/-_kT-8xlbW08/V2vYKQv2_lI/AAAAAAAA78E/RBEwIoQAdKMXycaWL4HVb_Z1LFD7MSr5ACLcB/s800/kumiawase_business.png)

---

### 設計書からテスト設計書を作成します

![設計書](https://1.bp.blogspot.com/-NThogaToW7c/Xbo7E1rzVJI/AAAAAAABVyY/XPEsejVWiQkyDDHCprIiZD4ZbD9bkwXrQCNcBGAsYHQ/s1600/document_sekkeisyo.png)

---

### テストを実施します

![不合格](https://3.bp.blogspot.com/-7y-GhxFEFU4/W1a4nOtMdKI/AAAAAAABNgw/ae6kkUDrb6oxofm7A2EGg31ZmezQ6IjtACLcBGAs/s800/document_shinsa_fugoukaku.png)

---

### バグ発見結果が開発部門へ

![バグ](https://1.bp.blogspot.com/-PYOsJAMddQI/WdyDTQ-OjQI/AAAAAAABHbU/wg8mS8AFANYaZOKreTrdJhPPUochYCkDQCLcBGAs/s800/character_program_shutdown.png)

---

### バグを修正します

![頑張る](https://1.bp.blogspot.com/-opoSCyJN0pY/XBC4qhz_PzI/AAAAAAABQ1U/tnvdH2eK8cwbhchvgibqNd9O5j6eaAXFwCLcBGAs/s800/computer_kurayami_woman.png)

---

### できたコードをコード管理者に渡します

![渡す](https://1.bp.blogspot.com/-_kT-8xlbW08/V2vYKQv2_lI/AAAAAAAA78E/RBEwIoQAdKMXycaWL4HVb_Z1LFD7MSr5ACLcB/s800/kumiawase_business.png)

---

### コード管理者がまた成果物を統合します

![コーディング](https://2.bp.blogspot.com/-WKhyux3zjI8/XASwaSwkEGI/AAAAAAABQZ4/5csR5XWpXNoxbA-cvkPm-SdeSeab1lkNACLcBGAs/s800/computer_programming_woman.png)

---

### コード管理者からテスト部門へ引き渡されテストされます

![合格](https://1.bp.blogspot.com/-5HpqQ1WibQM/W1a4njkhUoI/AAAAAAABNg0/EeLVdx02NAQCaxN1rRO3_-tvZi8aiRHywCLcBGAs/s800/document_shinsa_goukaku.png)

---

### リリース版を作成します

![ゴールデンディスク](https://4.bp.blogspot.com/-47HPph-iWmc/VkxL08L88YI/AAAAAAAA0qk/JNzwMJo7cno/s800/music_gold_disc.png)

---

### リリース作業担当部門へ出荷します

※インフラ部門がリリースする場合もあれば運用部門がリリースする場合もあります
![渡す](https://1.bp.blogspot.com/-_kT-8xlbW08/V2vYKQv2_lI/AAAAAAAA78E/RBEwIoQAdKMXycaWL4HVb_Z1LFD7MSr5ACLcB/s800/kumiawase_business.png)

---

### リリースタイミングを見極めます

※サービス影響が少ない日を狙うとかやってましたね
![縄跳び](https://2.bp.blogspot.com/-ALq4kRUR9Pg/XNE_J6lEBxI/AAAAAAABSvE/FOcjozfVJZUFleF5x6XoQwi7rfNLDkbiACLcBGAs/s800/kids_oonawatobi_hairenai.png)

---

### 更新を実施します

※メンテナンスとしてサービス停止が発生します
![更新](https://2.bp.blogspot.com/--FiY869JmSg/Ul5qUphSecI/AAAAAAAAZDQ/Hs8WpL9y848/s800/pop_koushin.png)

---

### 更新後に問題が出てないか監視します

![監視](https://2.bp.blogspot.com/-TPA7euWs3Z4/V5NEZlqOGfI/AAAAAAAA8i4/RkrUOdTyU7ok1eHgfFTsjyrwKmxEykLmgCLcB/s800/pool_kanshiin.png)

---

### 問題が見つかりました

![溺れる](https://3.bp.blogspot.com/-frz3qhFLPfo/Wb8ge1cvrjI/AAAAAAABGx8/Xcs_udENP1cnS42aDff9UNhB5tACoDN0QCLcBGAs/s800/kyuujo_ukiwa_tasukeru.png)

---

### 更新前に戻します

※メンテナンスとしてサービス停止が発生します
![更新](https://2.bp.blogspot.com/--FiY869JmSg/Ul5qUphSecI/AAAAAAAAZDQ/Hs8WpL9y848/s800/pop_koushin.png)

---

### いろんな人がいろんなところに謝罪します

![ごめん](https://3.bp.blogspot.com/-vniEhW_MIto/Vf-ejdjvkiI/AAAAAAAAyQc/NRwtTv2bn4w/s800/syazai_kaiken.png)

---

## なんとも胃が痛くなる話ですね

---

### 問題点

- ソースコードの統合に時間がかかりすぎ
- そもそも変更点が大きすぎる
- バグの発見からの手戻りが大きい
- 製品はできてるのに実際にユーザに届くまでタイムラグがある
- などなど

---

## 少しずつ改善していきましょう

---

### 継続的インテグレーション(CI)の発生

**1991年**にIBMのラショナル（ソフトウェア統合開発環境）開発主席技術者だったブーチさんが提唱した**考え方**。

![ブーチさん](https://upload.wikimedia.org/wikipedia/commons/3/39/Grady_Booch%2C_CHM_2011_2_cropped.jpg)


---

### CIを簡単にいうと

**ひとつのソフトウェアを複数人で開発している場合はすべての開発者の作業コピーを定期的に統合（マージ）した方が良い**という考え方

---

### メリットは問題点の反転

- バグを早期に発見し修正を早く行える
- 他の開発者とのコミュニケーションコストが少なくなる
- 実装してみたがいまいちだった機能が早めに見つかる
- コードの複雑さを小さくすることができる

---

### CIの構成要素

1. コードと(単体)テストの同時作成：開発者が実施
1. ソースコードの管理：ツール
1. 自動ビルド：ツール
1. 自動テスト：ツール
1. 結果を開発者に通知：ツール

---

## この考え方はのちのエクストリームプログラミングという開発手法に取り込まれます

**extreme programming(XP)：1999年くらい**

XPの詳細は興味があれば各自で調べてください。ざっくりいうと、小さい開発を反復することで大きな成果につなげるという手法です。

---

## XPはアジャイル開発手法の中でも比較的人気な一手法となりました

アジャイル開発手法の詳細は興味があれば各自で調べてください。

---

**継続的インテグレーション(CI)はソフトウェア開発チームの改善です**

---


## 続いて

---

### CDの発生

これは特定のこれいう発生起源はないです。
継続的インテグレーション(CI)の派生形です。
CDは継続的デリバリー(CD)と継続的デプロイ(CD)の類似パタンがあります。

---

### 継続的デリバリー(CD)を簡単にいうと

CIではテスト自動化まででしたが、テストまで完了したソフトウェアをインフラに適用するというところまでを自動化するという考え方。

---

### 継続的デプロイ(CD)を簡単にいうと

継続的デリバリーからさらに本番環境の更新まで自動的に行うという考え方。

---

### CDの構成要素

1. ステージング環境へ自動デプロイ：ツール
1. リリース判定：開発者が実施※このフェーズがない場合も
1. 本番環境へ自動デプロイ：ツール

---

### 継続的デプロイが範囲を本番更新まで含めるようになったことで継続的デリバリーになり、影響範囲が様々な組織にでるためDevOps(2008年くらい)などのマーケティングメッセージを作ることで浸透していきました

![devops](https://upload.wikimedia.org/wikipedia/commons/0/05/Devops-toolchain.svg)

---

**継続的デプロイ(CD)は運用/インフラチームの改善です**

---

### こんな分け方

![CI/CD/CD](https://cloudbees.techmatrix.jp/wp-content/uploads/2018/03/cd_2.png)


---

## CI/CDについて

---

### ソフトウエアの開発パイプラインとデプロイ作業パイプラインを一つすることでCI/CDパイプラインが出来上がります

---

## CI/CDパイプラインができる前と変わった点

- ソースコードのマージ作業者がいなくなった（ツールに置き換わった）
- テスターがいなくなった(開発チームのテスト作成支援部分に統合された)
- デプロイ作業者がいなくなった（ツールに置き換わった）
- 更新の粒度が小さくなった（ユーザが変わったことに気が付かないレベルで）
- などなど

---

## ツール：ソースコード管理ソフトウェア

（10年前に使われてなかったわけではないが）
ほとんどのソフトが淘汰されてGitを使ったソフト、サービスに置き換わった。

- GitHub(サービス、オンプレ))
- GitLab(オンプレ)
- Bitbucket(サービス)

---

## ツール：自動テスト

無数の自動テストツール、フレームワークを利用。

- 静的解析ツール：infer(C言語系), RoboCop(Ruby系)...
- 単体テストツール：Junit(Java), RSpec(Ruby系)...
- 結合テストツール：Selenium, Turnip...
書ききれないほど膨大

---

## ツール：CIツール

各社それぞれ自作で作っていた更新バッチがツールに移行した。

- Jenkins(オンプレ)
- GitLab(オンプレ)
- CircleCI(サービス)
- TravisCI(サービス)
- Github Action(サービス)
- 各種パブリッククラウドが用意するツール

---

## ツール：インフラ構築ツール

環境構築などのインフラ環境も仮想化、コンテナ化が進んだ。

- ハイパーバイザ型：vmware各製品, kvm, Hyper-V, VirtualBox...
- コンテナ型：Docker, Kubernetes...
- クラウドサービス構築：Pulumi, Telaform

---

## ツール：サーバ設定ツール

サーバ構築時のアプリケーションインストールや設定などの自動化ツールも百花繚乱。

- Chef(ツール)
- Ansible(ツール)
- Fabric(ツール)
- Puppet(ツール)

---

## 話が終わらないのでこの辺で

---

## 何が言いたいかというとこの10年くらいですごい変わりました

---

# デモンストレーション

---

## AWSではどんな感じか？

---

![AWS](http://www.keencomputer.com/media/k2/items/cache/5b62d01506bd8a53b6c4928e25fa9b8a_XL.jpg)

---

## デモ

---

# おしまい

---

# このドキュメント

- ![プレゼン形式](https://gitpitch.com/s-toyoda/cicd_history)
- ![ドキュメント形式](https://github.com/s-toyoda/cicd_history/blob/master/PITCHME.md)

# 参考資料

## 継続的インテグレーションの説明でいい感じの物

- ![さくらのナレッジ：継続的インテグレーション・継続的デリバリー – 「若手エンジニアのためのDevOps入門」(4)](https://knowledge.sakura.ad.jp/13251/)
- ![aws:継続的インテグレーションとは?](https://aws.amazon.com/jp/devops/continuous-integration/)
- ![wikipedia](https://ja.wikipedia.org/wiki/%E7%B6%99%E7%B6%9A%E7%9A%84%E3%82%A4%E3%83%B3%E3%83%86%E3%82%B0%E3%83%AC%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3)
