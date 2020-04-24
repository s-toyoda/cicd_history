# 継続的インテグレーションってなに？

---

# 結論を先に

---

継続的インテグレーション(CI)及び継続的デプロイ(CD)は、"いかに開発に掛かったコストを早く回収するか"と"いかにユーザから受けたフィードバックを製品に反映するか"という **ビジネスサイド** からの要求に対して **開発サイド** が出した改善案です。

---

様々なツールの出現やDevOpsというのマーケティングのためのバズワードが出てきたためわかりにくくなっていますが

---

いかに早くリリースするか

---

その一点に向けた改善策が継続的インテグレーション及び継続的デプロイです

---

これを頭の隅においていただいて引き続きお聞きいただければ幸いです

---


### 目次

- CI/CDの発生
- 何故CI/CDは開発者に受け入れられたのか
- DevOpsというバズワードの発生
- DevOpsはなぜ開発者に受け入れられたのか
- CI/CDを取り入れた開発フロー
- AWSではどんな感じか？
- 実際使われてるの？
- 体験方法の紹介

---

### 継続的インテグレーション(CI)の発生

IBMのラショナル（ソフトウェア統合開発環境）開発主席技術者だったブーチさんが提唱した**考え方**。

![ブーチさん](https://upload.wikimedia.org/wikipedia/commons/3/39/Grady_Booch%2C_CHM_2011_2_cropped.jpg)


---

### CIを簡単にいうと

**ひとつのソフトウェアを複数人で開発している場合はすべての開発者の作業コピーを定期的に統合（マージ）した方が良い**という考え方

---

### この考えが定着する前の問題点

- バグの発見が遅れる(開発者の手元にずっとバグがいる)
- 他の開発者との実装衝突の発見が遅れる
- フィードバックが遅れる(作ってる実装を他人が見るタイミングが遅い)
- 開発者が複雑なコードを作ってしまう(手元にあるので作りこんでしまう)

**どれも開発の期間を長くしてしまうリスク**

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

**継続的インテグレーション(CI)は運用/インフラチームの改善です**

---

### こんな分け方

![CI/CD/CD](https://cloudbees.techmatrix.jp/wp-content/uploads/2018/03/cd_2.png)

---

## 何故CI/CDは開発者に受け入れられたのか

---

### 実際しんどかったのです

---

### 要件から設計書ができます

アーキテクトからコーダ向けの設計書が来ます。
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

## CI/CDを取り入れた開発フロー

---

## AWSではどんな感じか？


---

## 実際使われてるの？


---

## 体験方法の紹介


---

# おしまい


---

# Ref

- [wiki : 継続的インテグレーション](https://ja.wikipedia.org/wiki/%E7%B6%99%E7%B6%9A%E7%9A%84%E3%82%A4%E3%83%B3%E3%83%86%E3%82%B0%E3%83%AC%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3)
- []()