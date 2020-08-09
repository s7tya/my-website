---
toc: true
layout: post
description: fastpagesで簡単にブログを作る
categories: [tutorial]
comments : true
image : images/diagram.png
title: fastpagesを使って簡単にブログを作る
---






## fastpagesとは

[fast.ai](fast.ai) が開発したブログプラットフォーム(?)です。

大きな特徴として、 「Jupyter Notebookをそのまま記事にできる」ということが挙げられます。

(もちろんMarkdownも使えますし、なんと.docxファイル(要はword)も使えます。すごい。)

htmlやcssなどの知識を必要とせずに簡単に技術記事を書けるのはとても魅力的です。

もちろん　**_Web完全理解者_**　の方は、自分なりにカスタマイズもできます。

## 使ってみよう
早速使ってみます。

(作業時間は10分もあればお釣りがくるレベルです)

公式には、
[fastpagesのリポジトリ](https://github.com/fastai/fastpages)のREADME.mdのSetup Instructionsの項目を参照してください。

### レポジトリを作る。

まずは本体を置くGitHubでレポジトリを作ります。

[このリンク](https://github.com/fastai/fastpages/generate) から新しいレポジトリを作ります。

この時にレポジトリの名前を {githubのユーザー名}.github.ioにしないように注意してください。


すると、1分もしないうちに自動でセットアップの手順を記したPRがBotから飛んできます。次はこれに従って設定していきます。


### 秘密鍵と公開鍵を作る




#### 生成
まず、 https://8gwifi.org/sshfunctions.jsp に飛んで、秘密鍵と公開鍵を生成します。
(もちろん手元で生成してもいいですが、 PRにはこのサイトを使用するように言われます。)

SSH-Keygen Online Algorithm　はRSA, RSA Key Sizeは4096を選択します。

Passphraseは何も入力しなくて大丈夫です。

generate-SSH-Keysで、　秘密鍵(画面上)と、　公開鍵(画面下)が生成されます。


![]({{ site.baseurl }}/images/generate_ssh_key.png "生成画面")


#### 秘密鍵の設定

次に、レポジトリの、
Settings => Secretsから、秘密鍵を登録します。

右上の、```new secret```をクリックして、先ほどの先ほど生成した秘密鍵を入力していきます。


Nameには、```SSH_DEPLOY_KEY``` 、

そして、Valueに先ほど生成した秘密鍵(Private Key)をコピペします。

(最初と最後の

```-----BEGIN RSA PRIVATE KEY-----```
、

```-----END RSA PRIVATE KEY-----``` 
も忘れずにコピペしましょう。)


#### 公開鍵の設定


次に、レポジトリの、
Settings => Deploy keys から、公開鍵を登録します。

Add deploy key をクリックして、 生成した公開鍵(Public Key)をコピペします。

Titleは何を設定しても問題ないので、公序良俗に反さない名前をつけておきましょう。

最後に、 Allow write accessにチェックを入れて、 Add keyをクリックします。


ここまでやれば設定は完了です。

飛んできたPRをマージしてください。


## すごい


しばらく待つと、
https://{あなたのGitHubのユーザー名}.github.io/{作ったレポジトリの名前}

に、Webサイトが構築されます！

また、masterにpushするたびにサイトが自動で更新されます！

![]({{ site.baseurl }}/images/web_site_result.png "GitHubActionsすごい")









